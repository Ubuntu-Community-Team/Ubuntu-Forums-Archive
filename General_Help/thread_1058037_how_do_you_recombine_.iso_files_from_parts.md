---
title: "how do you recombine .iso files from parts"
date: 2009-02-02
forum: General Help
---

### Post by dharkus on 2009-02-02
i have or am going to have in the next few days 8 .iso files of something from the internet that is big enough so that it needs to be in parts    (6.9 GB) - they are named [name].iso.001, [name].iso.002 up to [name].iso.008
i was wondering how i would go about recombining these files into one iso file or maybe 2 - so that i can fit it on 2 dvds
what programs would i need to do this and how would i use them for this - i have atm iso master and brasero disc burning and of course the cd/dvd creator

---

### Post by kbutcher5 on 2009-02-02
You can make one iso file out of them, this is done by installing unrar on your pc, and then opening the first file in the row with file-roller, also known as the unzipping/zipping tool of gnome.
Then you drag and drop, then it should extract it, happy trails!

---

### Post by dharkus on 2009-02-02
thanks for that - i'll try that when i have the rest of em - downloadin em all (950MB/file) on a 512Kb/s connection - oh the joy - 4-5.5 for each on and each one is unresumable!! and with dodgy uni wireless internet which randomly cuts out

---

### Post by dharkus on 2009-02-02
is there a gui for unrar - i can't seem to find one at all - i can only find it when i enter 'unrar' in terminal

---

### Post by binbash on 2009-02-02
You will join them with lxsplit

---

### Post by dharkus on 2009-02-02
what do u mean by that - what is the syntax for that command if it is even a command

---

### Post by binbash on 2009-02-02
you join that files with hjsplit at windows. lxsplit is a similar tool for that.[http://lxsplit.sourceforge.net/](http://lxsplit.sourceforge.net/)  It is  very easy to use the tool.

To merge (join) the already split pieces into the original big file, run this command:

    lxsplit -j smallfiles.bin.001

There is a deb at the site also

---

### Post by harlan on 2009-02-02
I think this does the work
> $cat file1 file2 > newFile.iso 

---

### Post by adamlau on 2009-02-02
cat usually does the job, but not always. Use with caution :) .

---

### Post by jerome1232 on 2009-02-02
> **dharkus said:**
> is there a gui for unrar - i can't seem to find one at all - i can only find it when i enter 'unrar' in terminal

The default file archiver in ubuntu works with unrar, so once unrar is installed you can open archives with file-roller.

edit: joining the files really depends on how they were split, if they are just one giant iso file literally broke into pieces then cat will do it. But if some utility was used that broke a giant iso file into several seperate true iso's then cat will not work.

So backup your originals before attempting the join operations!

---

### Post by dharkus on 2009-02-02
i think it was probably split into seperate pieces - each of which is not an actual iso but i will make sure i back em up - might possibly be recombining them in windows as that's the only way i know of to play this thing as it's an .exe and this laptop isn't actually good enough to play any thing in wine - not even warcaft 3 - the only game i've managed to play is a snes game in an emulator so far

---

