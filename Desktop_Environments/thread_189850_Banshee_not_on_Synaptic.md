---
title: "Banshee not on Synaptic"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Trelo on 2006-06-05
Hello everyone :)

I just switched from windows yesterday and is the first time I try linux.  I have a lot of questions but one at a time. :)

I want to install Banshee but I can't seem to find it on Synaptic.  If I understood how this works, I can either try it on Synaptic or on the console, command sudo apt-get install banshee.  None of the two systems can find Banshee.

What am I doing wrong?

Thanks! :)

---

### Post by johnc4510 on 2006-06-05
You need to enable universe and multiverse repostories to have access to many of the extra packages available, including banshee.
In synaptic:
Click on settings
Click on repositories
Put a check mark in all empty boxes and close that window
Click on Reload
Click on Mark all Upgrades
Click on Apply
Now you should be able to find banshee in synaptic

---

### Post by Nonno Bassotto on 2006-06-05
You need to enable extra repositories where to search software. Have a look here.

[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29)

---

### Post by Trelo on 2006-06-05
Thanks a bunch guys for the quick and precise answer, that worked for me!.  Now... where did it go? :P  Yes I'm a total newbie.  How can I put it on the Applications/Multimedia menu?

---

### Post by johnc4510 on 2006-06-05
Open your menu editor, should be here:
Applications>Accessories

---

### Post by Trelo on 2006-06-05
Thanks John found it :)

---

### Post by Trelo on 2006-06-05
One more thing... Banshee doesnt seem to read mp3, how do I add support for it?

---

### Post by titus1950 on 2006-06-05
[QUOTE=Trelo]One more thing... Banshee doesnt seem to read mp3, how do I add support for it?[/QUOTE]



Read this ,could be helpfull

[https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

---

### Post by Trelo on 2006-06-05
I can actually listen to mp3 on other applications.  And gstreamer0.10-plugins-ugly is installed according to Synaptic.  Still Banshee doesnt let me open .mp3 

Any solution?  Thanks in advance.:)

---

### Post by titus1950 on 2006-06-05
[QUOTE=Trelo]I can actually listen to mp3 on other applications.  And gstreamer0.10-plugins-ugly is installed according to Synaptic.  Still Banshee doesnt let me open .mp3 

Any solution?  Thanks in advance.:)[/QUOTE]


May be here?

[http://banshee-project.org/Ubuntu](http://banshee-project.org/Ubuntu)

---

### Post by codypumper on 2006-06-05
Install audio codecs with Automatix if that doesn't work...

---

### Post by Trelo on 2006-06-05
It works now :)  Thank you Titus and codypumper for your support, it's much appreciated.

---

