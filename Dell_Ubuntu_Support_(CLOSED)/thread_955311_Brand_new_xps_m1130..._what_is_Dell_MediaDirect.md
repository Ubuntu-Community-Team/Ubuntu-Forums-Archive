---
title: "Brand new xps m1130... what is Dell MediaDirect?"
date: 2008-10-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nikkkko on 2008-10-22
I took delivery of a Dell Ubuntu XPS M1330 last week and I am not disappointed.  Everything works perfectly and it was a good 100€ cheaper than the Windows version, (I am in France).  

However, one thing puzzles me. The laptop has a MediaDirect button and play, fast forward, pause, etc. buttons under the screen and is supplied with a dinky little remote control. Pushing the MediaDirect button, (when the computer is off), produces a MediaDirect splash screen and then the computer boots to Ubuntu as usual.

Reading on this forum and other sites it appears that MediaDirect is an OS of some kind in a separate partition which allows the XPS to be used like a DVD player.  I like this idea, but does it work under Ubuntu?  There is no documentation and I can't see anything on the Dell site.

Anyone out there got one of these and uses MediaDirect or knows whether it should work?

---

### Post by jespdj on 2008-10-22
The manuals that you got with your computer explain what MediaDirect is. It's a kind of mini-version of Windows XP meant to start up quickly so that you can use your XPS to watch a DVD, for example. In my opinion, it's a useless gimmick.

I don't use it. In fact, I deleted the MediaDirect partition when I installed Ubuntu. Some people report problems when they press the MediaDirect button, it seems that on some Dell computers it messes up the boot record and makes Ubuntu unbootable. I don't have such a problem on my XPS M1530. When I press the MediaDirect button, it shows a MediaDirect logo on the screen and boots into Ubuntu.

---

### Post by nikkkko on 2008-10-22
It's a gimmick because it uses a cut down Windows or because it doesn't work?  I also have an XC Cube box running Ubuntu and it has a DVD player on a ROM somewhere on the motherboard.  It's pretty useful and I was hoping this was something similar.

---

### Post by flakrat on 2008-10-22
I imagine that it would be useful for someone who wants to watch a lot of DVD's on their laptop (maybe someone who has a long commute or travels a lot?). Just like what was said previously, it's a small partition on your hard drive that allows you to quickly boot into a media player.

I had to delete it on my m1330 because I purchased mine with Vista (this predated the Ubuntu option), and at the time I wanted to dual boot. Unfortunately, I couldn't split the Vista partition without deleting another partition, the mediadirect partition was the sacrificial lamb.

A few weeks later I opted to nuke the whole system in favor of a full Ubuntu install with a Window virtual machine. I never did get mediadirect back on the system.

If I push the button with the laptop powered off, I'll get a mediadirect splash screen, and then an error that the partition doesn't exist.

---

### Post by flakrat on 2008-10-22
I should also add that the mediadirect button will open Rythmbox on my system when pressed while Ubuntu is running.

---

### Post by nikkkko on 2008-10-23
I guess MediaDirect is not an option for the Ubuntu ver of this laptop because it's a Windows derivative, so whether it works or not is probably academic.  It would be nice to have an answer from Dell as to whether this is a functionality offered to Ubuntu customers, even if just to confirm a negative.  I posted in the Dell forums but got no reply.

