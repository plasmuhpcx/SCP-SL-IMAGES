# SCP:SL radar UI references

`game_ui/` contains a focused local export of map-related sprites from the
installed SCP: Secret Laboratory Unity assets. Regenerate them with:

```powershell
python tools\extract-map-ui.py
```

The game's 079 facility map is not a single background image. It is generated
at runtime by `PlayerRoles.PlayableScps.Scp079.Map.ProceduralZoneMap` from room
nodes, transforms, labels, and a small set of special-room sprites. Our radar's
existing live room graph is therefore the correct basis for recreating it.

The extractor currently exports 78 map-facing sprites, including the complete
46-sprite room silhouette set:

- Every `EZ_*`, `HCZ_*`, and `LCZ_*` room tile exposed as a Unity sprite.
- Special rooms including gates, checkpoints, armories, SCP chambers, Tesla,
  server room, elevators, toilets, intercom, airlock, and nuke.
- All `Ping *` sprites plus camera-zone, door, elevator, and directional icons.

Other useful radar pieces:

- `106Radar.png`: circular range/radar mask.
- `elevatorUp.png`, `elevatorDown.png`, `elevator-move.png`: elevator markers.
- `Ping_Floor.png`, `Ping_Elevator.png`: 079 ping markers.
- `HCZ_Elevators.png`, `HCZ_ServerRoom.png`, `HCZ_Testroom.png`:
  special-room silhouettes.
- `LCZ_Checkpoint.png`, `EZ_Checkpoint.png`: checkpoint silhouettes.
- `Surface_Zone.png`: surface layout silhouette.

`game_ui/_room_tiles_preview.jpg` is a contact sheet for quickly reviewing the
room silhouettes.

The OPG and `facility*.png` files are camera-feed/interface references rather
than floor-plan tiles. Keep these assets local; they originate from the user's
installed copy of the game and should not be redistributed with a public build.
