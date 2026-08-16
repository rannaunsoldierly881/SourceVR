# SourceVR

Native VR ports of Half-Life 2, Episode One, and Episode Two for standalone Meta Quest headsets. Builds are published on the [Releases](../../releases) page.

No game content is included. Each APK requires your own retail copy of the game.

## Requirements

- A Meta Quest headset with Developer Mode enabled (developed and tested on Quest 3).
- A Steam installation of Half-Life 2, on the **`steam_legacy`** branch (PatchVersion `8491853`). Other builds are refused. In Steam: *Half-Life 2 → Properties → Betas → `steam_legacy`*, then let it update.
- Episode One / Episode Two, copied from that same `steam_legacy` installation, if you want to play them.
- Free space on the headset:

  | Game | APK + install | Game content |
  |---|---|---|
  | Half-Life 2 | ~1.2 GB | ~3.8 GB |
  | Episode One | ~1.2 GB | ~1.6 GB (plus Half-Life 2's content) |
  | Episode Two | ~1.2 GB | ~2.3 GB (plus Episode One's and Half-Life 2's content) |

## 1. Install the APK

Download from Releases and sideload with SideQuest or adb:

```sh
adb install SourceVRPort-hl2-<version>.apk
```

Each game is a separate, independent APK — install only the ones you want:

| Game | Package |
|---|---|
| Half-Life 2 | `com.sourcevrport.hl2vr` |
| Episode One | `com.sourcevrport.ep1vr` |
| Episode Two | `com.sourcevrport.ep2vr` |

Launch it from **Library → Unknown Sources** in the headset.

## 2. Grant storage access

On first launch the app asks for **Allow access to manage all files**. Grant it. The games share your retail content from one location, and Source needs to open those files by path.

## 3. Import your game content

The retail folders live at `/sdcard/SourceVRPort/common/` on the headset:

| Folder | Needed by |
|---|---|
| `hl2` | all games |
| `platform` | all games |
| `episodic` | Episode One and Episode Two |
| `ep2` | Episode Two |

Copy them from your Steam install:

- Windows: `C:\Program Files (x86)\Steam\steamapps\common\Half-Life 2\`
- macOS: `~/Library/Application Support/Steam/steamapps/common/Half-Life 2/`

Two ways to get them across:

**From the headset.** Use ADB, sidequest, or some other method to transfer them to the headset,  then press **Import from folder…** and select a listed folder, or a parentfolder containing  several of them. Android asks for one folder at a time, so repeat until every required folder is installed.

**From a computer.** Plug the headset in and copy the folders over MTP or adb straight into `/sdcard/SourceVRPort/common/`, then press **Re-check**. The `bin/` and `save/` subfolders are not used — skip them.

Files are verified before anything is activated, and your saves and settings are kept private to each game.

## 4. Play

Once the content check reports ready, press **Play**. Future launches go straight into the game.