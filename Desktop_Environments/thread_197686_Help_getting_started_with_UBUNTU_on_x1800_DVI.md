---
title: "Help getting started with UBUNTU on x1800 DVI"
date: 2006-06-16
forum: Desktop Environments
---

### Post by Rechinica on 2006-06-16
Hi,
I have a x1800 video card, a Hyundai L90D+ monitor on DVI connection.
I've installed the amd64 version of the UBUNTU 6.06.

After restart my monitor shuts off .. but i can hear a sound, i think the startup sound.

Restarted in recovery mode.

Installed fglrxdriver:

"sudo apt-get update"
"sudo apt-get install xorg-driver-fglrx"
"sudo aticonfig --initial"
"sudo aticonfig --ovt=Xv"

After restart ... the monitor shuts down and powers back 2-3 times and then remains on, but on a black screen. I don't hear the startup sound anymore.

What can i do next ? ... do i have to install somehow different drivers for amd64 ? ... and how can i take advantage of a dual core CPU in UBUNTU ?

---

