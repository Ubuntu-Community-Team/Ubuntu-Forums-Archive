---
title: "Thunar takes over 60 seconds to start up"
date: 2014-09-20
forum: Desktop Environments
---

### Post by WB0HYQ on 2014-09-20
In xfce4.10, I am trying to use Thunar file Manager.  Every time I start it up (using Cairo Dock) the icon bounces merrily up and down to ten seconds and then stops.  Nothing happens for 30 to 35 seconds and then I get a blank window (nothing inside it) 25 to 30 seconds later, my home directory is presented to me.

I installed Xubuntu about two months ago, but this Thunar thing began around a week ago and has not let up since.  I have a feeling that some update or other messed things up, but I haven't a clue what happened.

Has this type of behavior happened to anyone else?  If so, what have you done about it?  I looked into the Thunar Forum on the XFCE site, and found a couple of things which didn't help (most notably, a change to /usr/shares/gvps/mounts/ntwork.mount -- changing automount from True to False).  That did NOT work, even after a reboot.

Bill

---

### Post by vasa1 on 2014-09-21
> **WB0HYQ said:**
> ...
I installed Xubuntu about two months ago, ...
Is your system pure Xubuntu or Unity + the Xubuntu desktop?

---

### Post by Toz on 2014-09-21
And if you run "Thunar" from a terminal window, are any messages displayed?

---

### Post by matt_symes on 2014-09-21
Hi

It's a long shot but maybe worth asking anyway. 

Are you trying to auto-mount any NFS shares that are unavailable ?

Kind regards

---

### Post by WB0HYQ on 2014-09-21
@Vasa1: I am pretty sure that I run Unity with the Xubuntu desktop.  When I installed XFCE, I used the apt system and my notes tell me I used the install xfce-desktop command.  If I log out, and click the round icon just over the "password" box, I get the following:

Cairo-Dock (GNOME)
Ubuntu (Default)
XFCE Session
Xubuntu Session

At the moment, I am using the third option (XFCE Session), but when I really want to communicate with my other computer systems (both Windows and Ubuntu), I use Ubuntu Default because the file system is much faster.

My major problem with all the external machines is that each of them, in turn, have USB external drives on which I have made shared directories.  I suspect that Thunar is having a great deal of trouble gathering up all the queries and replies from those external machines on startup.  Once Thunar starts up - and for perhaps 10 minutes after I have closed it again, Thunar will start up again very quickly.  After around 10 minutes, I have to go through the 60-second long wait to again give me a window.

@Toz:  From a terminal, the command 'thunar' give me no messages at all, but the 60-second delay is present.  The behavior following that is exactly the same as what I outlined to Vasa.

Bill

---

### Post by Morbius1 on 2014-09-21
I've never experienced a 10 minute wait but see if this works for you - you can always reverse it is required:

Change the following file: /usr/share/gvfs/mounts/network.mount 

