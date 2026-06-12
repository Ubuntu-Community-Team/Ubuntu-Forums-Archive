---
title: "Sad beginnings"
date: 2006-09-29
forum: Desktop Environments
---

### Post by leonardotmnt on 2006-09-29
So I decided to try out linux because I heard it's starting to be more user friendly.  I made a livecd of Ubuntu and loaded it.  Everything went nicely but I decided I wanted to do some things on windows and needed to get back on.  I go to restart and my windows wouldn't load anymore and it kept giving me a stop code c000021a about an error in the logon process.  Long story short I ended up reinstalling windows and lost everything I had because of this.  

While this might be a windows error it still makes me not want to use Linux since even using a Livecd can apparently screw up a windows install (though I thought the livecd should do nothing whatsoever to the computer?).  Was there a way I could've fixed this without totally erasing everything I had?  It makes me very wary of Linux even if it's the fault of windows since I'm going to be primarily using windows until I get used to linux.

---

### Post by odinfromvalhalla on 2006-09-29
you could have just booted up with your windows cd, enter to rescue mode and fixmbr :P

it's your fault that your MBR got screwed up, not the live cd's

---

### Post by leonardotmnt on 2006-09-29
How exactly is it my fault?  I didn't even do anything in Linux. Just went to some websites and talked on Gaim.  If it's that finicky that it'll ruin a windows install doing that that's pretty sad.  Thanks for the fixmbr though, wish I knew that at the time.

Edit: It was my understanding that using a Livecd doesn't do anything to the hard drive.  Is that not the case? I just assumed that was most of the point in using it.

---

### Post by odinfromvalhalla on 2006-09-29
have you tried to install or anything? as by default (from what i know) the live cd does not try to setup a new MBR. it does that only on install (one of the final steps of the install actually)

---

### Post by morphodone on 2006-09-29
Sorry to hear that bro.

I don't think its anything you did or the live cd did either.

Probably a windows error that happened by coincidence.

---

### Post by odinfromvalhalla on 2006-09-29
anyway.. don't give up because of that. linux world is great :)

---

### Post by leonardotmnt on 2006-09-29
There was one thing I got from the applications part.  Would that have screwed it up?  Something I had read earlier talked as if it'd be fine if you did that.  Oh well I guess.

---

### Post by JedV on 2006-09-30
Were you using Dapper (6.06) or Edgy (6.10 -still beta)?

I did some siginifcant tinkering with the Dapper live CD prior to installing on a few different PC's, and none of them were effected at all.  Weird and unfortunate.

---

### Post by elementadiobam on 2006-09-30
Nothing was wrong with my computer when I put the livecd in. Your windoze was probably broken. I am now a proud Ubuntu Dapper user.

---

### Post by Atomic Dog on 2006-09-30
> **odinfromvalhalla said:**
> you could have just booted up with your windows cd, enter to rescue mode and fixmbr :P

True.  I never understood the overuse of fdisk and reinstalling the OS when a hiccup happens.  It truly is throwing the baby out with the bath water.

Anyway I seriously doubt it wass the live CD that caused your Winblows problem.

---

### Post by kerry_s on 2006-09-30
You proably accessed your windows drive, linux is still at the point where it's not very good with ntfs file system, but if you consider MS hasn't even bothered to make itself compatible with linux file systems, in fact it can't even see them.

---

### Post by leonardotmnt on 2006-09-30
Well, I wanted to repair windows but I didn't know the commands honestly.  I probably should've just tried the livecd again and checked out online before reinstalling but I wasn't in the best of moods after this happened.  

How would I have accessed the windows files while on the Livecd?  Is there something special I would've had to do?  It seems like more than a coincidence that windows amazingly decided to break itself at just the moment after I used the Livecd so I'm positive it was something that happened while using it whether it was my fault or not.  It was probably my fault but like I said before from what I'd read it seemed like the hard drive wasn't affected by anything done in Livecd.  I'll probably try this out again so I don't want to break it in the future, though it might be easier to fix since I've learned some console commands.  I guess I'm a big n00b when it comes to that stuff.

One more thing.  Has anyone had any experience with PCLinuxOS?  It was the other one I wanted to try out though Ubuntu seemed good before I ejected the cd :-k

---

### Post by lawina on 2006-09-30
The stop code you mentioned could be a windows security issue.

[I]0xC000021A: STATUS_SYSTEM_PROCESS_TERMINATED
(Click to consult the online Win XP Resource Kit article, or see Windows 2000 Professional Resource Kit, p. 1561.)
This occurs when Windows switches into kernel mode and a user-mode subsystem, such as Winlogon or the Client Server Runtime Subsystem (CSRSS), is compromised and security can no longer be guaranteed. Because Win XP can’t run without Winlogon or CSRSS, this is one of the few situations where the failure of a user-mode service can cause the system to stop responding. This Stop message also can occur when the computer is restarted after a system administrator has modified permissions so that the SYSTEM account no longer has adequate permissions to access system files and folders.[/I]

I have used various live cds including ubuntu, knoppix, pclinuxos, morphix, slax and didnt have trouble reading data from the native windows ntfs partition or the windows installation itself.

Good luck.

---

