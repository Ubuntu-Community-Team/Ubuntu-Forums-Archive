---
title: "Problems with startx"
date: 2011-03-30
forum: Desktop Environments
---

### Post by Ghosthaven on 2011-03-30
I'm setting up a new ubuntu box to act as a home web server and I believe I messed something up.

I'm a semi-newbie and I'm not sure how to explain the problem, so I'll simply say what I wanted to do, what I did and the result.

What I wanted to do:
Have the ability to telnet into this machine and start xwindows so I can later vnc into it when I wished. Basically the only thing I wanted to do is startx so it would use the machine's physical display, keyboard, mouse, ect and allow me to connect via vnc later if I wanted it to.

What I did:
I telneted in from a windows machine and attempted startx (I knew this would most likely try to use my windows machine as the display and would kick out an error, but I figured it was worth a shot.
I then tried startx &. No luck there either. I then tried sudo startx. I think that's where I screwed something up.

Result:
Now, not only does it not work, but if I attempt to startx on the machine normally I get a blank screen.

I understand that I most likely somehow set the display incorrectly but I have no idea how to fix this.

Can I get some help with both fixing my screwup and getting things to work as I originally wanted?

---

### Post by Krytarik on 2011-03-31
> **Ghosthaven said:**
> 
Result:
Now, not only does it not work, but if I attempt to startx on the machine normally I get a blank screen.

Check "/var/log/Xorg.0.log" for error messages.

Also, why don't you simply set it up to run startx at startup?
This way you wouldn't have to find a way to launch it through the remote machine.

---

### Post by Ghosthaven on 2011-03-31
I want to run it without a gui most of the time to conserve resources but I want to be able to vnc into x when I want to as well.

As far as the log file... its pretty much all greek to me.
I'm attaching it here so hopefully one of you gurus can help me
figure out whats wrong. (added the .doc extension so I could upload it)

I really don't want to have to wipe the drive and start from scratch. :(

---

### Post by Krytarik on 2011-03-31
I figured you have Maverick 10.10 installed, right?

1.) There is an error message (although not stated as such) that a video driver library file is missing.

2.) The xserver apparently thinks all is well, but in fact nothing gets displayed.

Conclusion: It seems to an issue with the video driver (nouveau), and not related to the previous launch of startx with sudo.

Suggestion: Upgrade the video driver through Xorg-Edgers' PPA, it offers more recent drivers than the offical repos:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Ghosthaven on 2011-03-31
Yes, I have 10.10 installed. Actually a server install with the
ubuntu-desktop package installed on top of it.

I don't understand how it could be a driver issue, as X was
working perfectly fine before. I did what you said though with
no change.

I am able to reproduce the effect in a virtual machine. Telneting
into a ubuntu 10.10 box from windows xp and running sudo startx 
will reproduce the problem.

I noticed something new in the VM (and later confirmed on the
actual server) if left long enough, it'll time out and scroll a
good bit of text over the screen thats not in the logs. I didn't
see all of it but I did get the end of it from the VM:

```

..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
giving up.
xinit: Resource temporarily unavailable (errno 11): unable to connect to X server

waiting for X server to shut down error setting MTRR (base = 0xe0000000, size = 0x04000000, type = 1) Invalid argument (22)
 ddxSigGiveUp: Closing log
xinit: Server error.
xauth: error in locking authority file /home/andy/.Xauthority

```

Then it drops me back to my shell. To be clear, this is from
running startx from the virtual machine's main screen. Not from
telnet.

I also copied the output of my sudo startx over telnet attempt
that actually caused this error on the VM:
```

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
Current Operating System: Linux virtual-server 2.6.35-28-generic-pae #49-Ubuntu
SMP Tue Mar 1 14:58:06 UTC 2011 i686
Kernal command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=ce56f82e-5bb5-42c2-9358-bb9b2723a3d3 ro quiet
Build Date: 09 January 2011 12:14:58PM
xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubun
tu.com/support)
Current version of pixman: 0.18.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 31 10:46:13 2011
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) Failed to load module "vboxvideo" (module does not exist, 0)
(EE) open /dev/fb0: No such file or directory
(EE) VirtualBox USB Tablet: failed to initialize for relative axes.
^C
waiting for X server to shut down error setting MTRR (base = 0xe0000000, size =
0x04000000, type = 1) Invalid argument (22)
 ddxSigGiveUp: Closing log

```

At this point it started X normally on the main display of the VM 
as I wanted, but I wanted to reproduce what I did on the actual
server so in the telnet window I terminated with ctrl+c and got
this:
```

xinit:  unexpected signal 2.

```

I don't know what exactly is going on. I'm guessing that either
some permissions were changed when I ran it with sudo, or its
now looking for that .Xauthority file in root somewhere or...
I don't know.

UPDATE:
It seems I CAN run X from both the vm and the server if I use
sudo... this proves that its screwing up permissions or something... right? How do I correct this?

