---
title: "My Ubuntu crashes on startup!"
date: 2008-07-25
forum: Desktop Environments
---

### Post by orphefs on 2008-07-25
Hello All,

I installed Ubuntu 8.04 recently; everything worked fine, set up the internet, installed Pidgin, installed the Eclipse environment through Synaptic Package Manager...While it was downloading and installing, I used 'shutdown -h +30' in order to give it enough time to install, so I could go to sleep!

This morning, I booted my PC, ubuntu graphical login screen shows up all nice and easy, so I type in username-password as always...But then, Ubuntu freezes, leaving a little white square box on the top left corner of the screen! The only thing I can do is press the power button on my PC, and when I do that the shell comes up going through the process of shutting down!


What is the problem? Please help me, I've gone through a lot, not to mention the faulty Asrock motherboard that froze my pc when I used the onboard LAN (got a new LAN card after all)!

---

### Post by orphefs on 2008-07-25
Any suggestions? :confused:

---

### Post by Joeb454 on 2008-07-25
You could try rebooting, and choosing recovery mode from the grub menu.

When that finishes loading (it'll give a root prompt) enter ```
dpkg --configure -a
``` and try again.

It may be that things didn't finish installing.

If not it's worth a try anyway :)

---

### Post by orphefs on 2008-07-26
Hey thanks for reading,

I followed your instructions, dpkg --configure -a did not display any message, then I tried the command startx, and a flickering like background appeared with a msgbox saying that I shouldn't be entering as a privileged (root) user, then I pressed continue and this white box appeared again :lolflag:

If I press 'quit' instead of 'continue' the command prompt appears again saying:

'Fatal server error:
Caught Signal 11. Server aborting

Emulator asked to make a suspect byte access to port 4 (0x0004); terminating.
Emulator asked to make a suspect byte access to port 4 (0x0004); terminating.'

I'm confused :confused:

---

### Post by babounours on 2008-07-26
You should try to know what is this box like by watching ps or top when the xorg starts.
create a new user and login with it, maybe this is only attached to your user

---

### Post by orphefs on 2008-07-26
I logged in with a new user, tried startx but that happens:

xauth: timeout in locking authority file //.Xauthority
X:user not authorised to run the X Server, aborting.
xinit: Server error.

What do you think the problem is?

---

### Post by upchucky on 2008-07-26
You may want to post this in the installations and upgrade forum, it will get better attention there.

it seems that the installation may be having trouble with the Video card to get the desktop working, however you do need to post some machine specs, and the output of some files before anyone can figure out where the problem is.

things to post are the contents and/or results of,
Code:

fdisk -l

this shows the drive geometry of your partitions and helps to find any boot problems

your /boot/grub/menu.lst file this shows what os to be booted.

your /etc/X11/xorg.conf this shows how the graphical display is set up

they will help in solving the problem, in the mean time search the forums for information on Video cards, grub loader, menu.list, and xorg.conf

there are hundreds of posts that have clues or even exact information if the system is the same as yours.

if you can boot and get a graphical display with the live cd without doing an install to the hard drive then the information on the boot messages has clues on the video setup, this will be a generic setting but the generic setting need to be put into the right files when you do the actual install, this is done from the command line.
upchucky is online now Report Post   	Edit/Delete Message

---

### Post by g4newbie on 2008-07-28
I had a the same thing, the previous evening I had changed my firewall settings via an iptables script and hooked it up via a pre-up script in /etc/network/interfaces.

I jumped to a text terminal [CTRL-ALT-F2] and backed out the changes, seems my iptables settings were interfering with the Gnome Display manager's connection over the loopback interface.

D'oh!

Hope this helps anyone who has the same issue and stumbles on this thread, if not the OP.

Also, this thread : [http://ubuntuforums.org/showthread.php?t=488689]("http://ubuntuforums.org/showthread.php?t=488689") suggests that if not the actual /etc/network/interfaces file, this definitely seems to be a network thing.

HTH

---

### Post by Azyx on 2008-07-28
Hi. Tried to start an erlier kernel? Today i upgraded to kernel 2.6.24-20 and my computer don't start. If I hold down esc-key during the GRUB-boot and chois thekernel 2.6.24-19, it boot as i should.

---

