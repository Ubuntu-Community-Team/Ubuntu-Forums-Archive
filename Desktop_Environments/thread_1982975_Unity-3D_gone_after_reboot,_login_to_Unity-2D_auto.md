---
title: "Unity-3D gone after reboot, login to Unity-2D automatically"
date: 2012-05-19
forum: Desktop Environments
---

### Post by Gufran on 2012-05-19
I just had a system reboot and Unity-2D popped up before my face, I am sure I didn't messed with Unity, compiz or X server's settings hijust installed a plymouth theme and removed it after the reboot. I also tried updating grub and initramfs but no luck. I cant seem to log into unity-3D again, even after selecting it from unity greeter screen it always load into 2D mode.
Unity support test show that Unity 3D is not supported on my system, but I know it was just before the reboot I was into 3D mode
here is the output of /usr/lib/nux/unity_support_test -p

```
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```

Also when I try to kill unity-2d applet or panel it doesnt close down, I tried starting unity from a terminal and 3D mode started overlapping the 2D mode. All the tweaks I made to 3D mode were still there but It was all messed up because 3D mode was overlapping with 2D mode.

I tried googe for a solution but none of them seem to fix my problem, can anybody kick me in right direction please ?
I really find it damn frustrating working with 2D mode.

---

### Post by Gufran on 2012-05-20
60+ views and no solution so far, somebody please help me out I am struggling bad to fix it.

---

### Post by tusharmakkar08 on 2013-01-07
I also have the same problem ..
Please help..

---

### Post by mreq on 2013-01-07
Happened to me when uninstalled bumblebee. Have you tried running unity from terminal and see the errors?

---

### Post by foberle on 2013-01-31
I'm well into my six month experience with Ubuntu 12.04 LTS (now updated to 12.04.1) so have learned not to expect much from this forum, but even though this thread seems to have never been resolved, I sure hope someone can point me in the right direction.

I too experienced this 2D-only syndrome with my desktop, although with not quite the same symptoms: I did a reboot yesterday and logged in as usual. When Unity appeared, I had super large icons, attempted to reset the size, and was warned I was in 2-D mode and was out of luck. Very annoying.

So, I logged out and attempted to select Ubuntu 3D, which WAS STILL LISTED. But no, it dropped down immediately to 2D. I do now have the various Gnome entries on the log in choices; I can't say they weren't there before, but I can say I never noticed them.

Then I thought perhaps my graphics card/chip or whatever had died. I tried booting from the install disk (same one I originally used), and still was only able to use 2D. I went into the BIOS and checked to see if all was well, and it appeared to be.

Then I thought I should run the /usr/lib/nux/unity-support-test -p command that Gufran mentioned in his earlier post. The output I received was:

```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22

```

I'm really not interested in reinstalling Ubuntu, and have enough experience with computers to know that doing an upgrade (e.g. to 12.10) while the current installation is fried isn't a good idea. I have backups, of course, but I don't want to do a blanket restore if there is some way to perhaps reinstall Unity (I assume that's a deb package or group of packages).

Other outputs that might be of interest, although I don't know how to interpret them are:
```

$> lspci | grep VGA

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780L [Radeon HD 3000]

$ sudo lshw -c video
[sudo] password for foberle: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RS780L [Radeon HD 3000]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff ioport:ee00(size=256) memory:fdff0000-fdffffff memory:fde00000-fdefffff

```

Does anyone know what is going on or how to remedy this? 

Thanks much ...

---

### Post by stinkeye on 2013-01-31
> Then I thought I should run the /usr/lib/nux/unity-support-test -p command that Gufran mentioned in his earlier post. The output I received was:
You may have just copied to your post incorrectly but the command is
```
/usr/lib/nux/unity_support_test -p
```

What gfx driver is in use?
```
lspci -nnk | grep -iA2 vga
```
eg
> [COLOR="DarkGreen"]glen@Quantal:~$ [/COLOR]lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] [10de:1244] (rev a1)
	Subsystem: Giga-byte Technology Device [1458:351a]
	**Kernel driver in use: nouveau**


Not up with amd driver issues but an amd gfx user should be able to help you out.

---

### Post by foberle on 2013-02-01
Thanks much for the response. I did indeed use dashes instead of underscores in the unity support test although, strangely enough, got exactly the same response:

```
$ /usr/lib/nux/unity_support_test -p
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22

```

The second command gives:

```
$ lspci -nnk | grep -iA2 vga
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS780L [Radeon HD 3000] [1002:9616]
    Subsystem: Giga-byte Technology Device [1458:d000]
    Kernel modules: radeon
```

Does this prompt any thoughts? Again, thanks.

---

### Post by foberle on 2013-02-01
One other thing I quickly discovered: All of my Compiz "Fixed Window Placements" have disappeared, meaning everything I run opens up at the top left of the screen (very annoying). Could I have trashed Compiz somehow?

---

### Post by foberle on 2013-02-03
And yet another discovery: I had four things running this morning and decided to click on the "Workspaces" icon so I could move the apps to different workspaces. Workspaces showed up, but I'm no longer able to drag an app to another workspace.
I had to break down and boot into Windows again (which I haven't done for a while) and nothing seems amiss on that side, so I'm guessing this isn't related to a hardware issue.
Whatever Ubuntu "upgrade" was done (it still says 12.04.1) sure doesn't seem very helpful.
Does anyone have any idea at all what I should be looking at [other than a Mac :) of course]???

---

### Post by foberle on 2013-02-05
A further result (I presume from the same thing that caused the other symptoms in my last couple posts) is that I can no longer move any of the icons on the Launcher. What happens is that any mouse motion (with the button held down) causes the entire Launcher to move up or down.

Reading some pop magazines indicated that Canonical decided to remove Unity-3D support from 12.10. I still show 3D as an option on the login screen, but it just doesn't work. Is it possible that I've somehow gotten "part of an upgrade" (which I didn't intend - I want to stick with 12.04 LTS). If so, are there packages I can remove? Does anyone know anything about this stuff?

---

### Post by stinkeye on 2013-02-05
You are being dropped back to the 2d session because you can't run the Ubuntu (3d compiz) session because of a driver issue.

What session are you in?
Terminal...
```
echo $DESKTOP_SESSION
```
**Ubuntu** session runs compiz.
**Ubuntu 2d** session runs metacity.

In the Ubuntu 2d session compiz is not the window manager
therefore you don't have your previous compiz settings.

In 12.10 Canonical has dropped the **2d** session.

---

### Post by karolosz on 2013-02-05
hello i've got the same, i up-date system, when i started i so it change deeply i was confused.
i coudn't run cairo-dock
my launcher looked weird
when i ran myunity told me that i am ran 2d unity

i went to driver & i installed for my graphic card ATI driver, reboot and my unity 3d back.

---

### Post by foberle on 2013-02-11
Sorry I missed these last two posts for some reason.
For Stinkeye: I am definitely running Ubuntu 2D per the command you gave.
For Karolosz: I too have ATI Graphics. Can you point me toward something that tells me how to reload the correct driver?
Thanks much.

---

