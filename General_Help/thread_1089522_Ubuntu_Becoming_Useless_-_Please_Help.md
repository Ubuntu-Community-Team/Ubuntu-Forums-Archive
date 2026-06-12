---
title: "Ubuntu Becoming Useless - Please Help"
date: 2009-03-07
forum: General Help
---

### Post by fidgaf on 2009-03-07
A moan and mini rant....

I have a dual boot Intrepid Ibex Ubuntu 8.10 and XP Pro.

Each is on its own dedicated Hard drive. No problems there.

I installed Ubuntu as an early Hardy Heron with the intention of moving most of my PC activity from XP to Ubuntu as I got more and more used to Ubuntu.

This was very successful and I was rarely booting into XP - Just for the odd game.

Since installing 8.10 (January) the reverse has happened very rapidly. I have hardly used Ubuntu and then mostly only to keep it updated or look at a bookmark or two that I had never transfered.

Why? 

Minor reasons are: 

My webcam does not work but did before. 

Automatic mounting of several partitions fails, but worked before (NTFS config).

Without auto-mount my Amarok has no music files to access and I keep forgetting (shut down Amarok, mount, start Amarok - It might decide to work).

There was a new driver installed on upgrade for my Nvidia card which seems quite poor and twitchy where it was not before.

A new usb headset doesn't work (plug and play in XP).

Ubuntu decides for no apparent reason to fail to find my Internet connection (wired to a wireless box). I do not recall this happening before.

As I said, minor niggles which might be fixable but shouldn't have gone wrong in the first place.

The MAJOR complaint is the [90 seconds delay while booting]("http://ubuntuforums.org/showthread.php?t=1052861").

Ubuntu had a major benefit as a fast booting O/S - This has gone. I now have XP as my default boot as it's now sooooo much faster.


My enthusiasm for Ubuntu has faded rather badly - perhaps if I can get the delay removes I might spend the many hours required to fix the other issues but have no idea where to start (I can't even find my Webcam's model).

Perhaps I should have stayed with hardy Heron?

I have yet to find any benefit in 8.10.

I am now starting to believe that Ubuntu is not a viable alternative to Windows - too much messing about and useless for the totally inexperienced, particularly with PCs becoming so multimedia, Internet and USB oriented.

Convince me otherwise. I want to be.

Thanks.

---

### Post by howefield on 2009-03-07
> **fidgaf said:**
> Perhaps I should have stayed with hardy Heron?

I agree.

You had a working solution you appeared to be happy with, use it or triple boot with Intrepid if you feel like tinkering enough to resolve your "minor niggles"

You could also try another distro, apart from Ubuntu the ones I find that just work are Mandriva and Fedora.

Good luck.  But don't give up because one edition regressed on you, could be that Jaunty gives you just as good a system as Hardy and that is only a few weeks from release.

---

### Post by fidgaf on 2009-03-07
Is my Hardy Heron setup recoverable?

I thought not.

---

### Post by howefield on 2009-03-07
And why would that be ?

Thought so.

---

### Post by fidgaf on 2009-03-07
How do you recover the previous install? I didn't think it possible.

---

### Post by howefield on 2009-03-07
Recoverable in the sense that you can reinstall.

Given your response, probably not what you want to do.

---

### Post by Therion on 2009-03-07
Just consider all this a big learning experience and reinstall Hardy.  I've reinstalled Hardy over a dozen times (no joke).  

I've tried Fedora, Suse, Sidux, Debian and most recently Jaunty (pre-release obviously) and I keep coming back to Hardy because NOTHING beats Hardy Heron's combination of unshakable stability on my system, overall ease of use and how... How... (gawd, I hate saying this) how "Everything just works".

You know it takes about a half hour or so to do a fresh install.  Give yourself another hour, hour and half to update, download and install any additional particular packages you may want or need, do some final tweaking and dude... You're back in the game and telling Microsoft to kiss your shiny white a--.  Or black or brown or whatever color your particular shiny a-- happens to be.  That's not my point... 

Doing a fresh install of Ubuntu is really no big deal.  A couple hours of your time and you're good to go.  DO IT.  You'll be glad you did.

---

### Post by lovinglinux on 2009-03-07
I also reinstalled Hardy Heron after trying Intrepid. Not a big deal, specially if you have a separate home partition.

---

### Post by ugm6hr on 2009-03-07
If you have a separate /home partition, it is very easy to reinstall Hardy.

---

