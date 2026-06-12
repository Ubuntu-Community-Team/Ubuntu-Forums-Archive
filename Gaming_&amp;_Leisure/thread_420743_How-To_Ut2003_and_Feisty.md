---
title: "How-To: Ut2003 and Feisty"
date: 2007-04-23
forum: Gaming &amp; Leisure
---

### Post by murlosad on 2007-04-23
How-to install Unreal Tournament 2003 in Feisty Fawn using the installer from disc 3.

After Days of searching the internets, I finally got UT2003 to install properly. Here's how:

Note: For the purposes of this how-to we will assume that you have 3d acceleration working properly.
> glxinfo | grep direct should say > direct rendering: Yes

Note: Just to be clear **username** = your username in any of the commands listed

Now, to the fun:

Step 1.

Copy linux_installer.sh from disc 3 to your harddrive (e.g. /home/**username**)
Easy way with this command:
> cp /media/cdrom/linux_installer.sh /home/**username**
Then make it executable:
> chmod a+x linux_installer.sh

Step 2.

Eject disc 3 from your system and insert disc 1

Step 3.

Tell the installer where to look for the cdrom (this step may or may not be necessary on your system, I couldn't get the installer to do anything without it).
> export SETUP_CDROM=/media/cdrom
you may have to change the path to /media/cdrom0 or cdrom1, but this worked for me.
(source: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+UT2003](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+UT2003))

Step 4.

Fix the glibc problem. (The installer from the cd wants glibc-2.1 which doesn't seem to be the correct version anymore, so this command essential tells it that you do have 2.1, and like magic, it works)
> export SETUP_LIBC=glibc-2.1
(source: [http://ubuntuforums.org/showthread.php?t=262340&highlight=glibc-2.1](http://ubuntuforums.org/showthread.php?t=262340&highlight=glibc-2.1))

Step 5.

Run the installer from the directory you saved it into (e.g. /home/**username**)
> sh linux_installer.sh or > sudo sh linux_installer.sh if you want to install the game somewhere you don't have write permissions. (e.g. /usr/local/games)

This should give you a license agreement, which of course you need to agree to. Then it will give you an opportunity to change the install directory but you can probably leave that alone.

The installer can take quite awhile to work, but at some point you will have to change the cd to disc 2 (which the installer calls disc 1) and disc 3 (which it calls disc 2).

Step 6.

Enter your cd-key twice. You want to enter it exactly as it is on the case, capital letters and all. (I had some trouble with this part, it kept telling me that the cd-keys didn't match)

You can manually add it to */usr/local/games/ut2003/System/cdkey* (if you didn't change the default install dir) in the format *AAAAA-BBBBB-CCCCC-DDDDD* or even just in your ***username**/.ut2003/System/cdkey* to prevent that the CDkey is visible for all Users logged into this machine. (source: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+UT2003](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+UT2003))

Step 7.

Play! you can run the game with > ./ut2003 from your home directory, assuming you didn't tell the installer not to make a shortcut for you. (it does create on by default)

Hope this helps someone, if not, at least it will be available the next time I have to install ut2003 :)

//Bonus Packs can be obtained here: [http://icculus.org/~ravage/ut2003/](http://icculus.org/~ravage/ut2003/)

---

### Post by dboot on 2007-04-25
Thanks for the howto!

I'm still having trouble installing.

After copying the installer to my home folder, I run "export SETUP_LIBC=glibc-2.1", then "sudo sh linux_installer.sh" from my home folder. The installer starts but then returns this error:

```
Decompressed ../BarrensHardwareBrush.utx.uz2 -> ../BarrensHardwareBrush.utx
cp: reading `Textures/BarrensTerrain.utx.uz2': Input/output error
failed to uncompress file.
Aborted (core dumped)
.setup10496: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed.
Aborted (core dumped)
The setup program seems to have failed on x86/glibc-2.1

Fatal error, no tech support email configured in this setup
The program returned an error code (1)

```

Thanks for help!

---

### Post by murlosad on 2007-04-25
> **dboot said:**
> Thanks for the howto!

I'm still having trouble installing.

After copying the installer to my home folder, I run "export SETUP_LIBC=glibc-2.1", then "sudo sh linux_installer.sh" from my home folder. The installer starts but then returns this error:

```
Decompressed ../BarrensHardwareBrush.utx.uz2 -> ../BarrensHardwareBrush.utx
cp: reading `Textures/BarrensTerrain.utx.uz2': Input/output error
failed to uncompress file.
Aborted (core dumped)
.setup10496: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed.
Aborted (core dumped)
The setup program seems to have failed on x86/glibc-2.1

Fatal error, no tech support email configured in this setup
The program returned an error code (1)

```

Thanks for help!

Well, I'm at work right now, so I can't test anything.  What I would try is this:

do the 'export SETUP_LIBC=glibc-2.1' again, and then run the installer as a normal user.

If that still fails, try 'sudo export SETUP_LIBC=glibc-2.1' and 'sudo sh linux_installer.sh.'  To be honest, I know that the 'export SETUP_LIBC=glibc-2.1' sets the SETUP_LIBC variable to glibc-2.1, which is what the installer looks for, but I don't know for sure if it sets it system wide or is user specific. I ran both commands as a normal user on my machine.

Post if you need more help, I might be able to do more when I get home. in like 5 hours :(

---

### Post by dboot on 2007-04-25
Fixed.

I simply attempted to install ut2k3 over and over. I kept getting the same error at different parts of the installation. After the 4th attempt, the install worked. However, it did not accept my cdkey, so I created /usr/local/games/ut2003/System/cdkey with my cdkey in it.

Next, I'm running Beryl and have twinview enabled. Do you know if I have to disable both in order to run UT?

Thanks!

---

### Post by dboot on 2007-04-25
I was able to update ut2003 and can play just fine.

I have two more questions:

Any idea why my sound doesn't work?

Is there anyway to copy my settings from my windows installation (as in User.ini and UT2003.ini) to my Linux installation?

Thanks again!

---

### Post by murlosad on 2007-04-26
You probably want to disable beryl before you run ut2k3, I'm not sure about twinview as I haven't used it in a long time.

As far as your user settings.. in linux they are stored in ~/.ut2003/System as .ini files so I would compare the two and see if there are any major syntax differences.  Or you could just backup your linux .ini's and copy them over from windows and see what happens.

Don't know why the sound isn't working, mine works fine. Are you using Alsa or OSS?

---

### Post by dboot on 2007-04-26
I found a few ini files in the System folder. It looks like I'll have to manually change the syntax of my Windows ini files for them to work properly.

I followed the README.linux file for the FAQ of "why my sound doesn't work." It had a simple command that I ran and fixed the problem. Now, the bass in my shock combos are really really loud (haha).

Thanks for the help.

---

### Post by paducahguy on 2007-12-05
I managed to install the game.. But once I did the screen was stretched to far when I ran the game... I also was only able to run the game under sudo ut2003 ... Without the cd key at that... Which shouldn't be capable and without the cd in the drive.. I am unsure if what I installed was right...but why won't it accept the cd key I have on my case ? and why won't it run without being sudo ... 

Also when i tried to do the join a server thing it would tell me unable to move the map file. or whatever file it downloaded and quit the server immediately... offline play was ok without the screen still being messed up being the only offline issue... 

In short.. I'm doing an rm -r on ut2003 because it's too buggy for me to successfully install it and get the key to realize it's the right cd :(

unless someone has some better ideas ? 

email me or send a pm via the forum... thanks all !

---

