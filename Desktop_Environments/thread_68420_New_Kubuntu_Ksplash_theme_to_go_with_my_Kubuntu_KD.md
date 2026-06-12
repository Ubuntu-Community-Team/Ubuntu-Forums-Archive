---
title: "New Kubuntu Ksplash theme to go with my Kubuntu KDM theme"
date: 2005-09-23
forum: Desktop Environments
---

### Post by jbus on 2005-09-23
I just released a sleek and sexy new Ksplash them to go with my Kubuntu KDM theme. It uses the very cool Moodin engine and is a bit different than the usual splashes. I made it exclusively for Kubuntu users.

It is fore 1024x768 res only for right now, but I will update with higher res versions in the next couple of days. My laptop doesn't handle these higher resolutions and I can't test it, so please don't hold that against me :(  Or if you don't mind hacking the RC file a bit, I'm sure you can make it work now with higher res now.

Be sure to compile the latest Moodin before trying to use this. More info about that on KDE- look.

You can grab it at KDE-Look [http://www.kde-look.org/content/show.php?content=29426](http://www.kde-look.org/content/show.php?content=29426)

Please let me know what you think.

---

### Post by drizek on 2005-09-23
i think someone needs to package moodin...

---

### Post by f1dave on 2005-09-23
I like this theme a lot... now if I could only decide between it and the breezy-style splash recently added to kde-look!

---

### Post by getaceres on 2005-09-23
I want to delete this.

---

### Post by stanz on 2006-04-05
This theme requires Moodwrod's Moodin Engine.
The moodin engine is/will be included in Dapper [U]and is also available for Breezy in backports.

[/U]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

### Post by Lukekelsall on 2006-05-10
hmm i'm getting a number of dependancy issues with this package, firstly whats the package name i should use for moodin (apt-get install ?) second are the two sources in the last post the only sources i will need? i assume apt-get update and apt-get dist-upgrade should do the trick?

i'm running KDE installed on ubuntu -breezy not kubuntu dont know if that is relevent. any help would be great.

---

### Post by Lukekelsall on 2006-05-10
Is o.k sorted it ksplash-engine-moodin did the trick dist-upgrade & -f install fixed the dependancy issues.

---

### Post by Omnios on 2006-05-10
Very clean very nioce, when I get my laptop ill probably use it on it.

---

### Post by stanz on 2006-05-10
[quote=Lukekelsall]whats the package name i should use for moodin (apt-get install ?) are the two sources in the last post the only sources i will need?[/quote] I'm using 'synaptic'.
I've now found the moodin package having these regular repo's checked.
[B]"Officially supported= Community maintained[&Universe]= Non-free Multi="
[/B]Searching "ksplash" brought it up... **(***or use-->***  apt-get install kslpash)**
Searching "kslpash-moodin-engine",  didn't !?

It's version 0.4.2-0ubuntu1~breezy1
=D>

---