### Post by stalkingwolf on 2009-03-07
Try rebooting.  When grub starts hit ESC.  select recovery mode.
when it finishes select Fix Broken Packages.  when that finishes
select attempt to fix X.  when that finishes reboot normally.


hope that helps.

---

### Post by fabricator4 on 2009-03-07
A 90 second delay on boot sounds like a system in trouble.  Have a look in the log files and you might be able to see what's gone awry.

Post the relevant bits here and someone may be able to help.  Not me - I'm at the same  point you are except I have two machines - the XP one which I use for work and a 10 year old Celeron with Ubuntu on which I'm trying to learn how to get it functional for my purposes.  It runs through a KVM switch and while Ubuntu is booting I can still work on the XP box.  The two boxes are hardwired to a wireless router which also supports my wife's machine and my laptop, both wireless.  That's two XP machines, one vista, and one Ubuntu, all of which can see each other.

Even better, the stuff that I _can_ do on Ubuntu and batch process, can be done by the box under the desk while I happily work away on the XP machine on top of the desk, or vice-versa.

Alternatives for you are to wait a few weeks for the next version, or try another distribution as has already been suggested.  If you've got time to sort it out you should do so however, otherwise you'll never know what went wrong, if it's going to happen again, or how to fix it next time (if/when).

As far as convincing you about the good things, I think you already know - open source.  I just found out tonight that openoffice word processor appears to be fully compatible with windows .doc files. It never occured to me to try before. Encouraged by this I tried opening a .docx (word 2007) and found moderate compatibility - all the text was there but some graphics and formatting was not.  Then there's WINE, which I believe does have compatibilty with Office 2007 (ie it runs it), but I'm not ready for WINE yet, and hopefully won't need it anyway.

On the bad side: patchy driver support from vendors (eg Canon), configuration problems require you to "go under the hood", and inconsistencies in the user interfaces, even within programs (like the GIMP).

All of the bad bits can be easier with a bit of planning, and the will to learn.  Hindsight is not much good except for kicking yourself with.

Rather than spending thousands on new software that runs under windows (a prospect I'm currently faced with), I'd rather spend it on new hardware like a faster box to run Ubuntu, and a new printer.

Chris.

---

### Post by fidgaf on 2009-03-07
Thanks all.

Cheered up a little. :)

I don't think I will go down the re-install Hardy route just yet particularly as there is a new distro out soon (more hair pulling perhaps). Maybe try that first and then back to Hardy.

I think I've tried the repair option earlier but cannot remember for certain. I will try that option again first.

The details of my 90 sec hang, as far as it got, is in the other thread mentioned in the OP.

---

### Post by oldsoundguy on 2009-03-07
Yep, too many issues with Intrepid .. just little things here and there .. I went back to Hardy also when I updated my motherboard/processor/ram in this box.  Rock solid!  And it LOVES a hyperthreaded processor.  Runs about 30 C cooler than when this board was on a Windows box!  No longer a whole house heater!!

---

### Post by fidgaf on 2009-03-07
Well, what do you know? Getting annoyed can help sometimes. :D

Auto-mount issue seems to be solved with pysdm

```
sudo apt-get install pysdm
```

Then

```
sudo pysdm
```

All a little too deep for me when it ran so checked the boxes for everything shown to run on boot - and they did.



BTW fixing everything fixable/checkable on grub startup. It deleted a few useless files but still has the mystery 90 second hang. :(

---

### Post by oldsoundguy on 2009-03-07
Do NOT know your setup, but I have an issue with an external USB plug in DRIVE on a Windows machine .. IF I attempt to boot with the drive powered up, Windows will not boot.  The moment I turn the drive OFF booting resumes.  Should NOT be that way, but USB IS USB across platforms and you may be having the same type of equipment issue.

Just remember not ALL problems can be laid at the feet of the software.

---

### Post by fidgaf on 2009-04-15
Impatient me ;)

Wiped Hardy Heron completely and installed Jaunty Jackalope (Beta)

Sweeeeeeeet.

All problems solved (so far).

I might be falling in love with Ubuntu again.

:D

---

### Post by paradigm2 on 2009-04-15
> **fidgaf said:**
> 
I don't think I will go down the re-install Hardy route just yet particularly as there is a new distro out soon (more hair pulling perhaps). Maybe try that first and then back to Hardy.

I agree.  Jaunty is pretty solid right now in my opinion.  Far better than previous versions in my opinion.

A lot fo the little problems you are having might also just be configuration issues due to what has changed between versions.  In some ways I think that is almost to be expected.

---

