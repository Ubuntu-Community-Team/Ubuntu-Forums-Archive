---
title: "X -nolisten tcp"
date: 2005-09-23
forum: Desktop Environments
---

### Post by bigqueso on 2005-09-23
I need to be able to remove the option to X that starts it with "-nolisten tcp".  I managed to do it once by hacking some config files (I don't remember which right now), but when I updated this morning my changes went away.  I want to find a way to do this that will persist across upgrades.  If you know which files I can change again, I would also appreciate that information.

Before I get responses saying that I should use "ssh -X" and tunnel X connections, let me tell you that doing this isn't really an option since the remote machine is too slow to encrypt the data at a reasonable rate.

Thanks,
James

---

### Post by Dooglus on 2005-09-23
You want to edit /etc/gdm/gdm.conf.

Where it says "DisallowTCP=true" you want "DisallowTCP=false".  Don't disallow TCP, allow it.

Are you sure about the -X tunneling being too slow?  It doesn't add very much of an overhead in my experience, and allowing TCP connections to your X server isn't a great idea from a security point of view.

---

### Post by bigqueso on 2005-09-23
You want to edit /etc/gdm/gdm.conf.

Where it says "DisallowTCP=true" you want "DisallowTCP=false". Don't disallow TCP, allow it.

-------------------------------------------------------------
This would probably work for Gnome, but I run KDE.  I found that I had to remove in /etc/kde3/kdm/kdmrc the argument of "-nolisten tcp" from the ServerArgsLocal variable.  

I restarted my session, but that didn't seem to work.  I then ran genkdmconf, restarted my session, killed X explictly (Ctrl-Alt-Backspace), and logged in.  That seemed to work.

I'm not sure if hard resetting my X server or running genkdmconf was the thing that made it work properly.

I will most likely have to reedit this next time kde starts up.  I'll post again if the config sticks (next time I update).

-------------------------------------------------------------------
Are you sure about the -X tunneling being too slow? It doesn't add very much of an overhead in my experience, and allowing TCP connections to your X server isn't a great idea from a security point of view.
------------------------------------------------------------------
SSH encryption is very slow using MIPS processors on an SGI Origin system (R14Ks if you're interested).  If you are trying to push a lot of pixels or geometry through SSH you will suffer greatly.  Even using a modern x86 processor can see performance degradation from going through a tunnel.

I wish there were an easier way to turn this on or off without having to edit config files and restart my X server every time I want to run an application remotely.  SSH just creates too much overhead.

I was looking through the forums and noticed something about xauth.  Perhaps there is something there.  Or maybe that's an alternative to xhost +machine.domain.com.

James

---

### Post by barna on 2007-09-27
I had the same problem, and I remember I solved it in the same way, quite some time ago. Now it showed up again (Feisty). I removed the -nolisten tcp options from 
/etc/kde3/kdm/kdmrc and /etc/X11/xinit/xinitrc
Restarted X (Ctrl+Alt+Backspace), rebooted the machine, etc, but still, it does not seem to work:

xhost +
ssh some.machine
setenv DISPLAY my_laptop:0.0
xclock

I need this way, since the application on the remote machine is using a heavy 3D GUI, which is substantially slower through the ssh tunnel.

Thanks for any idea

---

### Post by bigqueso on 2007-09-27
This is somewhat speculation, but I heard with newer versions of Xorg on Suse they completely removed the ability to listen for TCP at the source level.  This change may not have been Suse specific and may also be present in Feisty (I'll have to check my feisty install when I get in to work later).

If this is true, I will be very sad, for there are several cases where tunneling simply broke my rendering rather than just make it slow.

James

---

### Post by barna on 2007-09-27
Thanks a lot if you report any news on it. This would make also me quite sad.
Daniel

Ooops, it is solved: the network configuration of my institute has somehow changed unnoticed, and the IP address and hostname of my notebook was not the same as I believed. It works now.

---

