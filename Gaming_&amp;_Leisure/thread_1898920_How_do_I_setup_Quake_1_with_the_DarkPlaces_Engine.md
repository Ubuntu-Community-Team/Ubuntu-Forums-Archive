---
title: "How do I setup Quake 1 with the DarkPlaces Engine?"
date: 2011-12-22
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2011-12-22
Hi.

How do I setup Quake 1 with the DarkPlaces Engine?

I have download the file 'darkplacesengine20110628' from [http://icculus.org/twilight/darkplaces/download.html](http://icculus.org/twilight/darkplaces/download.html).

What is the next step?

Cheers.

Videos:
[http://www.youtube.com/watch?v=X_x4CVgiOS8](http://www.youtube.com/watch?v=X_x4CVgiOS8)
[http://www.youtube.com/watch?v=R14iqJnUtl0](http://www.youtube.com/watch?v=R14iqJnUtl0)

---

### Post by regor210 on 2011-12-22
It seems to have some issues with Linux.

[http://ubuntuforums.org/showthread.php?t=1027860](http://ubuntuforums.org/showthread.php?t=1027860)

Works grate in Wine.

You will need the the id1 file from Quake 1.

[http://icculus.org/twilight/darkplaces/readme.html#HowToInstallQuake_Linux](http://icculus.org/twilight/darkplaces/readme.html#HowToInstallQuake_Linux)

“All that DarkPlaces needs from the Quake CD is pak files, with this in mind, all you need to do is make a ~/quake directory, extract the darkplaces engine zip to that directory, then make a quake/id1 directory, and put the pak0.pak and pak1.pak from your Quake CD into the quake/id1 directory, then all should be well, you will probably also want to make a ~/bin/darkplaces script containing the following text:”

I have it up and going using Wine and the kids love it. No lag on there old x86 computer.

---

### Post by Rytron on 2011-12-23
> **regor210 said:**
> It seems to have some issues with Linux.

[http://ubuntuforums.org/showthread.php?t=1027860](http://ubuntuforums.org/showthread.php?t=1027860)

Works grate in Wine.

You will need the the id1 file from Quake 1.

[http://icculus.org/twilight/darkplaces/readme.html#HowToInstallQuake_Linux](http://icculus.org/twilight/darkplaces/readme.html#HowToInstallQuake_Linux)

“All that DarkPlaces needs from the Quake CD is pak files, with this in mind, all you need to do is make a ~/quake directory, extract the darkplaces engine zip to that directory, then make a quake/id1 directory, and put the pak0.pak and pak1.pak from your Quake CD into the quake/id1 directory, then all should be well, you will probably also want to make a ~/bin/darkplaces script containing the following text:”

I have it up and going using Wine and the kids love it. No lag on there old x86 computer.

Thanks, it works fine. I used a shareware version of Quake.

---

### Post by Brebs on 2011-12-24
> **regor210 said:**
> It seems to have some issues with Linux.
Maybe with pulseaudio (which I don't use), but with ALSA, darkplaces has worked great (for me) for many years.

Running darkplaces through wine is a bizarre choice. Try contacting the darkplaces author through email or IRC.

---

### Post by WienerWuerstel on 2011-12-24
Weird indeed.

I have darkplaces installed and it works just fine with pulseaudio and also natively.

Download the latest darkplaces, extract, cd into the Folder and try to run it via Terminal like this and tell us the output
```
./darkplaces-sdl /path/to/quakefolder
```PS: /path/to/quakefolder should be replaced by your actual Folder Name

---

### Post by ubonetu on 2013-04-07
I had problems from a PC version of quake.  I found that I needed to rename all the files so they were lowercase.  I found this bash command for the linux command line.  If anybody out there just can't seem to get quake to work and has tried everything, try changing all your files in the quake/id1 directory with this:

> find my_root_dir -depth -exec rename 's/(.*)\/([^\/]*)/$1\/\L$2/' {} \;

I just put a "." in for "my_root_dir" and it worked great.

Hope it helps somebody

---

