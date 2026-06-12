---
title: "fglrx + new login/user switch = system lockup!!!"
date: 2005-12-20
forum: Desktop Environments
---

### Post by amohanty on 2005-12-20
Hi All,

I am running 32 bit breezy on an amd64 3200+ on a Radeon X300SE. Recently I decided to install the default xorg-driver-fglrx driver, per the [howto]("http://ubuntuforums.org/showthread.php?p=408111"), which went smoothly. My frame rate bumped from about 600 on the ati drivers to about 2000, which was great. However I have run into this problem since then:

1. Login as user1 on display :0
2. Use the New Login panel applet to login as user2 on display :20 (default - I dont specify it)
3. Use the New Login panel applet to switch back to user1 on display :0

The screen then goes crazy with a whole bunch of multi-coloured junk in it. I perused the /var/log/Xorg.0.log file, the /var/log/Xorg.20.log and the corresponding .old files after a manual hard reboot and other than repeated consecutive appearance of :

> drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card17
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card18
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed


in Xorg.0.log file, I did not see anything wrong. A quick google search seems to indicate dri lib related trouble, but no mention of what exactly causes it or how to fix it. 

I also installed linux-restricted-modules-2.6.12-10-386 as part of the install process. Could this be the root cause of the problem? 

Would removing the dri module fix it? 
If so, I am assuming my frame rate would go down since direct rendering would not be possible without dri, am I correct in assuming that?

I have not tried using the driver without the restricted modules. Per my understanding it will not work without it. Is that correct?

Any help would be greatly appreciated.

Thanks.

---

### Post by Ocxic on 2005-12-20
try installing the 64-bit kernel from synaptic
removing the DRI module may help, i think it is used to communicate with your monitor for specs and stuff.

---

### Post by amohanty on 2005-12-20
The reason I use the 32 bit version is because I encountered several media related problems with the 64 bit version. Will check it out when I get home.

Thanks.
AM

---

### Post by amohanty on 2005-12-21
Unfortunately it didnt work. Any other way to fix this?

Thanks.
AM

---

### Post by ysse on 2006-01-02
Sounds a bit like what I'm experencing on a CL56 laptop, with a 2.0 GHz Pentium M, kernel 2.6.12-10-686, and a Radeon 9700.

The login screen for the new session is all scrambled, but typing works. In fact, I can log in, and a new session starts, but the screen is a mess. Ctrl-Alt-F7 brings back the original session, which looks all right, but switching back to the new one with Ctrl-Alt-F8 gives the same scrambled screen as before.

I even wrote down the keystrokes to access the Screen Resolution applet, and tried to switch resolution in the new session. It did change to something else, but still equally unreadable. Somehow it looks like the second session uses the wrong frequency. But the only choice I have in the Screen Resolution dialog is 60 Hz.

Before installing the ATI driver, switching sessions was OK.

By the way, I think removing the DRI module **would** break 3D-acceleration.

On the upside, hibernate and wake up actually works with the 3D-driver, it never did in Hoary.

---

### Post by amohanty on 2006-01-02
> On the upside, hibernate and wake up actually works with the 3D-driver, it never did in Hoary.

Works for me too with the new drivers, however since this is our primary desktop and my wife and I both work on it, I need to get this to work. I thought it was using the wrong h/v sync rates, however I have a L90D+ LCD and have set the hsync and vsync manually based on the monitor specs to single values, so I am a bit confused as to whether it is the source of all the trouble or not. 

Although I am not overly concerned because even with the default ATI drivers my X300SE manages to give me ~800 fps (fglrx pushes it ~2000), I would like to know the source.

Any ideas how I would go about debugging it. Any pointers resources/docs I could look use to track it down would be great. 

Thanks.
AM

---

### Post by ysse on 2006-01-02
amohanty, I honestly don't know if my problem is the same as yours, but i get this in /var/log/kern.log:

```
Jan  2 23:55:14 localhost kernel: [4306698.208000] [fglrx:firegl_umm_init] *ERROR* UMM area already initialized!
Jan  2 23:55:14 localhost kernel: [4306698.209000] [fglrx:firegl_unlock] *ERROR* Process 9563 using kernel context 0
Jan  2 23:55:35 localhost kernel: [4306718.911000] [fglrx:firegl_lock_free] *ERROR* lock was not held by 1! (*lock=0x00000000)
Jan  2 23:55:35 localhost kernel: [4306718.911000] [fglrx:firegl_unlock] *ERROR* firegl_lock_free failed!

```

