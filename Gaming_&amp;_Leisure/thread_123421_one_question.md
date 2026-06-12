---
title: "one question"
date: 2006-01-30
forum: Gaming &amp; Leisure
---

### Post by PLAY3ER on 2006-01-30
is anyone using TS2 with another game at the same time on Kubuntu? on Ubuntu i can't seam to get it working so im downloading Kubuntu now to try it.\\:D/ 


                                                                     Thanks, Ryan

---

### Post by joft on 2006-01-30
Hi,

I had similar problems or you can also say: the well known issue (with linux) and "concurrent" sound applications. I tried many different solutions/hacks, but if you have got a cheap sound chip (laptop), which is not able to do mixing in hardware .......

Then I found another "hack" myself, which I haven't seen yet in all the forums and mailing lists out there. Now I am using it for about 2 months and till now it works:

The problem is that ALSA does mixing with dmix plugin - but it does not work with its OSS emulation AND some application do NOT support dmix. My "solution":

- JACK as "sound server" (JACK is optimized for realtime stuff)
  => JACK uses ALSA as output
- Use applications which have a JACK output driver
- Use special tool "oss2jack" which emulates a OSS device and reroutes everything to JACK

=> Result: Every app which is able to output to JACK or to OSS is able to do so SIMULTANEOUSLY.
Amoung other things I tested TS2 (OSS) together with ET (OSS), Skype (OSS) and other apps, Cedega/Wine (OSS).

I even created some packages (.deb's) .... if you are interested, just tell me ...

---

### Post by PLAY3ER on 2006-01-30
i am, i hate windows but this is the only thing holding me back from taking windows off because im in a clan for ET and COD2 and i need TS with both. any help you can give me and thank you, 

MSN:ryan.macintosh@gmail.com

PS:thanks again

---

### Post by PLAY3ER on 2006-01-30
im going back to Ubuntu no more of this KDE crap, sorry guys for who loves it but its not working for me

---

### Post by PLAY3ER on 2006-01-30
k done, need deb's? plz

---

### Post by joft on 2006-01-31
**[SIZE="4"]Software mixing with JACK and oss2jack[/SIZE]**

**Problem:** ALSA supports **software mixing** by its dmix plugin (for sound cards which do not support that in hardware). dmix is working with ALSA apps, but there are ALSA application which do not work with dmix, they just block the whole ALSA device.
And OSS apps which are forced to use ALSA OSS emulation can't be dmix'd, they also block the whole sound device.

**Solution:** Sound servers: artsd (KDE), esd, polyp (GNOME), ... others. Sound application have to have special output drivers to use them and most have. 
But some applications don't have such drivers. Then you would have to use wrappers (artsdsp, esdsp) which "try" to catch the calls of the applications (in userspace) and reroute them to their sound servers.
These wrappers sometimes work great (artsdsp/KDE) or bad (esddsp/GNOME) (at least on my computer).

**Solution described here:** Use of JACK as sound server (although JACK is more than a sound server, I know ...) and oss2jack, a special tool which emulates an OSS device and reroutes the data to JACK.
Then all OSS application will be able to open the sound device at the same time and play at the same time.
Other application do often have jack output drivers (xmms, mplayer), so                         they will also be able to play at the same time.

**Important assumptions made in this HOWTO: You are using Ubuntu 5.10 with GNOME and ALSA. Your sound card works.**

**Note 1**: I'm neither an expert in sound stuff nor an ubuntu developer, so tell me, if I'm saying something wrong.

**Note 2**: If you really need *perfect* sound mixing, IMO you will still have to buy a "real" sound card with a sound chip which is able to do it in hardware.
I tested this solution with xmms, mplayer playing files and talking to somebody in skype at the same time. I also tested with TS2 and ET at the same time. 
Since 2 months now, it works - at least for me - very well.

**Note 3**: [laparel]("http://ubuntuforums.org/member.php?u=89420") asked me to include instructions to use **this HOWTO on Kubuntu**, that means with KDE instead of GNOME. In fact it's really easy, because all you have to do is: **leave out step 4, 9 and 13** - just ignore them. Instead **configure artsd** (in KDE's Control Center) to use OSS or jack (instead of ALSA or "Auto").
**The problem is**: Somehow we need to instruct KDE to start jackd and oss2jack right after login (compare step 9 under GNOME), but at the moment I don't know how - well, you could do it manually - but that's not what we want :neutral: .
And remember that you have to configure all your application to use either artsd, OSS or jack as output. Furthermore - one last word on KDE - consider using artsdsp [SIZE="1"](wrapper to re-route output of application not supporting artsd to artsd, see above)[/SIZE] instead of this solution, if you are using Kubuntu/KDE.

**Installing needed packages:**

**1.** [COLOR="Red"]Add[/COLOR] the following [COLOR="Red"]repository[/COLOR] to your /etc/apt/sources.list file:

```
deb http://neogate.homelinux.org/debian/ breezy sound
```

Don't forget to update your package system. To do this you can do:

```
sudo apt-get update
```

**2.A** Then [COLOR="Red"]install jackd[/COLOR] from breezy and [COLOR="Red"]oss2jack[/COLOR]
from the repository given above by typing:

```
sudo apt-get install jackd oss2jack
```

**NOTE:** During the installation of the package "oss2jack" you'll get asked 2 questions.
The first one says *"Do you want to disable the ALSA OSS modules?"*. For this HOWTO to work, you have to choose "Yes".
The second question says: *"Do you want to unload the ALSA OSS modules now?"*. You may choose "Yes" here, too. You could do that manually, too (see step 11), but it won't hurt to let the installation try to unload them.