From this:
> [Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
**AutoMount=true**
To this:
> [Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
**AutoMount=[COLOR=#0000cd]false[/COLOR]**

What you take away from one end you have to deal with on the other however so it may take a while when you select "Browse Network" to see anything - unless all your other machines are Linux or OSX and you use avahi.

---

### Post by matt_symes on 2014-09-21
Hi

From your last post, I assume you have no NFS shares.

> From a terminal, the command 'thunar' give me no messages at all

Is there any iindication as to what the reason for the slow start may be if you start Thunar using strace ?

Kind regards

---

### Post by WB0HYQ on 2014-09-21
@Morbius1:  The 10 minutes was not a wait.  What I said was that if I close Thunar completely and then wait around 10 minutes to try and start it again, I have the 60-second delay again.  I suspect that something is timing out (possibly the network or perhaps the actual connection to my other networked shares) which then has to be built up again.  I found your True/False solution while I was searching the Thunar Forum and tried it.  There was no difference noted even after I rebooted the computer.  From that, I can make an inference that AutoMount isn't part of the problem.

@Matt_Symes:  Some of my external shared directories reside on external USB drives on my Windows 7 (NTFS) machines.  When I am actually ON those machines, there seems to be a delay of around 10 seconds accessing my huge (2TB) USB drives if I haven't accessed them for a while (say, over 10 minutes).  For some reason (they are WesternDigital drives) they "go to sleep" even though I've tried my best to make them stop including "don't let this device power down to save resources".  I think the 'go to sleep' is built-in to the drives.

In any case, if I leave Thunar running and simply minimize it to an icon, it will be instantly ready any time I need it.  So that's my temporary solution to the problem.  There are some shared directories listed in Thunar that are actually on external (networked) machines.  If I select one of them, I do get a 5 to 10 second delay just the same as if I was on the physical machine and accessed the drives.  This is far and away better than having to wait 60-seconds to even view LOCAL drives and directories.

I hope the above makes sense.

I will try 'strace' for Thunar, see what happens, and report back here.

Bill

---

### Post by WB0HYQ on 2014-09-21
The 'strace' command, which I used to output to a local TXT file, did exactly the same as starting it from Cairo Dock or by the terminal command 'thunar'.  I waited 30 seconds for a blank window to appear, and then another 30 seconds for it to populate.  Among the locations in the left panel (which I've set to listview) were three external links identified by "/linkname/".  I closed those links (there were three) and Thunar itself.  Then I tried the command again 15 minutes later.  The same 30/30 second delay appeared, but the three external links were gone.

This would seem to indicate that the hangup is NOT connected with external links, but more having to do with something on my own system.  I do have one external USB drive (1.5Tb, divided into roughly half, designated as "TERA_T" and "TERA_U".  Both reside on another WD external USB drive that, in Windows, will take 10 seconds to open if not accessed in around 10 minutes.

In Windows, I have created a .NET program that reads, then writes to a throwaway TXT file on TERA_U named 'keepalive.txt'.  It does this every 300 seconds (5 minutes) and, when this program is running, I do NOT get the 10-15 second delay on first access after a long period of time.  Could this be the initial delay I am seeing in Thunar?  I am not convinved of this for a couple of reasons: 1) I duplicated the program in Gambas and when it is running, I still get Thunar's delay no matter what; and, 2) Thunar didn't start doing this until around a week or ten days ago after a fairly massive update of all sorts of Ubuntu internal libraries.  I have a feeling that this update caused the response in Thunar.

The file created by 'strace' is quite large (2.1Mb) so I hesitate to attach it to this post.  There are entries which deal with "TERA_T" and "TERA_U", which appear to be accessing both halves of the same drive without any errors popping up.  I don't know this for sure as I have no real grasp of what is being logged.

Bill

---

### Post by matt_symes on 2014-09-22
Hi

> Thunar didn't start doing this until around a week or ten days ago after  a fairly massive update of all sorts of Ubuntu internal libraries.  I  have a feeling that this update caused the response in Thunar.

You can confirm this by booting into a LiveCD/USB and see if you get the same slow down.

You can then look at your update history and see if there were any likely culprits installed around that time.

Kind regards.

---

### Post by WB0HYQ on 2014-09-22
The only 'live' CD I have is the plain-jane version of Ubuntu 14.04.  Thunar appears when I run the xfce4 desktop, which, as far as I can tell, isn't on a live CD.

What I have done, and it seems to be working just fine, is to start Thunar once and never close it.  If I minimize it I can drag it to an inconspicuous spot on my desktop - or another desktop (I have 4 set up) and recall it when I need it.  That way even the networked shares are still live and appear nearly instantly when I click on them.

Given the amount of updating that goes on (and I definitely am NOT complaining about that) this may all blow over soon anyway.

Thanks for the info though, Matt.

Bill

---

### Post by vasa1 on 2014-09-22
I don't use Thunar now but I remember seeing this in **man thunar**:>  **--daemon**
           Do not terminate the Thunar instance when the last window is
           closed, but keep it running to speed up opening new windows later
           on. This is the default when spawning Thunar as part of the default
           Xfce session or when using D-Bus activation.Would that be of any help?

---

### Post by WB0HYQ on 2014-09-22
I saw that before, but when I tried to run it with that parameter absolutely nothing happened when run from a terminal.  Thunar didn't appear but, according to the Task Manager it was there, but no window ever opened.  I entered it under "session and startup" and still nothing appeared when I logged out and back in.  So, I am still using my stopgap method of just minimizing the app and stowing it away in a corner of my desktop.

Bill

---

