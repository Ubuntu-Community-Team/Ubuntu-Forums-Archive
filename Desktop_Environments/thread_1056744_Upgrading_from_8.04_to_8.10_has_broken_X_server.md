---
title: "Upgrading from 8.04 to 8.10 has broken X server"
date: 2009-02-01
forum: Desktop Environments
---

### Post by gobstopper on 2009-02-01
As a sometimes 'dabbler' with Linux I have a old PC which I have used to run Ubuntu for a few years. The basic make-up of the machine is:-
[list]
AMD Duron 1.3Ghz
1.5Gb RAM
80Gb IDE drive
NVidia Geforce FX5500 graphics card with 256Mb RAM
Hanns.G HW191D 19" monitor
[/list]

As well has an old Win2000 partition, it has run some variant of Ubuntu since 6.06. I have upgraded it through the various versions have have never experienced a problem with the process. However, yesterday I decided that it was time to upgrade from 7.04 to 7.10 and have been left with a bit of a mess.

After realising that the 7.10 upgrade option wasn't available by default, I found out how to change the appropriate settings and set about performing the upgrade. The upgrade itself seemed to go very smoothly. However when completed, I was prompted to restart the machine and during the boot process, I was suddendly presented with the following:-

> 
Decompressing Linux - Done
Booting Kernel

Failed to start X server


this was quickly followed by a much longer message containing:-

> 
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Release 0
Build Operating System: Linux 2.5.24-19-server i686 ubuntu
Current Operating System: Linux <machine-name> 2.6.25-2-386 #1 Tue Sep 30 14:47:35 UTC 2008 i686
Build Date: 24, October 2008 08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
.
.
. (some other lines which I stopped writing down, because they didn't seem that relevant compared to what followed)
.
.
(EE) Failed to load module "type1" (module does not exist, 0)
FATAL: Module nvidia not found
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found, but none have usable configuration

Fatal server error
no screens found


At which point if I select OK, I am presented with an option to view an even more verbose set of messages and then I am dumped back to a command line login prompt.

Is this fixable? :icon_frown:

---

### Post by gobstopper on 2009-02-01
Whoops, just noticed an error in my description. I was, of course, trying to upgrade from 8.04 to 8.10 (as per title) not 7.04 to 7.10.

Sorry for misleading. Hopefully someone has some ideas?

---

### Post by gjoellee on 2009-02-01
this is your errors:
> (EE) Failed to load module "type1" (module does not exist, 0)
FATAL: Module nvidia not found
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!A module called "type1" failed to load. Now unless you have a special configuration you don't need that module so lets disable it. The second error says that the nvidia module does not exist. Make sure you have a nvidia driver installed, then lets move on to the steps below.

1. Get to a shell, but starting up in recovery mode and then select "go to root shell" or something like that appears in a menu.

2. Use this command:
```
sudo nano /etc/X11/xorg.conf
```NOTE: /X11/ is with capital "X".

3. A whole lot of text should appear. You can navigate through the text with your arrows. Find the "module section". It starts like this: 
```
Section "Module"
```and under that find this line:
```
Load "Type1"
```you can disable it by adding a "#" in front, so it looks like this:
```
# Load "Type1"
```if you feel that is unsafe just remove the the line.

4. Find the device section, it starts like this:
```
Section "Device"
```find the "Driver" line in the device section, and make it look like this:
```
Driver      "nvidia"
```5. Save and exit by first pressing CTRL + X and then press Y for Yes

6. Reboot

EDIT: You should try to run an Xfix, se how here: [http://www.kshoster.net/content/howto-run-xfix](http://www.kshoster.net/content/howto-run-xfix) or try what I wrote above

---

### Post by gobstopper on 2009-02-01
Thank you for your response.

I have tried your suggestion, editing the config file mentioned.

Placing a # in front of the "type1" module line has removed this error, but alas replaced it with a new one.

X still fails, but this time it claims that it is unable to find "nvidia".

Might give your plan B a try if I can understand the instructions.

---

### Post by Seymore on 2009-02-01
Replace the "nvidia" refernce with a "nv" reference. This will probably make the X server work, but without any 3D capabilities.

I'm having some of the same problems, I can get the X server starting but the kdm will not.

---

### Post by gobstopper on 2009-02-01
Ah! It seems that booting into recovery mode and running xfix (which actually appeared as an option in a pre-poulated menu, which made it a doddle to find!) has done the trick - I am sending this response from my Ubuntu machine. I appear to have lost the wobbly windows and other groovy features, but they are secondary to being able to see Gnome in the first place. So thanks for the advice!

On an unrelated subject (and forgive my rather basic Linux vocabulary) one thing I have never been able to see on this PC is what I call the 'boot messages (or progress). From the point I see "Booting Kernel" on the screen, the screen itself goes blank and displays the message "Input Signal out of range" until the point I am presented with the graphical logon prompt. I don't know why, especially as (when working) I am able to run the Gnome envrionment at exactly the resolution my monitor supports (1440x900).

Other than that, the only other thing 8.10 has introduced me to is silence. It doesn't appear to have detected the sound card on my Asrock K7VT2 motherboard.

---

