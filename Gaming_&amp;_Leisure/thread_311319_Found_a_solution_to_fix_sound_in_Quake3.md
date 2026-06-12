---
title: "Found a solution to fix sound in Quake3"
date: 2006-12-02
forum: Gaming &amp; Leisure
---

### Post by PuZo on 2006-12-02
I've been searching for a solution to fix sound in Quake3 under Ubuntu 6.10 for a few days now. I've tryed them all, none of them worked. Except for this one:

Download this .RPM: [**quake3-1.33-0.1.svn338.2.fc4.i386.rpm**]("ftp://fr.rpmfind.net/linux/freshrpms/fedora/linux/4/quake3/quake3-1.33-0.1.svn338.2.fc4.i386.rpm") and open it with some archive manager (i.e. File Roller).
Then simply extract to your Quake3 directory (default is /usr/local/games/quake3/) the folowing files/folders from the .RPM:
```
baseq3/
missionpack/
quake3
q3ded (optional)
```
You will be asked to replace the files/folders; select Replace All.

Now create a launcher (say on your Desktop) that contains the command '/usr/local/games/quake3/quake3' (assuming that /usr/local/games/quake3 is your path to the game).
Start the game with that launcher.

Hope this works for you ! :D 

PS: Just one small issue with this "patch": the image is very dark, even if I set the ingame brightness level to the max. Anyone that finds a solution to this issue is welcome to post it here.

**Edit:** I left my '~/.q3a/baseq3/q3config.cfg' unchanged (seta snddevice "/dev/dsp").

---

### Post by fifafrazer on 2007-01-28
Fileroller tells me that the archive type is unsupported. I'm using Ubuntu 6.10. How can I else extract the rpm?

---

### Post by PuZo on 2007-02-13
I just use "Open with Archive Manager" and browse it.
Maybe you need to do a:
```
sudo apt-get update
sudo apt-get upgrade
```

---

