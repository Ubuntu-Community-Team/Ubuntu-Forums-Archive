---
title: "Hibernate and Suspend issues on Vostro 1500"
date: 2008-06-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by KingJ on 2008-06-05
Hi,

I set up a Wubi install on my laptop a few days ago, it's been working perfectly. Anyway, I read that you can't Hibernate or Suspend and I confirmed this myself, it didn't work. So, following the instructions found [here](http://lubi.sourceforge.net/lvpm.html) I migrated my Wubi install to a proper partition then removed the old Wubi install. This has gone fine, it's now working without Wubi and I can still dual-boot with Vista (which i've left for any emergency situations, should Ubuntu mess up!).

Now, here is where the problem is, I still cannot Hibernate or Suspend. Hibernation fades to black, displays the flashing cursor and then just maintains a black screen indefinitely, I have to hard reboot it. Suspect turns off, but when you resume, it just displays a white background with the mouse cursor, which works but there is nothing I can do with just a mouse cursor, no menus, no hotkeys work etc.

I asked on the IRC channel and got given a few URLs for assistance. They included, [this one](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=523356), [this one](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/130457) and [this one](https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1500#head-eafd0abde464d1f206cc6c7c7ad75fcd5d7d3637). However, even after applying all fixes suggested, it still produces the same result.

Does anyone have any further ideas? It would be excellent to have suspend/hibernate functionality since I use this laptop many times a day and is the only thing stopping me from using Ubuntu full time, everything else functions fine.

Edit: It has the nVidia 8600GT Graphics, and i've got the latest drivers. Desktop settings are set on Extra.

---

### Post by KingJ on 2008-06-07
Bump, any advice appreciated.

---

### Post by elmu.edana on 2008-06-07
Hi, 

regarding suspend: Most of the times after resume I also see a white screen with the mouse pointer. When moving the mouse pointer over the screen I can find an area where the pointer changes into the shape of a text cursor, so I can know that there is a text field even if it is invisible. I can enter my password into this invisible field. After pressing enter, my desktop appears. Unfortunately the white screen doesn't appear always after resume, sometimes there is a black screen. For these cases I didn't find a solution so far.

Regarding hibernation: So far this worked for me, but it takes a long time to hibernate as well as to resume.

I run Ubuntu 8.04 on a Vostro 1700 with a GeForce 8600M GT. I use the restricted driver and compiz.

---

### Post by KingJ on 2008-06-08
> **elmu.edana said:**
> Most of the times after resume I also see a white screen with the mouse pointer. When moving the mouse pointer over the screen I can find an area where the pointer changes into the shape of a text cursor, so I can know that there is a text field even if it is invisible. I can enter my password into this invisible field. After pressing enter, my desktop appears. Unfortunately the white screen doesn't appear always after resume, sometimes there is a black screen. For these cases I didn't find a solution so far.

Just tried this and works for me too, thanks for finding this out :) . It would still be nice to be able to hibernate though.

---

### Post by KingJ on 2008-06-10
I just installed some of the backports updates, and now when resuming I get a login screen, as opposed to a white screen and having to find the box. So, at least that's suspend fully working.

---

### Post by James.Dedon on 2008-06-10
Have you tried to remove the fglrx drivers and use the open source video drivers?  That solved all of my suspend problems, albeit different problems....  However, you'll probably lose the compiz flashyness.

---

### Post by KingJ on 2008-06-10
> **James.Dedon said:**
> Have you tried to remove the fglrx drivers and use the open source video drivers?  That solved all of my suspend problems, albeit different problems....  However, you'll probably lose the compiz flashyness.

Unfortunately, I need the graphics drivers since I do play a lot of games. Hibernate would be nice, but if I can only have suspend I can live with that.

---

### Post by lightrush on 2008-06-10
KingJ, I think I am onto something for fixing suspend on NVIDIA/Intel combo Vostro and since u have trouble as well u can help me and I can help u. Since I am not totally sure because I am still testing I want u to test the following:

1. Make sure u run the "nvidia" driver  - not "nv".
2. Revert all modifications on files u did from previous attempts - e.g. /etc/default/acpi-support, /boot/grub/menu.lst, /etc/X11/xorg.conf
3. Now do ONLY the following mods:

Edit ur acpi-support
```

sudo gedit /etc/default/acpi-support

```

Make these options look like mine:
```

SAVE_VBE_STATE=false
POST_VIDEO=false
SAVE_VIDEO_PCI_STATE=true
USE_DPMS=false

```
---

Now blacklist intel_agp
```

sudo gedit /etc/modprobe.d/blacklist

```

At the end add
```

#blacklisting Intel's agpgart
blacklist intel_agp

```
---

And edit ur xorg.conf
```

sudo gedit /etc/X11/xorg.conf

```

In "Device" section add this:
Notice it is 0 - not 1
```

Option   "NvAGP"   "0"

```
---

And according to my testing the real magic hides here.
Go here:
```

cd /etc/acpi/suspend.d/

```

Rename (deactivate) this script:
```

sudo mv 80-video-vesa-state.sh inactive.80-video-vesa-state.sh

```

Finally remove the executable flag from this nastiness:
```

sudo chmod -x inactive.80-video-vesa-state.sh

```
---

4. After these steps are complete - reboot ur machine and start torturing it with Suspend/Resume. U can try first several fast suspend/resumes then leave it for longer periods off and on between suspends/resumes. In my exp when it hangs - it hangs when intervals between suspend/resume are longer but not necessarily. Most importantly - do not restart it - just Suspend/Resume.

5. If any of the above commands does give out an error - probably I have a typo but I think u can cope with it - thats why I explain what I do before each code line.



Please give results in this thread - I will be monitoring hourly :). :popcorn:

---

### Post by KingJ on 2008-06-10
Okay lightrush, I gave your fixes a go. Rebooted and started fine, so that's good at least.

Suspend worked, but on resume I had the white screen, but was able to find the password box by moving the cursor until I got the I text editing mouse cursor.

Hibernate failed in the same place, screen goes to black, a bit of disk activity and then nothing, computer remains on and hard reboot required.

Looks like it changed nothing :(

---

### Post by lightrush on 2008-06-10
Jesus this ACPI thing is different everywhere ... Well my config is Vostro 1400 with 8400M GS and it seems to behave differently than 8600GT. My suspend has always worked but inconsistently - e.g. it would hand suspending after 3-4 suspend or sometimes further - 10th. Sometimes it would not power my screen on resume. After reading most of the stuff on the topic with simple tweaking of acpi-support resume always powered my screen but the handing on suspend didnt go no matter what. Then I started ripping off VBE by first removing the script which executes it on suspend and everything worked magically. No more hangs. I have just installed Vanilla 8.04 and will try only this mod + the tweaks of acpi-support. 

I havent seen this problem with the missing box but I am almost sure u can get rid of it by turning off screen locking on resume from GNOME. 

Another guy on #phoronix had the same config as u (almost) same graphics and his machine suspends out of the box - no changes needed, so u should be able as well.

Again if this white screen was the only problem u had with Suspend - remove the screen lock and try again. And if suspend works for u consistently - forget about Hibernate - it is painfully slow. Almost as slow as rebooting.

---