Side note: It seems that installing those updated drivers that
Krytarik recommended totally messed up X's display on the server.
Is there a way I can rollback to the previous drivers without
reinstalling everything?

---

### Post by Krytarik on 2011-03-31
Ok, now we have a somewhat clearer picture.

It maybe that when you did run startx with sudo, that changed the ownership of "/home/andy/.Xauthority" to those of root. Check that, and if so, revert it to yourself.

As for the nouveau driver, it is still under development, and thus may cause issues at some systems or setups.
So, would you like to install the proprietary driver instead?

If you want to purge Xorg-Edgers' PPA and downgrade all concerning packages, you could use the tool "ppa-purge" for that:```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```However, if you choose to use the proprietary driver, you shouldn't remove the PPA, since it also offers the most recent version of those.

To install those, assuming that you don't have it already installed, you could run:
```
sudo apt-get install nvidia-current
```Make sure that a proper xorg.conf is present:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```But if you are able to get to the desktop after possibly fixing the mentioned file permissions, you should install it via "System -> Administration -> Additional Drivers".

---

### Post by FOBS1 on 2011-03-31
I am having similar problems.

However, mine started with some update or other. I had 10.10, 8.04 and PinguyOS 10.01 installed.

Pinguy was the first to abort the GUI on startup.  I had similar problems when trying  startx.  Then, 10.10 did the same to me.  Working one day, no GUI next.  So I started 8.04.  It worked.  Tried to upgrade to 10.04. Had errors about Nvidia driver show up. Won't show GUI. Same starx problems

Unfortunately, I then erased all the Linux's (yes, I'm a newbie) and tried to reload from CD.

Same problem on startup - no GUI   So -I can't display the log files, since none are created.

System.  HP Pavilion m9040n Nvidia Gforce 8400

Knoppix still loads and runs, so it seems to be a problem with the current Nvidia driver included in the CD (or update).

Any suggestions as how to get a working driver onto the ISO?

---

### Post by Ghosthaven on 2011-03-31
Got everything fixed :) For some reason it did change the ownership
of .Xauthority.

I went ahead and did the ppa_purge thing but after everything got
working I installed the new drivers via the GUI.

Now that you've helped me fix my screwups... is there a way to do
what I originally wanted and trigger X to start on the main
display?

The only way I can figure out to do it is really insane... a shell
script to add a cron job to startx in 1 minute... or something like
that.

Being a newbie sucks :(

---

### Post by Krytarik on 2011-03-31
@FOBS1: Your issue is actually quite different to those this thread is basically about. Although *Ghosthaven* indeed had a temporary issue with running Xwindows (GUI) at all, just like you, it is basically about launching startx through remote control.

But nevertheless I will give a first shot: Try adding "nomodeset" to the kernel boot options. To do so, edit the kernel options while at the boot menu, you need to press the Shift key to make it appear, if you have only those single Ubuntu installed. Highlight the first boot option, that is usually the most recent kernel, then press "e" to edit its options. Add "nomodeset" right after "quiet splash", then press "Ctrl+X" to boot with those options. Those modification affects only those single boot process, it will not get saved.
Also see here: [https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot]("https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot")

If that works, you can set those option permanently by following this guide, add it again right after "quiet splash" as the value for "GRUB_CMDLINE_LINUX_DEFAULT":
[https://help.ubuntu.com/community/Grub2#/etc/default/grub%20(file)]("https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29")

If that doesn't work and you need more help, please start an own thread about that matter.

Also, the default driver being used during and right after the installation isn't the proprietary Nvidia driver, it isn't even included by the installCD. Your issue is actually more about the basic handling of your video card.

___________________________________________________________________________________________________

@Ghosthaven: Keep in mind that, like I said, that Xorg-Edgers' PPA offers the most recent packaged version of the proprietary driver. So, if you at any later time want to upgrade to those, you know the proper commands for that.

As for your actual startx launch matter, try this command:
```
DISPLAY=:0.0 startx
```Hope it works, for both of you!

---

### Post by FOBS1 on 2011-03-31
Thank you Krytarik, for your thoughtful reply.

While working with your suggestions, I saw some errors that referenced my wacom (tablet) drivers.  I unplugged that tablet and things proceeded properly.  I feel a bit silly, but am happy to be proceeding again.

---

### Post by Ghosthaven on 2011-03-31
I tried
```
DISPLAY=:0.0 startx
```
with no luck.
It gave me the following message:
```

xauth: (stdin):2:  unknown command "13ca6ec3237bc0f1bf4c4dc52a5c4e7b"

