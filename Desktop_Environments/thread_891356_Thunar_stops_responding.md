---
title: "Thunar stops responding"
date: 2008-08-16
forum: Desktop Environments
---

### Post by pmooney78 on 2008-08-16
I use Xubuntu GNU/Linux 8.04 on a Pentium III 550 MHz with 384 MB of RAM. Thunar CONSTANTLY and REPEATEDLY becomes unresponsive. (By which I mean very nearly completely unresponsive: I can move its windows, but they won't paint after something else is an front of them, and they don't respond to mouse clicks ... at all.) It doesn't matter how long I wait: I can walk off, go grocery shopping, go to work, etc.; when I come back, Thunar is still useless. Invoking "thunar -q" from a command line doesn't work, either. I can force it to quit with the System Monitor program, but having to do this is an enormous pain, especially if I'm in the middle of doing something already.

It seems to happen more often when browsing foreign (i.e. NTFS) partitions, or folders with lots of files, but I'm really not willing to reorganize or reformat my file system just to keep a buggy program from becoming unresponsive. (The computer should allow me to work in the way that's intuitive to me, not force me to organize my files in a way that keeps it from choking -- right?) Moreover, it happens under "normal" circumstances, too ... ext3fs partitions, in folders taht I own with only a few files.

This used to happen under Xubuntu 7.10, too. Quite frankly, I'm fed up with it. Can anyone recommend a fix, or some way of figuring out what's going on? Or a replacement for Thunar? My preference would be for something with a small memory footprint.

Many thanks for any advice.

---

### Post by mali2297 on 2008-08-16
I've never experienced these problems but if you want an alternative file manager, consider [pcmanfm](http://pcmanfm.sourceforge.net/) or [rox-filer](http://roscidus.com/desktop/ROX-Filer).

---

### Post by perixx on 2008-09-17
Hi pmooney78!

I know exactly what you mean. I'm using Xubuntu 8.04 64-bit here, but I've been encountering this menacing bug back since when I started with Xubuntu Feisty 32-bit over 1 1/2 years ago - on completely different systems:
my current one and on an old Thunderbird 1,2GHz board. 

I've even sent along a bugreport at bugzilla at that time (where other's reported the same issue as well), but no one seems to have been taking care about it. 
Perhaps it's about time to file some more bug reports, in order to make the Thunar devs finally wake up. 

perixx

---

### Post by pmooney78 on 2008-09-19
Thanks for the reply. I'd be happy to file a bug report, but I'm a newbie ... how do I file a bug report with bugzilla?

The thing is, I've tried other file managers, but I LIKE Thunar's interface & don't want to give it up. I'd be grateful if the problem just went away.

---

### Post by bionnaki on 2008-09-20
sudo apt-get install pcmanfm

just use that - its nearly the same.

---

### Post by perixx on 2008-09-20
Hi pmooney78...

sorry, but I mixed it up here - it's not bugzilla, but launchpad, that's being used as a bug filing platform for Ubuntu. Pardon that, but it's been quite some time since I last filed a report!