*_Now do step 2.B **OR** step 2.C, not both, only one of them depending on the kernel you have installed:_*
**2.B** In my repository are pre-build kernel modules for **breezy kernel 2.6.12-10**. If you have installed this kernel, do:

```
sudo apt-get install fusd-kor-module-`uname -r` fusd-kor
```

**2.C** **If** you have an **other breezy kernel** (e.g. 2.6.12-9) or a **selfmade one**, you will have to [COLOR="Red"]install fusd-kor-source instead[/COLOR] of the pre-build module and build your own fusd-kor-module package.
First you have to prepare your system for module compilation. To do that, install module-assistant:

```
sudo apt-get install module-assistant
sudo m-a prepare
sudo apt-get install gcc-`grep LINUX_COMPILER /usr/src/linux/include/linux/compile.h | sed 's/.* \([0-9]\+\.[0-9]\+\).*/\1/'`

```

The second command will make module-assitant (m-a) install the needed linux-headers packages. [SIZE=1](If you have a selfmade linux-kernel package, you (probably) will have to manually install your own linux-headers package.)[/SIZE] The last command here, makes sure that you have got installed the right version of gcc (GNU C Compiler).

Then, install fusd-kor-source and build your own fusd-kor-module packages:

```
sudo apt-get install fusd-kor-source fusd-kor
sudo m-a a-i fusd-kor
```

In the last command m-a will do all the stuff needed to configure, build and install your own fusd-kor-module package automatically.

**NOTE on step 2.B and 2.C:** During the installation of the package "fusd-kor" you'll get asked 2 questions.
The first one says *"Do you want the fusd-kor kernel module to be loaded during the boot process?"*. For this HOWTO to work, you have to choose "Yes".
The second question says: *"If needed, you can specify commandline parameters ..."*. Do not enter anything there, leave it blank.

**3.** I also [COLOR="Red"]installed the realtime kernel module[/COLOR], so that jackd and oss2jack are able to run with a higher priority.
First you have to prepare your system for module compilation. To do that, install module-assistant:

```
sudo apt-get install module-assistant
sudo m-a prepare
sudo apt-get install gcc-`grep LINUX_COMPILER /usr/src/linux/include/linux/compile.h | sed 's/.* \([0-9]\+\.[0-9]\+\).*/\1/'`

```

The second command will make module-assitant (m-a) install the needed linux-headers packages. [SIZE=1](If you have a selfmade linux-kernel package, you (probably) will have to manually install your own linux-headers package.)[/SIZE] The last command here, makes sure that you have got installed the right version of gcc (GNU C Compiler).

Then, install realtime-lsm-source and build your own realtime-lsm-module packages:

```
sudo apt-get install realtime-lsm-source realtime-lsm
sudo m-a a-i realtime-lsm
```

In the last command m-a will do all the stuff needed to configure, build and install your own realtime-lsm-module package automatically.

**4.** Usually the package "libesd-alsa0" is installed to allow esd to output to ALSA. But since we are going to use JACK (and jackd blocks the ALSA sound device), you need to [COLOR="Red"]replace "libesd-alsa0" with "libesd0"[/COLOR], which enables esd to output to OSS devices.

   ```
sudo apt-get install libesd0
```

   This way, esd (which is responsible for all "GNOME desktop sounds") will output its stuff to our emulated OSS device by oss2jack.


**Configuring the installed software**