(And yes, I have a 1500km drive coming up and three kids in the back who would love to watch DVD's without having to ask me for my login)

---

### Post by jespdj on 2008-10-23
> **nikkkko said:**
> It's a gimmick because it uses a cut down Windows or because it doesn't work?
It's a gimmick because is doesn't really add any value (ofcourse that's my personal opinion). You can just as well play DVDs etc. with a media player in the normal operating system that you have installed on the computer.
> **nikkkko said:**
> (And yes, I have a 1500km drive coming up and three kids in the back who would love to watch DVD's without having to ask me for my login)
You can set Ubuntu or even Windows to log in automatically, so that your kids don't have to enter your password.

---

### Post by superm1 on 2008-10-23
> **nikkkko said:**
> I guess MediaDirect is not an option for the Ubuntu ver of this laptop because it's a Windows derivative, so whether it works or not is probably academic.  It would be nice to have an answer from Dell as to whether this is a functionality offered to Ubuntu customers, even if just to confirm a negative.  I posted in the Dell forums but got no reply.

(And yes, I have a 1500km drive coming up and three kids in the back who would love to watch DVD's without having to ask me for my login)
Media direct is *not* offered with Ubuntu installs.  It's purely coincidental that the factory process causes that key to be mapped to it still before the OS is booted.  In the current factory implementation, there simply aren't enough primary partitions to go around if it were to be enabled, let alone it being an entirely closed source solution.

Partitions:
<1> dell diagnostics
<2> fat32 / recovery partition
<3> ext3 / ubuntu partition
<4> extended
       <5>  swap

> **jespdj said:**
> It's a gimmick because is doesn't really add any value (ofcourse that's my personal opinion). You can just as well play DVDs etc. with a media player in the normal operating system that you have installed on the computer.

You can set Ubuntu or even Windows to log in automatically, so that your kids don't have to enter your password.
Also worthwhile to note that there will be guest session support in 8.10.  You will be able to just click a guest session button for people to be able to login instead for this purpose.

---

### Post by maraja on 2008-10-23
it would be really nice to get instructions letting us configuring the media key so that it will automatically load mythubuntu (installed in a separate partition)

please please please!

---

### Post by cendant on 2008-10-23
Be careful!

If you re-install your own Windows or another Linux and accidentally press MediaDirect button, it will make your system inaccessible. MediaDirect will mess your hard drive big time and even RescueCD will be of little help.

I got rid of MediaDirect nearly at once last year (after I lost some photos because of this beast) and I do not regret it.

Note: Just partitioning the disk is not going to delete MediaDirect partition. It is a special type of a hidden partition and you can get rid of it if you NULL your hard disk.

I can't remember the details, but I used Ubuntu LiveCD and the command dd in the console to wipe the XPS's hard disk properly

---

### Post by maraja on 2008-10-23
> **cendant said:**
> If you re-install your own Windows or another Linux and accidentally press MediaDirect button, it will make your system inaccessible. MediaDirect will mess your hard drive big time and even RescueCD will be of little help.

I experienced the problem and I was able to restore the Ubuntu partition using [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") :)

---

### Post by superm1 on 2008-10-23
> **cendant said:**
> Be careful!

If you re-install your own Windows or another Linux and accidentally press MediaDirect button, it will make your system inaccessible. MediaDirect will mess your hard drive big time and even RescueCD will be of little help.

I got rid of MediaDirect nearly at once last year (after I lost some photos because of this beast) and I do not regret it.

Note: Just partitioning the disk is not going to delete MediaDirect partition. It is a special type of a hidden partition and you can get rid of it if you NULL your hard disk.

I can't remember the details, but I used Ubuntu LiveCD and the command dd in the console to wipe the XPS's hard disk properly
This does not happen on Ubuntu preinstalled systems, only Windows preinstalls.  It shouldn't happen with later versions of mediadirect either.

---

### Post by nikkkko on 2008-10-23
> Media direct is *not* offered with Ubuntu installs. It's purely coincidental that the factory process causes that key to be mapped to it still before the OS is booted.
> It is a special type of a hidden partition and you can get rid of it if you NULL your hard disk.

Does the Ubuntu version of the Dell laptop still have the hidden partition where MediaDirect used to hide?

---

### Post by nikkkko on 2008-10-23
Ok, last question. What are the chances of sticking a linux os in the hidden partition, (or any partition), which boots in 5 seconds and launches a dvd/cd player full screen, and which makes use of the play, pause, fast forward etc. hot keys?

---

### Post by superm1 on 2008-10-23
> **nikkkko said:**
> Does the Ubuntu version of the Dell laptop still have the hidden partition where MediaDirect used to hide?
No it does not.  This is why the key only shows the splash screen (artifact of the factory process)

---

### Post by superm1 on 2008-10-23
> **nikkkko said:**
> Ok, last question. What are the chances of sticking a linux os in the hidden partition, (or any partition), which boots in 5 seconds and launches a dvd/cd player full screen, and which makes use of the play, pause, fast forward etc. hot keys?
This should technically be possible, but you'll have to go mucking around a bit and probably do some forensics on the boot sector with a machine that has media direct installed.  If you want a challenging project, I say back up your stuff, and try to get it back to a factory state with Vista & Media Direct on it, and then analyze what's really going on.

---

### Post by nikkkko on 2008-10-23
> This should technically be possible, but you'll have to go mucking around a bit
Just fishing really, wondering if someone else out there might like to run with the idea.

---