Head over to 
> [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
and generate an account there (you can use it for future bugreports, too).
Then go along the instructions and look if your problem is already mentioned
(which it should be) and you should confirm this bugreport. 
If not, or if you're unsure, file a new report and try to be as specific as possible with your bug description, preferably providing a procedure, on how to reproduce the bug successfully (when it does appear most certainly).

Also, don't forget to mention your OS version (Hardy/Gutsy/Xubuntu/Kubuntu...) and perhaps some notes on your hardware. 

I know it's kind of cumbersome at first, but you'll get used to it quickly.

greetings,

perixx

---

### Post by gcmelzi on 2008-10-10
I'm just searching for the same problem here. 
One thing I've tried yesterday was launching thunar as superuser (sudo thunar) from terminal while another Thunar window stops, and constantly it works. So I'm wondering if this has to do with permissions.
Could you give a try and confirm "sudo thunar" works for you?

---

### Post by pmooney78 on 2008-10-23
I use "gksudo thunar" occasionally, mostly to mount devices that aren't in /etc/fstab, and haven't ever seen any problems with it, but I don't use it for very long, so maybe that's why.

I'll try to use it more extensively and see whether the problem still crops up.

---

### Post by perixx on 2008-10-23
I haven't encountered any crashes of Thunar for two or three weeks now; perhaps the kernel-upgrade has made a change to the better?

perixx

---

### Post by perixx on 2008-10-23
Oh yeah. Speaks and... crash again. 

I can almost certainly track it down to when using 2 or more instances of Thunar at a time and/or involving access to non-user folders during prolonged working with Thunar and other applications.

perixx

---

### Post by pmooney78 on 2008-10-25
Yeah, that was my thought too. "Oh good, new version seems not to crash as often ... wait ...". And I've discovered that it happens even when using Thunar in super-user mode. For me, it happens more frequently when I've got multiple Thunar windows open (which is the case most of the time), but still happens when I only have one instance running.

---

### Post by pmooney78 on 2008-10-25
Oh, and I notice CPU usage (for Thunar, as reported in the GNOME system monitor) drops to zero when it's not responding, although it's frequently zero anyway when Thunar isn't doing anything. Changing the priority (e.g., with "sudo renice [some number] [pid]" in a terminal) doesn't make any difference, either. Don't know if any of this is relevant.

---

### Post by perixx on 2008-11-01
Say, do you use the 32-bit version of Xubuntu or 64-bit? 
Single-core or dualcore? Intel/Athlon?

I'm using an Athlon 64 X2 3800+ here. It was causing some trouble in the past to me, so I just thought...

perixx

---

### Post by perixx on 2008-11-04
**Capture!**

Here's you can find a long-term bugreport about our specific problem: 
> [http://bugzilla.xfce.org/show_bug.cgi?id=2502](http://bugzilla.xfce.org/show_bug.cgi?id=2502)

It's a bug that's been known since 2006, but I'm not sure whether it's an XFCE desktop's glitch or a bug in Thunar...

So far, I've sent a bugreport to the Thunar team, as soon as I find my password for bugzilla again, I'll send one to XFCE, too :P
You can hop over, create an account (if you don't already have) and contribute your bugreports to mine, so we do gain more overall weight:
> [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/293839](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/293839)
**But please be polite**, no hassles or insults here. Be objective and try to provide information to the devs: OS + Thunar version, how do you reproduce the crash?

To temporarily avoid your crashes (that I suppose are triggered by hiding/unhiding hidden files, ONLY when the tree view is active, like mentioned under this bugreport), uncheck View > Sidebar > Tree view 
in Thunar's menu.

Regards,

perixx

---

### Post by perixx on 2008-11-14
Good news!

This bug has been confirmed recently and is being worked on:

[http://bugzilla.xfce.org/show_bug.cgi?id=2502](http://bugzilla.xfce.org/show_bug.cgi?id=2502)

Don't know, when there will be a bugfix via the official repositories, though.


perixx

---

### Post by pmooney78 on 2008-11-17
Hooray!

---

### Post by perixx on 2008-11-18
Yeah, great, isn't it?


And even better: the bug's been already fixed on SVN repository! 
So the only question is, when a new stable version of Thunar is released and actually included into the official update repositories... :)

greetz,

perixx

---

### Post by pmooney78 on 2008-11-21
Wonderful! I'll be waiting to see Thunar in my Update Manager list. 

And in response to your earlier question, I'm using a 32-bit version (Pentium III, 550 MHz ... yeah, it's a dinosaur.:) )

---

### Post by perixx on 2009-02-01
I think the bugfix has been applied to the repos and was eliminated with an update, meanwhile. At least so it seems - can anybody confirm this?


perixx

---

### Post by pmooney78 on 2009-02-03
It never seems to happen to me anymore ... but then, I'm now using 8.10 on a new computer ...

---

### Post by perixx on 2009-02-04
** Just successfully crash-landed 2 Thunar windows** 
:D

No, we're just not there yet...
I simply opened a Thunar window in my home folder, another one in /usr/local/share/, both with 'tree view'. Then I did CTRL+H twice - bam, both windows gone zombi-style. The old song.

I really wondered, because I usually skim all the updated prior to installing them, and I can't remember seing about Thunar once ever since the bug was fixed. No, we're just not there yet.


perixx

---

### Post by pmooney78 on 2009-02-09
Yeah ... doesn't seem to happen as much for me anymore, but it does happen sometimes.

Thinking about chucking Xubuntu entirely for exactly this reason and moving to a different distro. What a pain in the ***.

---

### Post by adamlau on 2009-02-10
Open a virtual session to examine errors thrown, run Thunar from a terminal session, check logs.

---

### Post by pmooney78 on 2009-02-10
> **adamlau said:**
> Open a virtual session to examine errors thrown, run Thunar from a terminal session, check logs.

Sorry ... way over my head. I can run Thunar from a terminal, but what is a virtual session? And where does Thunar keep its logs?

---

### Post by perixx on 2009-02-10
Well, 

it's basically just open a terminal (Menu > Terminal) and type 'thunar'. Now, use Thunar till it freezes (usually press CTRL-H twice does it) and look what the error output in the terminal says (if there's any, that is).
Normally, there should also be some evidence of the crash in ~/.xsession-errors, even if you don't start Thunar in a terminal, though.
IF there is any such error output, because the filemanager doesn't actually crash, but hang-up instead, that's different. 
In such a situation, the questionable application will most likely not respond or give any error output at all, I suppose.

