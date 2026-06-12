---
title: "Just can't seem to get the resulotion right"
date: 2009-05-09
forum: Desktop Environments
---

### Post by Drokles on 2009-05-09
Hello there.
Other than reading a few guides here and there and playing around with some applications today I'm absolutely new to Ubuntu. I started running Jaunty today, and everything works just fine; it's honestly a pleasure to work with this OS.

When I got to installing a graphics card driver however I couldn't seem to get it right. My card (nvidia 7900 GT) was compatible with 3 different drivers. One of them was recommended and I chose it but the resolution of the screen didn't go up to 1280x1024 which is the resolution my screen uses. I tried using EnvyNG but that just suggested the same 3 drivers.

I'm not entirely sure what to do about it. Is this something that can be fixed?

~ Drokles

---

### Post by KhurramM on 2009-05-09
I hope u can cli.

For resolution try:

xrandr -q

It will give u the possible resolutions u can have with your present configurations.

try:

xrandr -s 1280x1024

only if it is suppoted.

Do read:

man xrandr

on cli.

Hope I make myself clear.

---

### Post by Zimmer on 2009-05-09
Check the xorg.log as to what is happening at boot.
If you are loading your preferred driver correctly and your display is being correctly identified then try installing

nvidia-settings (via Synaptic) and setting your resolution from there.

---

### Post by Drokles on 2009-05-09
Nope, I don't know how to cli, but thanks anyway ^_^.
Oh, I should've probably mentioned, the nvidia settings initializes fine, but it doesn't let me chose the right resolution.

---

### Post by Zimmer on 2009-05-10
Did you actually complete an installation of the 173 driver using Envyng?

Have you looked at the xorg.log?

---

