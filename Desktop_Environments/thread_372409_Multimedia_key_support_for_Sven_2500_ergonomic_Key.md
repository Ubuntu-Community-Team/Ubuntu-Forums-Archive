---
title: "Multimedia key support for Sven 2500 ergonomic Keyboard"
date: 2007-02-28
forum: Desktop Environments
---

### Post by kayosiii on 2007-02-28
You will need to create or replace these two files to get this working on Edgy Eft....

The first is hotkey-setup in /etc/init.d

it should read

> 
!/bin/sh
setkeycodes \
e068 158 e012 159 e023 128 e029 173 e02e 217 e030 156 e01e 150 e019 165 e01a 166 \
e010 164 e062 163 e026 113 e025 114 e017 115 e018 238 e021 239 e032 178 e031 177 \
e020 155 e022 157 e028 140 e024 237
# e068 158 \ # Back
# e012 159 \ # Forward
# e023 128 \ # Stop
# e029 173 \ # Refresh
# e02e 217 \ # Search
# e030 156 \ # Bookmarks/ Favourites
# e01e 150 \ # Home WWW
# e019 165 \ # Audio Previous Song
# e01a 166 \ # Stop CD
# e010 164 \ # play/pause
# e062 163 \ #Audio next song
# e026 113 \ # Mute
# e025 114 \ # Volume Down
# e017 115 \ # Volume Up
# e018 238 \ # Zoom out #######
# e021 239 \ # Zoom In ######
# e032 178 \ # Scroll Down
# e031 177 \ # Scroll Up
# e020 155 \ # email
# e022 157 \ # Computer
# e028 140 \ # Calculator
# e024 237  #Screensaver ####


and the other file is /usr/share/apps/kxkb/ubuntu.xmodmap it should read
> 
keycode 234 = XF86Back
keycode 233 = XF86Forward
keycode 146 =
keycode 232 = XF86Stop
keycode 163 =
keycode 231 = XF86Refresh
keycode 229 = XF86Search
keycode 230 = XF86Favorites
keycode 178 = XF86WWW

keycode 162 = XF86AudioPause
keycode 164 = XF86AudioStop
keycode 154 =
keycode 144 = XF86AudioPrev
keycode 153 = XF86AudioNext

keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 151 =

keycode 243 = XF86ZoomOut
keycode 152 =
keycode 244 = XF86ZoomIn
keycode 143 = XF86ScrollUp
keycode 220 = XF86ScrollDown
keycode 236 = XF86Mail

keycode 235 = XF86MyComputer
keycode 161 = XF86Calculator
keycode 242 = XF86ScreenSaver

keycode 223 = XF86Standby
keycode 165 = XF86Sleep




How do I go about getting support for this keyboard into the next (K)ubuntu release????

---

