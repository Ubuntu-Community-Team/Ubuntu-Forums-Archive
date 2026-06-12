---
title: "Cinnamon installation problem - no panels"
date: 2013-03-30
forum: Desktop Environments
---

### Post by daviestar on 2013-03-30
Hi folks,

I am really pulling my hair out trying to get Cinnamon up and running in my Ubuntu 12.10 set up.  When I log into Cinnamon I get a blank desktop - wallpaper from Unity I think - and no panel or icons, can't click or right click, think I hear 3 error beeps.  I can only reboot, and go back into Unity.  I have tried uninstalling/re-installing.  I found [this]("http://ubuntuforums.org/showthread.php?t=1941288") post on here, and [another]("http://askubuntu.com/questions/235198/cinnamon-failed-desktop-only-no-panel-no-dialog-frame") which sound like my problem, but apparently has been solved (or no answer).

I installed with these lines:
```

sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon

```

I am extremely (6 days or so!) new to linux and ubuntu, so I could be making a n00b mistake, if anyone could suggest any ideas???

I am running Ubuntu 12.10 Desktop in VMWare Player with 3D acceleration, on Windows7 64-bit on Toshiba z830-10u.

I read somewhere that Nema may not play nice with Nautilus.

---

### Post by ManamiVixen on 2013-03-30
If your pc produced error beeps, there is a problem with your hardware. Might need to check it out.

---

### Post by daviestar on 2013-03-30
I don't mean mainboard beeps, I mean OS 'error sounds'.. if that makes a difference?

---

### Post by ManamiVixen on 2013-03-30
Odd, I never heard of Cinnamon making error sounds.

Ok, lets try this. Login to Cinnamon and after eveything loaded, and the beeps, push "ctrl+alt+t" to bring up terminal and type an run "cinnamon --replace". Copy and paste here what the output is. To bring up firefox, on the Terminal click file<new tab and type firefox in and run it.

---

### Post by daviestar on 2013-03-30
> **ManamiVixen said:**
> Odd, I never heard of Cinnamon making error sounds.

Yeah, I'm pretty sure I'm not even logging into Cinnamon, I think it's still Unity.  In Unity, I put a folder on the desktop and tried logging into Cinnamon again.  The folder was there with the same orange styling as Unity.  However I can't click on it or do anything with it.

> **ManamiVixen said:**
> Ok, lets try this. Login to Cinnamon and after eveything loaded, and the beeps, push "ctrl+alt+t" to bring up terminal and type an run "cinnamon --replace". Copy and paste here what the output is. To bring up firefox, on the Terminal click file<new tab and type firefox in and run it.

The command didn't work.  Cinnamon doesn't seem to accept any input and I need to reset my virtual client.

---

### Post by ManamiVixen on 2013-03-30
So wait? Is this on a virtual machine? I'm a doofus for missing that second to last sentence.

Now as to why Cinnamon is crashing, it has to do with the fact VMWare dosen't do a good job at OpenGL acceleration and most Linux desktops with GL will crash. Cinnamon is no exception, but Unity is. When Unity sees no hardware that is available for 3D OpenGL Acceleration, it will enable LLVMPipe, which is a virtual GPU and in turn creates an OpenGL enabled GPU as a process in the CPU. So Unity will run, but very slowly.  

Anyways, Unity, Cinnamon, all desktops in fact use the same desktop folder for displaying desktop items. So the folder made in Unity would in fact show on Cinnamon's desktop if put in the Desktop folder. And since both Unity and Cinnamon use Gnome as a base, they will also show the same wallpaper. So it likely is Cinnamon.

---

### Post by daviestar on 2013-03-30
Ok thanks.  So would you recommend something else like VirtualBox?? I only just got my LAMP installation up and running too... :(

---

### Post by daviestar on 2013-03-30
To help anyone else with this issue, I have some more info after some digging.

Latest versions of VMware Player DO support openGL, and [very well]("http://www.phoronix.com/scan.php?page=article&item=vmware_virtualbox_osx&num=1") from what I can tell (please correct me if I'm wrong).

Using the commands:
sudo apt-get install mesa-utils
glxinfo |egrep 'OpenGL|vendor|rendering'

You can check if LLVMPipe is indeed handling GPU processes.  Return for me was:

direct rendering: Yes
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on SVGA3D; build: RELEASE;  
OpenGL version string: 2.1 Mesa 9.0.2
OpenGL shading language version string: 1.20

The 'SVGA3D' part is the VMWare openGL plugin. If this says LLVMPipe, then it's correct that Cinnamon will not run (for now).

I'm hoping this very recent bug to do with a Ubuntu update [is the culprit]("https://github.com/linuxmint/Cinnamon/issues/1763"). There's a rant in the comments by LinuxStrikesAgain which will make you smile :)

---

