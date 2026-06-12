---
title: "Firefox icon missing after upgrade to Ubunty 11.10"
date: 2011-11-07
forum: Desktop Environments
---

### Post by PhilipGanchev on 2011-11-07
After I upgraded from Ubuntu 10.10 to 11.10, the Firefox icon is now missing. Firefox windows and the dock launcher have the generic app icon. With this release, the only desktop is unity (and unity-2d), there is no Gnome2. How can I configure the icon?

---

### Post by BillyBoa on 2011-11-07
Did you try opening Firefox and press "keep in launcher"?

---

### Post by PhilipGanchev on 2011-11-07
Yes, of course. That does not help. 

Is there someone who has upgraded? Do you have the same problem or is it just me? Where are the app icon associations described?

---

### Post by subehsharma on 2011-11-07
for gnome, install gnome-shell. this is how you'll get gnome 3. And about ur problem, are you seeing it only in 2d unity or also in unity 3d?

---

### Post by PhilipGanchev on 2011-11-08
I don't have 3D because I'm missing a video driver with hardware acceleration which is needed for Compiz. I can install the propriatory one from Nvidia but I don't want to, as a matter of principle.

Installing Gnome3 would not help.

I fixed the problem. The cause was that my user setting in file 

.local/share/applications/firefox.desktop

was pointing to a Firefox version that is no longer installed:

Icon[en_US]=/usr/lib/firefox-3.6.17/chrome/icons/default/default32.png

I don't know how that happened. I fixed the problem by editing the line in the configuration file to point to the correct image file:

Icon[en_US]=/usr/share/pixmaps/firefox.png

---

### Post by tom-ubuntu on 2011-11-26
Many thanks, PhilipGanchev, that fixed the problem.

my ~/.local/share/applications/firefox.desktop was showin these entries:

Icon=firefox-3.0
Icon[en_US]=firefox-3.5

which I replaced with

Icon=/usr/share/pixmaps/firefox.png

and Firefox finally shows its icon again.

Thanks again.

Tom

---

### Post by Jukka-Pekka on 2012-02-13
Strange, but in Unity I have no icon-entry in that file whatsoever? I have the same "missing icon"-problem.

---

