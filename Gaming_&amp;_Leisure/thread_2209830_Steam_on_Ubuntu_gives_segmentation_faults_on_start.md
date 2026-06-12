---
title: "Steam on Ubuntu gives segmentation faults on startup."
date: 2014-03-07
forum: Gaming &amp; Leisure
---

### Post by sam38 on 2014-03-07
Hey

I recently installed Ubuntu 13.10 on my main desktop machine after having been running Debian based OS's on my netbook for quite a while now.
One of the first things I did was install Steam from the Steam website (After installing proprietary AMD beta 14.2 drivers for my HD7870). 
To my dismay I when i clicked on the the Steam icon after the install process (which went without errors) nothing happened. 
I then went and ran Steam from the terminal to see any errors.

The output is as follows:

```
Running Steam on ubuntu 13.10 64-bitSTEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140307172506_1.dmp
/home/samathy/.local/share/Steam/steam.sh: line 755: 23800 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
mv: cannot stat ‘/home/samathy/.steam/registry.vdf’: No such file or directory
Installing bootstrap /home/samathy/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME has been set by the user to: /home/samathy/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140307172508_1.dmp
/home/samathy/.local/share/Steam/steam.sh: line 755: 23928 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-add40cdf-69cf-4b49-9027-e98b52140307
Finished uploading minidump (out-of-process): success = no
error: HTTP response code said error



```

As you can see there are no obvious errors in there, nothing about missing dependency or faulty drivers.

I have so far tried googling a lot and not found any similar problems with Steam apart from this one: [http://ubuntuforums.org/showthread.php?t=2203323](http://ubuntuforums.org/showthread.php?t=2203323)
I tried the solution suggested in that thread, but only to be told by apt that i already have libc6 and libc6:i386 installed.
I have also tried doing:
```
steam --reset
```
Which did nothing.

I understand that Valve only official supports 12.04 LTS, however i have Steam (and a few steam games) running on my Ubuntu 13.10 netbook and cant for the life of me understand why I'm getting errors on my desktop, but not on my laptop.

My hardware specs are as follows:

AMD FX 6350
AMD R HD7870 (AMD proprietary drivers.)
12GB DDR3
120GB Samsung 840 EVO

Ubuntu 13.10 + xfce4 (Although steam produces the same errors in Unity, Xfce4 and I3)


This isn't a massive issue for me as most of my games are Windows anyway, and i still have Windows 7 on another partition.

Any help is appreciated!

Thanks.

---

### Post by oldrocker99 on 2014-03-07
I have an nVidia card, and after a reinstall (after breaking my system:redface:), I had a similar problem with Steam insistng that my OpenGL settings being awry. I ended up simply reinstalling the proprietary drivers I had already installed, and the problem was fixed.

Give it a try, anyway.

---

### Post by sam38 on 2014-03-08
Hmm, i'll try that. The thing is, I see no errors complaining about GL settings. So it could be anything!
 
Thanks for the reply.

---

### Post by spectatorx on 2014-03-08
OMFG.... good i've found this thread. Because of the very same problem in last few days are tried all flavours of ubuntu (xubuntu, lubuntu, kubuntu and god knows what else xD ) in various versions (12.04, 13.04, 13.10, 14.04). After reading what you guys posted here i removed fglrx and to be sure if open source driver should work, reinstalled kernel 3.13.6. After reboot steam started without issues! I gave a second try to proprietary driver and installed it again and after reboot steam still works on proprietary driver.

So, temporary workaround is:
If you freshly installed steam and it doesn't want to start and you have proprietary driver installed so steam, for its first run, has to be started on open source driver. You have to remove proprietary driver, reboot pc, run steam, let it update itself and now you can install proprietary driver again, steam will work like it should.


I hope valve will fix their steam package soon.

---

### Post by sam38 on 2014-03-08
Wow thats weird! I have literally just came back to check this thread again after doing exactly what you speak of. And i mean, I rebooted for the last time seconds ago!

For others who come searching - My process was as follows:

Uninstall proprietary AMD drivers.
Reboot
Uninstall and reinstall Steam. (from Steampowered.com)
Start Steam. (And let it update fully then login)
Close Steam
Install Proprietary AMD drivers.
Reboot
Start Steam.
Profit!

Thanks for the help guys, I shall mark as solved once I verify that I can run games. (It seems like it'll be about 3 hours before ive managed to download TF2, If this post is older than that without replies, mods can mark it as solved probs.)

And [COLOR=#000000]SpectorX, Valve only officially support 12.04 LTS so they might never fix their launcher until a new LTS is decided upon :( Cant make to much work for themselves supporting an OS that updates every few months really.[/COLOR]

---

### Post by spectatorx on 2014-03-08
I have hd7790 which is not supported by default kernel in 12.04, at least it is unable to boot in gui mode. Next LTS is fairly soon, april. So far i decided to stay for some time with ubuntu-gnome 14.04 beta 1.

---

### Post by renegade-traceur on 2014-09-11
This issue is a graphics issue... but its a little more nuanced then you  think... I believe Steam only uses mesa-glx for it's opening "updating  steam" screen and then uses native driver glx when actually invoking the  application... which means you probably are using the latest proprietary nvidia  drivers that are installed with the "NVIDIA-Linux-x86_64.XXX.XX..run script and chose the options to install the 32-bit libraries. I was  able to fix the segmentation fault and fix steam by doing the following...

1) Uninstall steam:

$sudo apt-get purge steam*

2) Uninstall the nvidia driver:
     [HR][/HR]Press CTRL+ALT+F1


Then in root:

#service lightdm stop          (or #service gdm stop on Gnome. Note: this stops the xserver)

#cd [location of NVIDIA-Linux-sh-Script]:

#sh NVIDIA-Linux-x86_63.340.35.run --uninstall


[HR][/HR]3) Reinstall the NVIDIA driver 

#sh NVIDIA-Linux-x86_63.340.35.run    

Choose 'NO' when asking to install 32-bit compatibility libraries...

Choose "Yes" to update the xorg.conf

After Driver installation:

Press CTRL+ALT+DELETE to reboot ubuntu.


[HR][/HR]4) In terminal, install steam using apt:

$sudo apt-get install steam -y
   
$steam

Note: steam will update itself and then give you a bunch of "libglx32.so is missing" errors and steam won't open. 


[HR][/HR]5) uninstall and reinstall the NVIDIA drivers with steps 1 and 2 above... but this time choose "yes" when prompted to install the 32-bit compatibility libraries and yes to the xorg.conf update. 

Restart ubuntu with CTRL+ALT+DEL

6)run steam:

$steam

Steam will now prompt you for your account and will work with the native nvidia driver without the segmentation fault.

---

### Post by renegade-traceur on 2014-09-11
Oh crap... nevermind... everyones already got the memo. forget it.

---

