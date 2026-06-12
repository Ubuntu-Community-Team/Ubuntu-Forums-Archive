---
title: "My Kubuntu is acting weird"
date: 2006-01-03
forum: General Help
---

### Post by Kræn Knude on 2006-01-03
I have struggled a lot with sound in kubuntu, and I think most it is working now, BUT:

When ever i reboot, my sound is turned down. Everytime i start the computer, i have to open alsamixer and turn the volume up for "front speaker"...

How can i change this annoying habit?

I hope somebody out there has a good answer :)

---

### Post by Lord Illidan on 2006-01-03
Type ```
sudo alsactl store
``` after modifying the volume.

---

### Post by Kræn Knude on 2006-01-03
Thanks for the quick answer. 

When i write "sudo alsact1 store"

it comes out with the error:

sudo: alsact1: command not found

Is there something i need to install?

EDIT: Nevermind me, i found out i had to write alsactl (with an l instead of a 1), thanks! :)

---

### Post by tikal26 on 2006-01-03
i think you tped and 1 instead of an l

---

### Post by GeneralZod on 2006-01-03
Do you have kmix running in the system tray?

[img]http://etotheipiplusone.com/kmix-systray.png[/img]

That should handle everything transparently.

---

### Post by Kræn Knude on 2006-01-03
The other solution didn't work :(

No I don't have Kmix running. I closed it and couldn't find it again... I need to look into how i make a "standart-desktop" with the programs I want to start up when i open the computer... right now kubuntu just starts with whatever i left open when i closed it down...

But to summerize, i still have the problem with sound getting muted every time i reboot :/ I'll try and see if kmix can do anything about it.

EDIT: It seems the problem is solved now. In kmix configuration theres a checkbox called "restore volumes on login", now whether this solved the problem, or just kmix starting up, I don't know. But i think so...

---