And these lines from xorg.20.log are not in xorg.0.log
```

(EE) fglrx(0): Failed to initialize UMM driver.
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8f03000 at 0xb7aee000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

So, what is the UMM driver?

I'm still not quite sure, but a bit of googling pointed me to this [http://lists.debian.org/debian-user/2003/11/msg02702.html](http://lists.debian.org/debian-user/2003/11/msg02702.html)

> That's quite normal since the second head is not 3D accelerated if you
are not running that "extended desktop" configuration in which both
heads are fed from the same framebuffer.

I suggest you try disabling any acceleration (even 2D at first), don't
load the DRI module or anything that might want to access the AGP bus
and try again. From there on, you can re-enable the stuff again one by
one (GLX is probably safe, but you never know).


The question in that thread did not actually concern dual-head, but a situation like yours and mine, where we want to switch between sessions.

I will try not to load dri and glx, and see what that does to my fps and session switching.
Back soon with results.

---

### Post by amohanty on 2006-01-02
I might be the same problem, because I see the same gunk in the kernel and Xorg log files. As to whether it shows up in the Xorg.20... or Xorg.0.. log file depends on which display you were on when you tried to switch. For me, the first new login works fine: eg.

user A logs in in display:0
user A uses New Login to login as User B on display :20
user B uses New Login to switch to User A's ongoing session
** BOOM **

I did try not using dri. Unfortunately then the fglrx module doesnt even load... wtf??? I have been reading up on the operation of xserver using 3d accl modules, but still havent managed to figure out what's going on. If you make some headway please let us know.

Thanks.
AM

---

### Post by ysse on 2006-01-02
Yes, you're right. Not loading dri (commented it out in xorg.conf) gave me a lowly 120 fps in glxgears, compared to 2120 fps with dri.

But switching sessions worked without dri.

So, where does that leave us? We get to choose between living without accel or without session switching?

I'm a bit out of my depth here, but would it be possible to supply some alternative xorg.conf for the second display, that didn't try to enable 3d?

/Anders

---

### Post by amohanty on 2006-01-02
> I'm a bit out of my depth here, but would it be possible to supply some alternative xorg.conf for the second display, that didn't try to enable 3d?

So I took your idea, hunted down the app which does the user switch: **gdmflexiserver** and went through the man page:

> GDMFLEXISERVER
8
2005-03-30
GNOME 2.6
Debian GNU/Linux

    * NAME
            gdmflexiserver - start a GDM session using the GDM flexible server mechanism, or in Xnest 
    * SYNOPSIS
            gdmflexiserver GNOME options gdmflexiserver options 
    * DESCRIPTION
            The flexi server mechanism allows to run GDM sessions on demand, in a new virtual console. The administrator can define multiple server configurations, using alternate X servers, or different options, in the gdm.conf file, and gdmflexiserver will present you with a menu, where you will be asked to choose between those server configurations marked with flexible=true.

            Alternatively, the --xnest option allows you to run a new session in an Xnest(1) window. 
    * OPTIONS
            In addition to the common Gtk and GNOME options, gdmflexiserver accepts the following options:

            "-c
                Send the specified protocol command to gdm 

            "-n,
                Xnest mode 

            "-l,
                Do not lock current screen 

            "-d,
                Debugging output 

            "-a,
                Authenticate before running --command

Unfortunately not much with specifying an alternate xorg.conf file. I am going to try to have fglrx on with dri support and see ifregular switch (via CLI) and a nested xserver (x in window in current session - again via CLI) will work. Will post the results.

AM

---

### Post by krewemaynard on 2006-01-04
You might want to try installing Xnest in the meantime. It runs the gdmflexiserver in a nested window, not full screen. You call it up as such:

$ gdmflexiserver -n

It's not perfect, but it's better than nothing. I've been having the same problem with my ATI Radeon (never had it with my nvidia, and may switch back). It sucks on a multiuser machine when you don't want to close out what you or someone else is doing.

---

### Post by nxn on 2006-01-04
This problem has been plaguing the ati drivers for almost over a year, if not over a year. Believe me, I have broken keyboards over this out of anger, the ati people seem to just shrug it off with each new update and I have no reason to expect them to ever feel like doing something about it. You can check the release notes on each of the drivers and look in the "known issues" section, it's been there so long it's growing mold. The last driver I remember that actually worked with multiple X sessions was one of the 3.* drivers.

Oh and stopping and starting X back up as a different user will lock it up as well if I remember correctly. So the only way around it is to comment out the Load "dri" line of your xorg config.

I promised myself to not ever buy anything from ATI again.

---

### Post by ysse on 2006-01-05
Thanks krewemaynard! I'd almost forgotten about xnest; it was installed by default on my old Linux laptop and I didn't know how to get it working in Ubuntu. But it wasn't very difficult. 

At least now I can fire up an session in English so I'll know what to call things when posting. (Was it System - Preferences or System - Settings?).

Well, the ATI driver surely is the biggest let-down right now. And as my system is a laptop, I'm stuck with it. (Grinning and bearing it)

---

### Post by amohanty on 2006-01-06
it works. nested x sessions work... whew. never going to buy ati again... cross my heart and hope to die if i do.

thanks all.

---

### Post by Ryuhayabusa on 2006-10-20
i've been watching, thanks for the help
i too am frustrated with ATI, and will not buy from them again (unless they change policy and cooperate with the community) i wonder how many other people will not buy ATI because of this type of problem? is ATI watching this forum?

---

### Post by imbjr on 2008-02-04
I'm currently experiencing this. Today, a long POV-Ray render got nixed because the wife needed to use the computer. ACK!

This Xnest business, though, I assume I would have to have an unlocked screen/my account for the wife to use it? I can't run it full screen, keep my account locked and let her log in through Xnest?

---

### Post by dda on 2008-04-26
Also got the same error and lockup after couple of switching between users: 
```

