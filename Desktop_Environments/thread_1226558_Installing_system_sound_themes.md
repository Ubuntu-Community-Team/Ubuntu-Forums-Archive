---
title: "Installing system sound themes"
date: 2009-07-29
forum: Desktop Environments
---

### Post by justin315 on 2009-07-29
I currently have ubuntu 9.04 but i like the mac sounds.  i downloaded a system sound theme called macossounds.zip from gnome-look.org and am having problems installing it.  any help?

---

### Post by frosty007 on 2009-11-28
**Please make sure you put the correct files, and i have copied and pasted this information from this website > [http://www.ubuntu-art.org/content/show.php/%22Borealis%22+sound+theme?content=12584]("http://www.ubuntu-art.org/content/show.php/%22Borealis%22+sound+theme?content=12584")** so yea not much credit to me :P

[B]You asked for 'the gnome way'.

For Gnome Sound Themes please use the folders:
/usr/share/sounds/Borealis
/usr/share/sounds/Borealis/stereo

and the file
/usr/share/sounds/Borealis/index.theme

Index.theme should contain:
----
[Sound Theme]
Name=Borealis
Directories=stereo

[stereo]
OutputProfile=stereo
----
In 'stereo' the audio-files must read:

audio-channel-front-center.ogg
audio-channel-front-left.ogg
audio-channel-front-right.ogg
audio-channel-rear-center.ogg
audio-channel-rear-left.ogg
audio-channel-rear-right.ogg
audio-channel-side-left.ogg
audio-channel-side-right.ogg
audio-test-signal.ogg
battery-low.ogg
bell.ogg
button-pressed.ogg
button-toggle-off.ogg
button-toggle-on.ogg
camera-shutter.ogg
complete-media-burn.ogg
desktop-login.ogg
desktop-logout.ogg
dialog-cancel.ogg
dialog-error.ogg
dialog-information.ogg
dialog-ok.ogg
dialog-question.ogg
dialog-warning.ogg
link-pressed.ogg
menu-click.ogg
message-new-email.ogg
message-new-instant.ogg
phone-incoming-call.ogg
phone-outgoing-busy.ogg
power-unplug.ogg
service-login.ogg
service-logout.ogg
suspend-error.ogg
trash-empty.ogg
window-close.ogg
window-maximized.ogg
window-minimized.ogg
window-move-start.ogg
window-move-stop.ogg
window-slide.ogg[/B]

---