X: user not authorized to run the X server, aborting.
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```

I'm quite shocked that I'm the first to want something like this.
It seems to me that a lot of people would want to do something
like fire up their servers from work or whatever.

Any idea whats wrong? And should I file the whole sudo startx
changing ownership thing as a bug somewhere or is it just too
minor?

---

### Post by Krytarik on 2011-03-31
Please run this command to check if the variable is at least correct:
```
echo $DISPLAY
```> **Ghosthaven said:**
> 
I'm quite shocked that I'm the first to want something like this.
It seems to me that a lot of people would want to do something
like fire up their servers from work or whatever.
Yeah, I also didn't see a thread regarding exact those matter in these forums so far. But I also didn't do a web search so far, including these forums.
> **Ghosthaven said:**
> 
Any idea whats wrong? And should I file the whole sudo startx
changing ownership thing as a bug somewhere or is it just too
minor?
I really don't think that it's a bug. Actually, you should never run graphical apps with "sudo", usually you should use "gksudo", because the possible outcome is exact those what you had. However, I don't know if you could use "gksudo" in those specific application.
Also see here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

I need to say that I've actually not really an experience in ssh'ing into a machine, or telnet'ing like in your case, this one I know even more less. So, while trying to give you a helping hand, you shouldn't expect too much of me, because you are actually more experienced than me in that aspect. ;-)

---

### Post by Ghosthaven on 2011-03-31
It seems $DISPLAY isn't set (echos a blank line) when not running
X. But if I start X and check it in a terminal box, its set to :0.0

Where would environmental variables like that be stored? And what
should it be set to? (My VM installs of ubuntu have them blank
as well except for in X)

And the only reason I know anything about telnet is because I'm a
MUD admin :) I trust your guru-ness.
----------------------------------------------------------------------

Update:
Got it! Don'tcha just love Google?
It turns out that the file /etc/X11/Xwrapper.config has a setting that prevents anyone
from starting X without being at the keyboard.

To fix this, change:
```
allowed_users=console
```
to
```
allowed_users=anybody
```

I do have to admit though, the term "anybody" does scare me a bit. I'm not sure if that
opens security risks or not.

Now, to start X remotely, all I have to do is
```
startx -- :0
```

Now my problem is I have to keep the telnet connection active. Tacking & on the end of
that doesn't seem to background it normally. If I logout of the telnet session, it
freezes up X on the main display. Any ideas?

---

### Post by Krytarik on 2011-03-31
> **Ghosthaven said:**
> 
```
allowed_users=anybody
```I do have to admit though, the term "anybody" does scare me a bit. I'm not sure if that
opens security risks or not.
Ok then, I was more thinking along the lines of:
```
export DISPLAY=:0.0
DISPLAY=:0.0 startx
```That obviously wouldn't have fixed the "not authorized" issue, but you found it.
Maybe just try setting your username instead of "anybody", to address the security risk.
> **Ghosthaven said:**
> 
Now, to start X remotely, all I have to do is
```
startx -- :0
```Now my problem is I have to keep the telnet connection active. Tacking & on the end of
that doesn't seem to background it normally. If I logout of the telnet session, it
freezes up X on the main display. Any ideas?
Try both, my above stated commands, and this one:```
setsid startx -- :0
```

---

### Post by Ghosthaven on 2011-03-31
No luck with either
```
setsid startx -- :0
```
or
```
setsid startx -- :0 &
```
In both cases, when I exit the telnet session, the screen
goes insane, blinking a dialog box so fast I can't see it and
I can't do anything to stop it other than just reset the system.

This:
```

export DISPLAY=:0.0
DISPLAY=:0.0 startx

```
Started X properly, but still, its tied to the telnet screen.
When I close the session, X freezes.

Any other ideas? This seems like such a simple thing and setsid
SHOULD work from what I've read.

-----------------------------------------------------------------
Update:
Google for the win once again... I found a command that works a bit
like setsid called nohup. It basically ignores disconnects and stores
the output of a program into a file. This works perfect for my
purposes.

Now I just telnet in, and run:
```
nohup startx -- :0 &
```
and everything works exactly as I wanted. Seems that nohup is designed
for just this kinda thing.

Thank you Krytarik for everything!

---

### Post by Krytarik on 2011-03-31
Great! :)

Yeah, I did hear of "nohup" before, alongside to "setsid" and "disown". But I only used "setsid" so far, because it always worked, temporarily forgot about the others. Good to know.

---

### Post by kfpaulo on 2012-07-03
I have the same issue (EE) open /dev/fb0: No such file or directory
All I did was apt-get update/upgrade and install vnc4server (this is a remote VM)
I was doing it on ssh
User is not root but admin right. I'm on 10.04. When I vnc into it, I see only a terminal.
If I use the terminal through VNC, I get the following :

[I]xauth:  error in locking authority file /home/desktop/.Xauthority
xauth:  error in locking authority file /home/desktop/.Xauthority
xauth:  error in locking authority file /home/desktop/.Xauthority
xauth:  error in locking authority file /home/desktop/.Xauthority


Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log
No protocol specified
giving up.
xinit:  Resource temporarily unavailable (errno 11):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
xauth:  error in locking authority file /home/desktop/.Xauthority
[/I]
Any idea ?

Cheers

---

### Post by wildmanne39 on 2012-07-03
Hi, this is an old thread so it has been closed, please start a new thread.
Thanks

---