Apr 26 09:22:58 x700 kernel: [  208.051385] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000002
Apr 26 09:23:25 x700 kernel: [  222.063572] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
Apr 26 09:23:25 x700 kernel: [  222.063826] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Apr 26 09:23:34 x700 kernel: [  227.760955] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000001
Apr 26 09:23:34 x700 kernel: [  227.760963] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000002
Apr 26 09:23:43 x700 kernel: [  236.531708] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000001
Apr 26 09:23:43 x700 kernel: [  236.531827] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000002
Apr 26 09:23:43 x700 kernel: [  236.532281] [fglrx:firegl_lock_free] *ERROR* lock was not held by 4! (*lock=0x80000001)
Apr 26 09:23:43 x700 kernel: [  236.532286] [fglrx:firegl_unlock] *ERROR* firegl_lock_free failed!
Apr 26 09:23:46 x700 kernel: [  237.687791] [fglrx:firegl_lock_free] *ERROR* lock was not held by 1! (*lock=0x00000000)
Apr 26 09:23:46 x700 kernel: [  237.687797] [fglrx:firegl_unlock] *ERROR* firegl_lock_free failed!

```
I found that if after logging in to my desktop I click "switch user", log in into another account, then I can switch by Ctrl-Alt-F7/Ctrl-Alt-F8, and it doesn't fail. At least, I switched back and forth ~10 times. I will see if it works in a long term.

---

### Post by imbjr on 2008-04-27
> **dda said:**
> Also got the same error and lockup after couple of switching between users: 
```

Apr 26 09:22:58 x700 kernel: [  208.051385] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000002
Apr 26 09:23:25 x700 kernel: [  222.063572] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
Apr 26 09:23:25 x700 kernel: [  222.063826] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Apr 26 09:23:34 x700 kernel: [  227.760955] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000001
Apr 26 09:23:34 x700 kernel: [  227.760963] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000002
Apr 26 09:23:43 x700 kernel: [  236.531708] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000001
Apr 26 09:23:43 x700 kernel: [  236.531827] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000002
Apr 26 09:23:43 x700 kernel: [  236.532281] [fglrx:firegl_lock_free] *ERROR* lock was not held by 4! (*lock=0x80000001)
Apr 26 09:23:43 x700 kernel: [  236.532286] [fglrx:firegl_unlock] *ERROR* firegl_lock_free failed!
Apr 26 09:23:46 x700 kernel: [  237.687791] [fglrx:firegl_lock_free] *ERROR* lock was not held by 1! (*lock=0x00000000)
Apr 26 09:23:46 x700 kernel: [  237.687797] [fglrx:firegl_unlock] *ERROR* firegl_lock_free failed!

```
I found that if after logging in to my desktop I click "switch user", log in into another account, then I can switch by Ctrl-Alt-F7/Ctrl-Alt-F8, and it doesn't fail. At least, I switched back and forth ~10 times. I will see if it works in a long term.

Mmm, this is still happening? That's a pity.

---

### Post by dda on 2008-04-27
I found that it happens only when I logout from secondary session (using Gnome). If I end the secondary session by killing X (Ctrl-Alt-BackSpace), then I can open it again using "switch user". Added by notes here: [http://ati.cchtml.com/show_bug.cgi?id=1041#c7](http://ati.cchtml.com/show_bug.cgi?id=1041#c7) - maybe it will help to solve it.

---

