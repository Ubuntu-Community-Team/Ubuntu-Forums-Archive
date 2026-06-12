---
title: "urgent! nautilus stopped working for me in jaunty"
date: 2009-04-24
forum: General Help
---

### Post by darkweasel on 2009-04-24
Hello everyone,

I yesterday upgraded to Jaunty and started GNOME as normal, but no desktop appeared - only a black screen. The panels appeared as normal.

When starting nautilus from the command line, all I get is:
darkweasel@darkweasel-desktop:~$ nautilus
Segmentation fault
darkweasel@darkweasel-desktop:~$ 

Please help, otherwise I'll probably have to switch to KDE, and I really don't like KDE...

---

### Post by ranch hand on 2009-04-24
Have you tried booting in recovery mode?  Should be the 2nd line on your grub menu.  This will probably find and correct the problem.

---

### Post by ranch hand on 2009-04-24
On your loggin page you can click on "options" and then on "select session".  I would try a Gnome seasion and if that didn't work try Xserver session.  If either come up you can run updates and maybe fix the problem.  There is also "failsafe gnome".

If you can get in and recovery hasn't fixed it I would wipe nautilus and reinstall it.

---

### Post by darkweasel on 2009-04-24
I've meanwhile made it display a desktop background (but still no icons). I'm currently reinstalling nautilus - if only at.archive.ubuntu.com weren't so slow...
Edit: No, didn't work. Neither did your other advice.

---

### Post by ranch hand on 2009-04-24
Well, I'll be jiggered, as my father used to say.

If you can get to your files in your home folder I would back the buggers up and reinstall.

I see that we joined these forums about the same time.  I besides being in agriculture which makes you pretty self reliant, I am a Blacksmith.  We like pushing things to see what happens.  I am pretty good at breaking my system.  This is not real good if you want to use it so this is what I have done.

I install on 2 partitions - 1 root, 1 home for my work install.  I dual boot with the same OS on a single partition and use it to try new stuff before inflicting it on my main OS.  I have had real good luck reinstalling on the 2 partition system on a smaller box that I run Intrepid on.

When I reinstalled on it, I did not back up and used the manual install and set it up so that the root partition was formatted but on the home partition.  Came through with all data intact (you should back up).

I would reinstall after backing your Home directory.  That way you will have a clean install and it will be on ext4 which is native for Jaunty.  I would not, for the world, reccomend going to Kubuntu because I don't think that will solve your problem.

A clean install is always best.

If you have a large enough drive you should be able to get to your files with the live CD and put them in a small partition and then partition to your taste and reinstall.  I would stay on the live CD to transfer your backed up fils back where they belong, then reboot to your newly installed OS.  You may want to boot to it to check before you transfer files but it will be easier on the liveCD as you are a real super user there.  I would live the backup file where ever you put it just to be safe for a while.

---