[just checked it - there's no output in the terminal and .xsession-errors for this specific hang-up]

regards,


perixx

---

### Post by pmooney78 on 2009-02-27
I'm ready to chuck Xfce entirely. Is there an easy way to migrate to Ubuntu or Kubuntu without reinstalling?

---

### Post by pmooney78 on 2009-03-03
OK, done. I've happily migrated to Ubuntu. Thunar can #$&*&$#&$*#$#&$*#&*$#&*$#. I'm tired of it and like Nautilus better anyway, now that I've been using it for a few days. There are other things I like better about Ubuntu, too, now that I've given myself a few days to adjust.

---

### Post by perixx on 2009-04-25
Congratulations, pmooney :]


If not for the LTS, I'd maybe switch to 8.10, which is said to have better comfort like an integrated find feature (in Thunar too?).
But then again, who says, they'll get around and apply the fixes we've been talking about here.

Perhaps I should let the xfce team have a mail about this matter. No idea, why they have such a poor update policy for their vital applications, it really puzzles me.

As of late, I've been working a lot with OpenSuSe 11.0 and KDE. Didn't like the bloat and Konqueror despite of all the eye-candy. Perhaps it would've been better with Gnome. But it has some advantages: it's more like a mixture of a server- and a client system, or so it feels. Network services seems to fit better into place and integrate easier than in Ubuntu. Also, it has many neat system scripts and stuff. 
On the down-side, Novell seems to have an urge to differ from the things I'm used to in Linux in many ways, which is annoying. Boot options and system-specific expressions for example. This gives sort of an MS-like feeling sometimes...


perixx

---

### Post by pmooney78 on 2009-04-28
Thanks! I'm happy to have migrated over to Ubuntu and have chucked XFCE. I agree, long-term failure to deploy a bug fix for a fundamental part of the OS, like a file browser, is a serious problem. 'T any rate, I only settled on Xubuntu initially because I was using an incredibly old machine, but that's no longer a limiting factor. 

My initial reaction to OpenSUSE was negative for reasons I no longer remember ... it's been a while, and I think it was just that things didn't work the way that I expected them to. (Of course, that was my initial response when migrating away from Windows!) But I've been playing with Fedora over the last few days and it's growing on me.

Of course, at some point, I'm going to settle on a distro that works for me and let the setup issue more or less fade into the background so I can use the computer to accomplish tasks ...

---

### Post by perixx on 2009-05-11
I've recently reported, the bug's being persistent in the LTS version of Xubuntu. It's already been fixed in Jaunty and the dev's response suggests it might be eventually fixed in Hardy via a SRU from a backport, if someone finds the time to do it.

That's by far better an experience than I've had with the Openoffice bug reporting system, so far.

Have fun with Fedora...


perixx

---

