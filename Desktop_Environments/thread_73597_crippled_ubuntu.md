---
title: "crippled ubuntu"
date: 2005-10-09
forum: Desktop Environments
---

### Post by xolot1 on 2005-10-09
I'm only 2 or so months into linux, but ive loved playing with it.

yesterday, i messed up something with a c compiler (as best as i can figure), so when i restarted, GNOME didnt work.  Again, thats just what i can figure.

but those are just petty details.

i was planning to reinstall unbuntu anyways, so nows a great time i figured.  i see that 5.10 is coming out on the 13th, so ill reinstall then.

heres the question:
since i cant easily log onto ubuntu, and im not yet confident at the terminal, im trying to use a live CD to recover my important data (DSL if you care).

the thing is, i dont really know how to mount the harddrives ubuntu used.
there are also some files that windows had (i dual booted, tho i only ever used ubuntu) that i'd like to save.

how would i go about finding what devices hold this data, and how to mount them?

---

### Post by aysiu on 2005-10-09
I'd follow these instructions:

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by Emerzen on 2005-10-09
I'm not sure of the capabilities of the Ubuntu Live CD...I typically use a copy of Knoppix for repair work if needed as it comes loaded w/ software.  So, you can download a copy of Knoppix, which will recognize all your hardware (even Windows partitions) and allow you to read/write to all your partitions...so you can grab what you want.  If you're going to reinstall Ubuntu though, I would leave your Windows partition be as it will be recognized by the new install.  [www.distrowatch.com](www.distrowatch.com) will have a link to the download for Knoppix.  Again, you may be able to do this w/ Ubuntu Live, I've never used it though.

---

### Post by xolot1 on 2005-10-09
will knoppix mount the partitions automatically?
i was trying to read about how to force a mount, but i couldnt figure out/remember what the names of the devices were (hda, etc)

ive fixed the windows files, so now i only need to access what i had under ubuntu (thunderbird profile, etc)

---

### Post by 5-HT on 2005-10-10
[QUOTE=xolot1]will knoppix mount the partitions automatically?
[/QUOTE]

Knoppix should automatically mount the partitions (though it'll mount NTFS ones as read only)


HTH

---

### Post by Emerzen on 2005-10-10
for a list of your devices use:

sudo fdisk -l

Knoppix will likely mount all of your partitions or they will show up on your desktop as an icon, right click it and select mount.

---

### Post by xolot1 on 2005-10-10
ok, so i have the knoppix live dvd running, but all the partitions are read only.

im probably missing something stupid, but how can i access them, and actually do something?

(btw, knoppix is very pretty)

---

### Post by Emerzen on 2005-10-10
I don't have Knoppix running and it's been awhile since I've used it.  But, I believe you have to set a root password before you can change read/write permissions.  Hunt around in the system utilities section...there's a utility for setting the root password.    Then you can change the permissions and do whatever you like.  BTW, if you like the look of Knoppix, it's KDE desktop (Kubuntu) instead of Gnome.

---

### Post by 5-HT on 2005-10-13
[QUOTE=xolot1]ok, so i have the knoppix live dvd running, but all the partitions are read only.

im probably missing something stupid, but how can i access them, and actually do something?

(btw, knoppix is very pretty)[/QUOTE]

It's been a while since I've last used knoppix as well, but I believe that if you right click on the desktop icons of the partitions there should be some sort of permissions/preferences/options tab which will enable you to select write access .

I don't think you need to do anything about unlocking the root password as I don't remember having to do so in the past, though I could easily be mistaken.

---