**5.** This **step is obsolete** as of today (02/04/2006). The repository given above in step 1 has an updated fusd-kor package, which does the job of this step automatically.
[I][SIZE=1]Old text was:
[COLOR="Red"]Add a new line containing "kfusd" (without ") to your /etc/modules file.[/COLOR] oss2jack uses this module to emulate the OSS device. This way, it will be loaded as part of the boot process.[/SIZE][/I]

**6.** This **step is obsolete** as of today (04/12/2006). The repository given above in step 1 has an updated fusd-kor package, which does the job of this step automatically.
Old text was:
[I][SIZE=1]Due to the fact that we want oss2jack to emulate the *first* dsp device (/dev/dsp), you have to [COLOR="Red"]make sure that the ALSA OSS emulation modules do *not* get loaded.[/COLOR] Otherwise they will occupy /dev/dsp . Simply copy over the examples file, which configures modprobe (module loading) the right way:

   ```
sudo cp /usr/share/doc/oss2jack/examples/oss2jack.modprobe /etc/modprobe.d/oss2jack
```[/SIZE][/I]

**7.** To be able to run jackd and oss2jack with a higher priority, you have to [COLOR="Red"]make sure that you are a member of the "audio" group[/COLOR]. This is also needed due to the owner/group settings of the device files of the kfusd kernel module. If in doubt, do:

   ```
sudo adduser <your_username> audio
```

**8.** Moved. This is step 13 now.


**Start jackd and oss2jack after login (automatically)**

**9.** GNOME automatically starts its esd (GNOME's sound server) after login, so that you can hear the login sound etc. In the first section you configured esd to output to OSS devices (step 4.).
So we need to [COLOR="Red"]start our jackd/oss2jack combination before esd gets started[/COLOR].   To do that we use the ~/.gnomerc file, which is executed before any GNOME stuff gets started after login. You will find the script I use in /usr/share/doc/oss2jack/examples/.gnomerc , so copy it over to your home directory:

   ```
cp /usr/share/doc/oss2jack/examples/.gnomerc ~/.gnomerc
```

   I admit, that my script is some kind of a (dirty) hack ... just in case you wonder about loop at the end.


**It's nearly done :D**

**11. Only needed if you don't want to reboot now**, you will have to load the kfusd and the realtime module manually. Next time you do a reboot it will get loaded automatically (step 5/step 3). Furthermore you have to unload the ALSA OSS emulation modules. If you choose to unload them during the installtion of the package oss2jack (step 2), they shouldn't be there anymore, but it doesn't hurt to "rmmod" them again (so there might appear an error message saying "Module XXX does not exist ..." - just ignore it). On future reboots they will be prevented from being loaded automatically, too (step 6).

```
sudo /etc/init.d/fusd-kor start
sudo /etc/init.d/realtime start
sudo rmmod snd-pcm-oss
sudo rmmod snd-mixer-oss
```

**12.** Now at least you have to logout and login again, so that your ~/.gnomerc script gets executed.

**13.** Usually [COLOR="Red"]gstreamer[/COLOR] is installed and configured to use ALSA as out- and input. But - same reason as with esd (step 4.)- we need it to [COLOR="Red"]output to our emulated OSS device[/COLOR] by oss2jack. Go to:

   System -> Preferences -> Multimedia Systems Selector

and chose OSS (output and input).


**Configuring (other) sound application**

Here is a list of applications and with which output driver I use them:

- esd ... oss	(configured above, step 4.)
- gstreamer ... oss	(configured above, step 8.)

- xmms ... jack
- mplayer ... jack
- vlc ... oss
- gxine ... oss
- licq ... use "esdplay" in Licq Menu -> Options -> OnEvent: Command
- wine ... oss (wine needs a patch, see the resources section below)

Applications like audacity, TS2, Skype, ET, ... can use OSS only, so they will use our emulated OSS device by oss2jack.


**(Other) resources around this HOWTO**

- Little (external) "homepage" of this HOWTO [http://neogate.homelinux.org/howto-oss2jack/]("http://neogate.homelinux.org/howto-oss2jack")

- oss2jack: [http://fort.xdas.com/~kor/oss2jack/]("http://fort.xdas.com/~kor/oss2jack/")

- JACK: [http://jackit.sourceforge.net/]("http://jackit.sourceforge.net/")

[COLOR="Red"][B]=====================================================================
END OF HOWTO
=====================================================================[/B][/COLOR]

[INDENT][INDENT]If you don't like the result of this HOWTO or if you have to reverse the whole thing because of some other reason, here's a **list**, what you have to do to **switch back to ALSA/dmix**. I used the same step numbers as in my HOWTO:

**9.** Remove ~/.gnomerc

```
rm ~/.gnomerc
killall esd
killall oss2jack
killall jackd
```

**8.** Go to

System -> Preferences -> Multimedia Systems Selector

and select ALSA (for both input and output).

**6.** Remove /etc/modprobe.d/oss2jack

```
sudo rm /etc/modprobe.d/oss2jack
```

**5.** Remove the line "kfusd" from your /etc/modules file, **only if** you have added one before (see step 5 above in the HOWTO).

**4.** Replace the package "libesd0" with "libesd-alsa0", by doing:

```
sudo apt-get install libesd-alsa0
```

[SIZE="1"]**2.A(B|C) + 3.**[I] Now, if you like you could further uninstall the rest of the software packages, but you don't have to. E.g.:
```
sudo apt-get remove oss2jack fusd-kor* jackd realtime-lsm* 
```[/I][/SIZE]

**11.** If you don't want to reboot now, you have to load the ALSA OSS emulation modules again:

```
sudo modprobe snd-mixer-oss
sudo modprobe snd-pcm-oss
```

**13.** Now at least you have to logout and login again, so that esd is getting started again by GNOME.
[/INDENT][/INDENT]

---

### Post by PLAY3ER on 2006-01-31
i got stoped on #3, on sudo m-a a-i realtime-lsm "Bad Luck, The Kernel Headers for the traget kernal could not be forund and you did not specify any others"

PS: at boot up the line to boot Ubuntu has a 9 at the end of it not a 10 ?

PSS: root@ubuntu:~# cp /usr/share/doc/oss2jack/examples/oss2jack.modprobe /etc/modprobe/oss2jack
cp: cannot create regular file `/etc/modprobe/oss2jack': No such file or directory


PSSS: after i get pased this i need to ask you about wine to

---

### Post by PLAY3ER on 2006-01-31
what did i do now, it whon't login in less i login it GNOME,

PS: torrow night i'll reinstall Ubuntu to have a freash installion

---

### Post by joft on 2006-02-01
> i got stoped on #3, on sudo m-a a-i realtime-lsm "Bad Luck, The Kernel Headers for the traget kernal could not be forund and you did not specify any others"

PS: at boot up the line to boot Ubuntu has a 9 at the end of it not a 10 ?
So you have an older kernel ... hmmm ... but I don't understand why m-a (module-assistant) is complaining about it. There *are* kernel headers for 2.6.12-9 in the archive (breezy/main).

What did you do in step 2? Did you install one of my precompiled modules or did you use step 2.1 and build your one? Because - as I wrote - my precompiled modules are for 2.6.12-10 ... so you used step 2.1, right? No error there?

You could install the kernel headers for 2.6.12-9 manually. Assuming you arr using linux-image-2.6.12-9-386 you would do (replace 386 with your flavour):
```
sudo apt-get install linux-headers-2.6.12-9-386
```
Then try step 3 (and step 2.1 again).



> PSS: root@ubuntu:~# cp /usr/share/doc/oss2jack/examples/oss2jack.modprobe /etc/modprobe/oss2jack
cp: cannot create regular file `/etc/modprobe/oss2jack': No such file or directory

Ok ... my fault ... typo, it has to be:
```
sudo cp /usr/share/doc/oss2jack/examples/oss2jack.modprobe /etc/modprobe.d/oss2jack
```



> what did i do now, it whon't login in less i login it GNOME,

PS: torrow night i'll reinstall Ubuntu to have a freash installion
Hmmm, I don't understand the first sentence here? Your are not able to login anymore? But you get the normal login prompt?

---

### Post by PLAY3ER on 2006-02-01
[QUOTE=joft]So you have an older kernel ... hmmm ... but I don't understand why m-a (module-assistant) is complaining about it. There *are* kernel headers for 2.6.12-9 in the archive (breezy/main).

What did you do in step 2? Did you install one of my precompiled modules or did you use step 2.1 and build your one? Because - as I wrote - my precompiled modules are for 2.6.12-10 ... so you used step 2.1, right? No error there?

no i did 2 i gess i was wrong sorry

Ok ... my fault ... typo, it has to be:
```
sudo cp /usr/share/doc/oss2jack/examples/oss2jack.modprobe /etc/modprobe.d/oss2jack
```

np,thx


Hmmm, I don't understand the first sentence here? Your are not able to login anymore? But you get the normal login prompt?[/QUOTE]

its something i did don't worry i know what happend.

PS: i'll try this with i get Ubuntu back on,. wich im going to do right now.

---

### Post by PLAY3ER on 2006-02-01
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)


i think the URL+server must be down, i'll try later

---

### Post by PLAY3ER on 2006-02-01
What did you do in step 2? Did you install one of my precompiled modules or did you use step 2.1 and build your one? Because - as I wrote - my precompiled modules are for 2.6.12-10 ... so you used step 2.1, right? No error there?

i do get an error
root@ubuntu:~# sudo apt-get install fusd-kor-module module-assistant Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package fusd-kor-module



```

```Ok ... my fault ... typo, it has to be:
```
sudo cp /usr/share/doc/oss2jack/examples/oss2jack.modprobe /etc/modprobe.d/oss2jack
```

still doesn't work 

with old or new, but i think i need to pass the 2.1 thing before i can do this right?

---

### Post by PLAY3ER on 2006-02-01
nvm i got it me bad i did add repository to the progrman just to the file

---

### Post by PLAY3ER on 2006-02-01
new problem i got done doing everything! now it whon't start as user ryan i need to use failsafe thats the only way i ccan get in plz help

---

### Post by PLAY3ER on 2006-02-01
ryan@ubuntu:~$ sudo modprobe kfusd
Password:
FATAL: Module kfusd not found.


PS: is their a way you can connect to my computer and look at this if you don't mind im getting :mad:  but im not giving up email though because if you will i can give you my user password

---

### Post by PLAY3ER on 2006-02-01
when i do  System -> Preferences -> Multimedia Systems Selector and go OSS for both i hit Test and it gives me an error 

Failed to construct test pipeline for 'OSS -Open Sound System'

---

### Post by joft on 2006-02-02
> **joft]What did you do in step 2? Did you install one of my precompiled modules or did you use step 2.1 and build your one? Because - as I wrote - my precompiled modules are for 2.6.12-10 ... so you used step 2.1, right? No error there?
[QUOTE=PLAY3ER]
i do get an error
root@ubuntu:~# sudo apt-get install fusd-kor-module module-assistant Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package fusd-kor-module
[/QUOTE]
[/QUOTE]

Ok ... again - sorry - my fault. Although the text above the code is correct, the code is wrong. The name of package has to be fusd-kor-source:

```
sudo apt-get install fusd-kor-source module-assistant
```

I just updated the HOWTO, which now also shows right name. When you look at the HOWTO you will see, that I re-structured the whole step 2 a bit to make it clearer .... so don't get confused when looking at it after reading this  said:**
> still doesn't work

with old or new, but i think i need to pass the 2.1 thing before i can do this right?

Yes. In fact you have to pass every step to get it right :D. (Well, you could skip the realtime stuff ... but this is not recommended).

----------------------------------

> ryan@ubuntu:~$ sudo modprobe kfusd
Password:
FATAL: Module kfusd not found.

when i do System -> Preferences -> Multimedia Systems Selector and go OSS for both i hit Test and it gives me an error

Failed to construct test pipeline for 'OSS -Open Sound System'

It seems, that somehow you did not install the fusd-kor kernel module and thus oss2jack does not start and because of that the MM Systems Selector gives this error.

----------------------------------

> PS: is their a way you can connect to my computer and look at this if you don't mind im getting but im not giving up email though because if you will i can give you my user password

I can try, ... I'll contact you by email.

---

### Post by aaronwh98 on 2006-02-02
Hi, 

I've been trying to get MIDI and Rosegarden to work on my box.  Jack will connect fine to ALSA but then I get no sound whatsoever until I disconnect Jack.  Then I get sound (but no MIDI of course).  I've tried everything on this site except I have the following problem when I try to start oss2jack:

!!!Scheduler set to Round Robin with priority 10 FAILED!!!
libfusd: /dev/fusd/control does not exist; ensure FUSD's kernel module is installed
Could not create sound device
: Package not installed

If I "modprobe kfusd", I get no errors so the package seems to be installed correctly.  

Any ideas?

Honestly, I wouldn't care if I didn't have any other sounds but MIDI when I connect Jack because I could disconnect it when I want to do other stuff.  I just want to be able to use RoseGarden.

Thanks

---

### Post by joft on 2006-02-02
[QUOTE=aaronwh98]
I've been trying to get MIDI and Rosegarden to work on my box.  Jack will connect fine to ALSA but then I get no sound whatsoever until I disconnect Jack.  Then I get sound (but no MIDI of course).
[/QUOTE]

I never worked/tried MIDI within Linux and/or JACK - so I can't help you with this - sorry.
With which application did you try playing sound? Just an idea: It has to be an application which uses JACK as output - not ALSA. (As I wrote in the HOWTO, JACK blocks the ALSA sound device).

[QUOTE=aaronwh98]
I've tried everything on this site except I have the following problem when I try to start oss2jack:

!!!Scheduler set to Round Robin with priority 10 FAILED!!!
libfusd: /dev/fusd/control does not exist; ensure FUSD's kernel module is installed
Could not create sound device
: Package not installed

If I "modprobe kfusd", I get no errors so the package seems to be installed correctly.[/QUOTE]

I haven't seen the first error message yet.
But the rest is strange ... Did you check if the module is really loaded? ("lsmod | grep kfusd") And if that's the case, if the chararcter device /dev/fusd/control really exists ("ls /dev/fus* -l") ?

I think, that it has to do with the first error (first line). I'll try to look that up .... (in the sources)

---

### Post by aaronwh98 on 2006-02-02
Rosegarden (a compositional program) uses Jack (or jackd) as its output.  It is specifically designed to use jack.  That's what got me into this mess.  But now I have no sound whatsoever.  Kind of irritating. 

lsmod | grep kfusd produced:
kfusd                  26012  0
soundcore               9184  2 kfusd,snd

So it seems that it is loaded properly.  

Even if I can't get this to work, is there anyway to reverse what I've done (from your Howto) so that my system uses ALSA normally again?  I currently have no sound at all, midi or otherwise.

The device /dev/fus* does not exist.  Probably part of the problem, but I've no idea on how to fix that. 

Thanks for your help.

---

### Post by PLAY3ER on 2006-02-02
well OSS is working now, but can't login, only under fail safe? plz help

no it loged in but i gess it say under the input andout put its useing ESD

? not sure whats going on, everythinng happens to me :( i'll reply to your email and i don't have ICO sorry do you need me when your looking in my system because i can set it up and leave it on for you, i'll set it up tonight and email you my user name and pass. thank you ;)

---

### Post by PLAY3ER on 2006-02-02
heres what im doing 

```
ryan@ubuntu:~$ sudo apt-get install openssh-server)
bash: syntax error near unexpected token `)'
ryan@ubuntu:~$ sudo apt-get install openssh-server
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  rssh
The following NEW packages will be installed:
  openssh-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/195kB of archives.
After unpacking 524kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package openssh-server.
(Reading database ... 57689 files and directories currently installed.)
Unpacking openssh-server (from .../openssh-server_1%3a4.1p1-7ubuntu4_i386.deb) ...
Setting up openssh-server (4.1p1-7ubuntu4) ...
Creating SSH2 RSA key; this may take some time ...
Creating SSH2 DSA key; this may take some time ...
 * Restarting OpenBSD Secure Shell server...                             [ ok ]

ryan@ubuntu:~$ sudo bash
root@ubuntu:~# sudo apt-get update
Get:1 http://ca.archive.ubuntu.com breezy Release.gpg [189B]
Hit http://ca.archive.ubuntu.com breezy Release
Ign http://neogate.homelinux.org breezy Release.gpg
Hit http://ca.archive.ubuntu.com breezy/universe Packages
Hit http://ca.archive.ubuntu.com breezy/main Packages
Hit http://ca.archive.ubuntu.com breezy/restricted Packages
Ign http://neogate.homelinux.org breezy Release
Ign http://neogate.homelinux.org breezy/sound Packages
Get:2 http://neogate.homelinux.org breezy/sound Packages [1952B]
99% [2 Packages gzip 0]
gzip: stdin: not in gzip format
Err http://neogate.homelinux.org breezy/sound Packages
  Sub-process gzip returned an error code (1)
Fetched 2B in 1s (2B/s)
Failed to fetch http://neogate.homelinux.org/debian/dists/breezy/sound/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:~# sudo apt-get install jackd oss2jack
Reading package lists... Done
Building dependency tree... Done
jackd is already the newest version.
oss2jack is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:~# sudo apt-get install fusd-kor-source module-assistant
Reading package lists... Done
Building dependency tree... Done
fusd-kor-source is already the newest version.
module-assistant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:~# sudo apt-get install libesd0
Reading package lists... Done
Building dependency tree... Done
libesd0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:~# sudo cp /usr/share/doc/oss2jack/examples/oss2jack.modprobe /etc/modprobe.d/oss2jack
root@ubuntu:~# cp /usr/share/doc/oss2jack/examples/.gnomerc ~/.gnomerc
root@ubuntu:~# sudo modprobe kfusd
FATAL: Module kfusd not found.
root@ubuntu:~# clear

root@ubuntu:~# sudo apt-get update
Get:1 http://ca.archive.ubuntu.com breezy Release.gpg [189B]
Hit http://ca.archive.ubuntu.com breezy Release
Hit http://ca.archive.ubuntu.com breezy/universe Packages
Ign http://neogate.homelinux.org breezy Release.gpg
Hit http://ca.archive.ubuntu.com breezy/main Packages
Hit http://ca.archive.ubuntu.com breezy/restricted Packages
Ign http://neogate.homelinux.org breezy Release
Ign http://neogate.homelinux.org breezy/sound Packages
Get:2 http://neogate.homelinux.org breezy/sound Packages [1952B]
99% [2 Packages gzip 0]
gzip: stdin: not in gzip format
Err http://neogate.homelinux.org breezy/sound Packages
  Sub-process gzip returned an error code (1)
Fetched 2B in 0s (2B/s)
Failed to fetch http://neogate.homelinux.org/debian/dists/breezy/sound/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:~# sudo apt-get install jackd oss2jack
Reading package lists... Done
Building dependency tree... Done
jackd is already the newest version.
oss2jack is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:~# sudo apt-get install fusd-kor-source module-assistant
Reading package lists... Done
Building dependency tree... Done
fusd-kor-source is already the newest version.
module-assistant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:~# sudo m-a a-i fusd-kor
Reading package lists... Done
Building dependency tree... Done
fusd-kor-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Updated infos about 1 packages
root@ubuntu:~# sudo apt-get install realtime-lsm-source realtime-lsm module-assistant
Reading package lists... Done
Building dependency tree... Done
realtime-lsm-source is already the newest version.
realtime-lsm is already the newest version.
module-assistant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:~# sudo apt-get install libesd0
Reading package lists... Done
Building dependency tree... Done
libesd0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:~# sudo cp /usr/share/doc/oss2jack/examples/oss2jack.modprobe /etc/modprobe.d/oss2jack
root@ubuntu:~# cp /usr/share/doc/oss2jack/examples/.gnomerc ~/.gnomerc
root@ubuntu:~# sudo modprobe kfusd
FATAL: Module kfusd not found.
root@ubuntu:~#
```

---

### Post by PLAY3ER on 2006-02-02
box will be left on and untouched for friday,satday and sunday day and half night untill i get home about 9 or 10 but if you are working ion it and i can see, i'll leave it alone, thank you very much for everything you doing for me

---

### Post by joft on 2006-02-03
> **aaronwh98]
!!!Scheduler set to Round Robin with priority 10 FAILED!!!
libfusd: /dev/fusd/control does not exist said:**
> 

I had a look at the source code of oss2jack now and tested it myself: I can reproduce the **first** error above message, if I do not load the realtime kernel module (installed in HOWTO step 3). So, did you do step 3? Did you do a reboot? Because I just noticed that you have to manually load the realtime kernel module the **first time** (if you don't do a reboot after doing step 3).
I add that to the end of the HOWTO (step 11).

[QUOTE=aaronwh98]
Even if I can't get this to work, is there anyway to reverse what I've done (from your Howto) so that my system uses ALSA normally again?  I currently have no sound at all, midi or otherwise.


I added a section about reversing to the **end** of my HOWTO:
[http://www.ubuntuforums.org/showpost.php?p=695990&postcount=6](http://www.ubuntuforums.org/showpost.php?p=695990&postcount=6)
Scroll down and look for the END OF HOWTO marker.

[QUOTE=aaronwh98]
The device /dev/fus* does not exist.  Probably part of the problem, but I've no idea on how to fix that. 
[/QUOTE]

That's really strange ... what does "dmesg" say about it?

---

### Post by Cathbard on 2006-02-03
I won't interfere with the tech talk but I will offer a word of encouragement. I use Teamspeak on Ubuntu/Kubuntu (I run both Gnome and KDE on my Ubuntu) whilst playing Guild Wars and it is great.

Soldier on!!!!!

---

### Post by joft on 2006-02-04
[QUOTE=Cathbard]I won't interfere with the tech talk but I will offer a word of encouragement. I use Teamspeak on Ubuntu/Kubuntu (I run both Gnome and KDE on my Ubuntu) whilst playing Guild Wars and it is great.
[/QUOTE]

Without a special solution??

Then you are using artsdsp with artsd (KDE sound daemon), right?

Or do you have a sound card which is able of doing hardware mixing? (Which explains everything, I mentioned that at the beginning of my HOWTO.)

If both assumptions are wrong, then I am really interested **how** you do that?!

---

### Post by joft on 2006-02-04
Hi all,

I have just updated some packages in my repository and I updated the HOWTO, too. I tried to make especially step 2.C and step 3 more clear/complete. There were some things, which haven't been 100% correct - sorry - my mistake :( . So if you had problems with step 2.C or 3 and you are still interested, look at them now.
Also note, that step 5 is obsolete now. Just do nothing there.

[QUOTE=aaronwh98]
libfusd: /dev/fusd/control does not exist; ensure FUSD's kernel module is installed
Could not create sound device
: Package not installed

The device /dev/fus* does not exist. Probably part of the problem, but I've no idea on how to fix that. 
[/QUOTE]

I think I fixed this problem. @aaronwh98: If you are still interested, just install the package fusd-kor from my repository. It contains a configuration file for udev, which was missing before.
```
sudo apt-get install fusd-kor
```

---

### Post by PLAY3ER on 2006-02-04
k thanks i just seen it now but i need to do it all over again, do you use the Ubuntu IRC? because we can talk their because i think i what to reinstall alnd try all agin?

---

### Post by PLAY3ER on 2006-02-04
> [COLOR="Red"][B]=====================================================================
END OF HOWTO
=====================================================================[/B][/COLOR]

[INDENT][INDENT]If you don't like the result of this HOWTO or if you have to reverse the whole thing because of some other reason, here's a **list**, what you have to do to **switch back to ALSA/dmix**. I used the same step numbers as in my HOWTO:

**9.** Remove ~/.gnomerc

```
rm ~/.gnomerc
```

**8.** Go to

System -> Preferences -> Multimedia Systems Selector

and select ALSA (for both input and output).

**6.** Remove /etc/modprobe.d/oss2jack

```
sudo rm /etc/modprobe.d/oss2jack
```

**5.** Remove the line "kfusd" from your /etc/modules file, **only if** you have added one before (see step 5 above in the HOWTO).

**4.** Replace the package "libesd0" with "libesd-alsa0", by doing:

```
sudo apt-get install libesd-alsa0
```

[SIZE="1"][I]Now, if you like you could further uninstall the rest of the software packages, but you don't have to. E.g.:
```
sudo apt-get remove oss2jack fusd-kor* jackd realtime-lsm* 
```[/I][/SIZE]
[/INDENT][/INDENT]



thanks i was wonding if i could reverse it, now i just redid it now i'll try again nothing failed WOOT!

---

### Post by PLAY3ER on 2006-02-04
[QUOTE=PLAY3ER]when i do  System -> Preferences -> Multimedia Systems Selector and go OSS for both i hit Test and it gives me an error 

Failed to construct test pipeline for 'OSS -Open Sound System'[/QUOTE]
 

got that again but this time it did hang, but it was working beccaue the busy light was on on the computer,:S i'll get my IP and send it to ya and leave the compter on

---

### Post by PLAY3ER on 2006-02-05
im going to try this in KUbuntu

---

### Post by joft on 2006-02-06
Hi,

@PLAY3ER: If you try my HOWTO with Kubuntu you have to consider that KDE runs artsd instead of esd. So you have to reconfigure artsd to use the emulated OSS device instead of ALSA. Furthermore you have to find out where to put the commands starting jackd and oss2jack, in a way that they get started after login but before KDE starts artsd.

I recommend using artsdsp (wrapper for non-artsd-apps) under KDE/artsd. Note: I didn't test the whole jackd/oss2jack with KDE!

But anyway, why did you change your mind? I thought is was working now (except the gstreamer thing, which is not that essential)?!

---

### Post by PLAY3ER on 2006-02-06
its was not working..i got an error when i tryed to test it.

PS: i wasn't sure if it would or wouldn't work with KDE so i wanted to try

---

### Post by PLAY3ER on 2006-02-07
oss2jack:
 Depends: libjack0.80.0-0 (>=0.99.0) but it is not installable
 Depends: libsamplerate0  but it is not installable

---

### Post by joft on 2006-02-08
[QUOTE=PLAY3ER]oss2jack:
 Depends: libjack0.80.0-0 (>=0.99.0) but it is not installable
 Depends: libsamplerate0  but it is not installable[/QUOTE]

Hmmm, strange thing. These packages are both in breezy's main repository and I don't know why apt would say they aren't installable.

Did you try to install these packages manually? ==>:

```
sudo apt-get install libjack0.80.0-0 libsamplerate0
```

Perhaps it helps. Then try step 2.A again. Did apt-get throw any other messages while doing step 2.A?

---

### Post by PLAY3ER on 2006-02-08
```
sudo apt-get install libjack0.80.0-0 libsamplerate0
```

i did in the window one but i didn't know the command in the term do to it thx

---

### Post by PLAY3ER on 2006-02-08
```
root@ubuntu:~# sudo apt-get install libjack0.80.0-0 libsamplerate0
Reading package lists... Done
Building dependency tree... Done
Package libjack0.80.0-0 is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libjack0.80.0-0 has no installation candidate

```

---

### Post by Cathbard on 2006-02-09
Yes, I use a Soundblaster Audigy which makes it somewhat easier. However having said that, I think something has changed because I also seem to have lost /dev/dsp too. I was screwing around trying to compile a kernel so I blamed that but I'm noticing people getting that problem anyway. (I'm upgrading it to dapper so I don't really care much.)
As a workaround in the meantime I created a symbolic link to /dev/dsp1 called dsp and TS started working again. I know this won't help ur situation but that's my story.

---

### Post by joft on 2006-02-09
[QUOTE=PLAY3ER]```
root@ubuntu:~# sudo apt-get install libjack0.80.0-0 libsamplerate0
Reading package lists... Done
Building dependency tree... Done
Package libjack0.80.0-0 is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libjack0.80.0-0 has no installation candidate

```[/QUOTE]

Again, that's really strange. I just checked this package's existence again. It's in **Ubuntu Breezy**, "**main**" repository.
What does
```
apt-cache show libjack0.80.0-0
```
say?

Maybe your /etc/apt/sources.list is a bit .... "damaged" .... Or the mirror you are using is bad .... Perhaps a

```
sudo apt-get update
```

helps?

Another "manual" possibility would be to download the package from ubuntu's website "manually":
[http://packages.ubuntu.com/breezy/libs/libjack0.80.0-0](http://packages.ubuntu.com/breezy/libs/libjack0.80.0-0)
Scroll down the page to "Download" and chose "i386" **OR** use this direct link:
[http://archive.ubuntu.com/ubuntu/pool/main/j/jack-audio-connection-kit/libjack0.80.0-0_0.99.0-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/j/jack-audio-connection-kit/libjack0.80.0-0_0.99.0-2ubuntu1_i386.deb)

And then do (**after** changing into the directory you downloaded the file to):

```
sudo dpkg -i libjack0.80.0-0_0.99.0-2ubuntu1_i386.deb
```

Then - if there are dependency errors - you have to install these packages it complains about via apt-get (=> "sudo apt-get install <package>").

---

### Post by PLAY3ER on 2006-02-09
```
ryan@ubuntu:~$ apt-cache show libjack0.80.0-0
ryan@ubuntu:~$ sudo bash
Password:
root@ubuntu:~# apt-cache show libjack0.80.0-0
root@ubuntu:~#

```

```
root@ubuntu:~# sudo apt-get update
Ign http://neogate.homelinux.org breezy Release.gpg
Ign http://neogate.homelinux.org breezy Release
Hit http://neogate.homelinux.org breezy/sound Packages
Reading package lists... Done
root@ubuntu:~#

```

you have 1 broken packge on your system!

use the "Broken" filter to locate it. ("Broken" filter?)

---

### Post by joft on 2006-02-10
[QUOTE=PLAY3ER]```
ryan@ubuntu:~$ apt-cache show libjack0.80.0-0
ryan@ubuntu:~$ sudo bash
Password:
root@ubuntu:~# apt-cache show libjack0.80.0-0
root@ubuntu:~#

```

```
root@ubuntu:~# sudo apt-get update
Ign http://neogate.homelinux.org breezy Release.gpg
Ign http://neogate.homelinux.org breezy Release
Hit http://neogate.homelinux.org breezy/sound Packages
Reading package lists... Done
root@ubuntu:~#

```

you have 1 broken packge on your system!

use the "Broken" filter to locate it. ("Broken" filter?)[/QUOTE]

Besides the message about a broken package, I think you have got a problem with your /etc/apt/sources.list file. The output that comes from your above show "sudo apt-get update" are a bit short. There should be more lines than that. Especially there should be lines which tells you that apt-get is downloading from an official ubuntu archive - like I said in my last post already: Check your /etc/apt/sources.list file.
To give you an example of what it should look like:

```
deb http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted universe
deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe

deb http://neogate.homelinux.org/pub/debian breezy sound

```

---

### Post by PLAY3ER on 2006-02-10
k i'll look at it tonight

---

### Post by PLAY3ER on 2006-02-12
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://ca.archive.ubuntu.com/ubuntu breezy main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://ca.archive.ubuntu.com/ubuntu breezy-updates main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ca.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://ca.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
  deb http://neogate.homelinux.org/debian/ breezy sound
# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```


PS:W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by joft on 2006-02-12
@PLAY3ER: Ok, I think we have a major misunderstanding here. I'll try to explain it: Look at your sources.list file's contents you posted. The "'#" characters at the begining of most of the lines say, that the line is a comment. That means, it's not interpreted by apt-get - it just ignores these lines. So, as you can see now, all about apt-get cares in your sources.list are the very first line and down at the end the line pointing to my repository. The first line says, that apt-get should look at the Ubuntu CDROM (as long as you insert it).

But due to the fact that you have got DSL perhaps it's easier to point apt-get to the repositories on ubuntu's webservers - instead of to your Ubuntu CDROM. So you can disable the first line, by adding a "#" character infront of it and enabling the other lines starting with "# deb ..." by removing the "#" character.
There are several other lines - as you can see - each one points an other repository and the ubuntu developers even described them using comments (above the "deb"-lines)- READ them, then you know what the repository is good for.

In my last post a already suggested a couple of "deb"-lines. You are free to take them and put them at the end of your existing sources.list. Leave out the last line I suggested, because you already have that (look at your file)!

IMPORTANT (also mentioned in the HOWTO): [B]After changing /etc/apt/sources.list, you have to do:

```
sudo apt-get update
```[/B]

Again - I already said that indirectly - the output, what you are going to see after executing the above command, usually shows you the repositories apt-get is working on (fetching the list of Packages in the repository).

The error messages you attached to your last post, AFAIK say that you commented some lines of your sources.list and then never did an "sudo apt-get update".

After doing that, try to install oss2jack again.

---

### Post by PLAY3ER on 2006-02-13
sorry for the misunderstanding , i'll do that right now

---

### Post by PLAY3ER on 2006-02-13
could it be 10?

Linux Kernel

User interaction required! A new version of the Linux kernel has just been installed. We strongly  recommend that your machine is restarted as soon as possible to complete the system update.

---

### Post by AtZeuS on 2006-04-26
The installation went ok, but when I use the .gnomerc the system hangs after i've typed in my username and password in the login screen. When I run failsafe gnome it runs ok, but I have no jack :( Any ideas?

---

### Post by joft on 2006-05-02
First - a big sorry, for my late answer ...

[QUOTE=AtZeuS]The installation went ok, but when I use the .gnomerc the system hangs after i've typed in my username and password in the login screen. When I run failsafe gnome it runs ok, but I have no jack :( Any ideas?[/QUOTE]

Hmmm, well something the script does seems to go wrong. Did you setup GNOME to start esd (Preferences -> Sound -> Enable sound server)?
If this is not the case: You have to enable esd, because my (silly) .gnomerc script depends on a running esd. Without an esd, jackd and oss2jack never will get started. BUT: this shouldn't be a reason for system hanging.

I suggest to rename the script (to something other than .gnomerc), then login and try to execute the script by hand:

```
. <script-file-name>
```

But I doubt that this will bring up any clues, since the whole output of the started programs inside the script is piped away (/dev/null). So it's better to try to start the 2 programs by hand and see what they say:

```
nice -n -1 jackd -R -d alsa -p 256
```

Then, in another console:

```
nice -n -1 oss2jack
```

Now, is there any strange output from the two programs? Error messages? Failures? jackd gives some output at the beginning, oss2jack shouldn't say anything right after it's started.
NOTE: Both programs SHOULD block the console (no daemon mode in this case), if one is returning, something IS wrong.

---

