---
title: "Google Earth after installation"
date: 2009-06-06
forum: General Help
---

### Post by spector70 on 2009-06-06
I installed Google Earth via Synaptic.  Afterwards I could not locate it anywhere on my gnome desktop.  Does anyone know where to find it after installation?  I have installed other programs and easily found them even though I am clearly a noob.

---

### Post by solidsnake204 on 2009-06-06
Looked in the Applications menu?
I would guess it would come under 'Internet' or 'Accessories'

---

### Post by spector70 on 2009-06-06
Yeah, I looked all over for it and used file search and file browser, too.  No where to be found.  I have enough pc experience to use ubuntu somewhat effectively, but there are some things that I am quite new to.

---

### Post by bluelamp999 on 2009-06-06
What I did was set up a launcher with the command "gksudo googleearth" (without the quotes), you can also set the icon which for me was here - "/opt/google-earth/googleearth-icon.png".

I then added this to my panel...

Good luck!

---

### Post by markharding557 on 2009-06-06
type google earth in a console

---

### Post by cmost on 2009-06-06
You guys are missing the boat.  The Google-package in Ubuntu's repository only installs a script to fetch and install GoogleEarth.  The package itself does not launch GoogleEarth.  If you want the easiest way to get GoogleEarth via Synaptic, then add the following repository to /etc/apt/sources.list

## Mediabuntu
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

Type apt-get update; open synaptic and search for GoogleEarth.  Install and enjoy!

---

### Post by spector70 on 2009-06-07
I ended up installing it from medibuntu   It now works well.

---

