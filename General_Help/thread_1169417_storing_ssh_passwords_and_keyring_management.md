---
title: "storing ssh passwords and keyring management"
date: 2009-05-25
forum: General Help
---

### Post by jaybee99 on 2009-05-25
I am using jaunty and want to store my ssh passwords for all time, even though I know this is a bit dodgy...I have used the keyring manager to set this up when I log in to gnome: I am not prompted for a password and I can ssh into my remote server locations no trouble. My normal wm is xmonad though, so I need to recreate this for a login that uses .xinitrc:

```

#!/usr/bin/env bash
CABAL_BIN=/home/jim/.cabal/bin
$CABAL_BIN/xmobar &
eval `gnome-keyring-daemon --start` 
gnome-settings-daemon &
/usr/lib/gnome-session/helpers/gnome-settings-daemon-helper &
nm-applet --sm-disable &
seahorse-daemon &
eval `keychain --eval id_dsa`

$CABAL_BIN/xmonad 

```

I copied what seemed to be the relevant daemons etc from the "Startup applications" panel in gnome, as everything works there, but that left me needing to enter the passphrase each time I use ssh. I added the line `eval keychain --eval id_dsa` (which isn't a gnome startup app) which means I get a dialog box immediately after logging in, unlike in gnome, but which means I can then login without supplying a passphrase. How do I set it up so that there is no dialog, no passphrase required? (I could just about live with entering the passphrase once on logging in if it weren't for the fact that the dialog comes with a sound that I can't disable. I always disable these sound effects but this seems not to be governed by the preferences.)

TIA

---

