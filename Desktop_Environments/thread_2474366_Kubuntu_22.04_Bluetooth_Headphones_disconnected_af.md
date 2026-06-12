---
title: "Kubuntu 22.04 Bluetooth Headphones disconnected after automatic re-connect"
date: 2022-04-27
forum: Desktop Environments
---

### Post by MikeBraxner on 2022-04-27
Hi again.

Used to be (on, say, Kubuntu 21.10) that if I turned the headphones on, they would automatically re-connect to the laptop. 

On a clean install of Kubuntu 22.04 on a Dell XPS 9500, after properly pairing them, the headphones *initially* re-connect upon being turned on, but are then *immediately* disconnected, i.e. in less then a couple of seconds. Manually selecting them from the bluetooth widget to connect works as expected.

Any idea how to fix this?

---

### Post by MikeBraxner on 2022-05-05
Turns out this is a bug in pulseaudio.

[Igor Kovalenko was able to identify and fix it]("https://gitlab.freedesktop.org/pulseaudio/pulseaudio/-/issues/1354"). Said fix should be forthcoming in the usual update cycle.

---

### Post by peterburten on 2022-05-16
Check of your headphones have any RESET button? if yes, then press it for 5-7 seconds until you hear a beep. I have similar bluetooth headset and had the same issue as you mentioned. I found this solution in the user manual.

---

