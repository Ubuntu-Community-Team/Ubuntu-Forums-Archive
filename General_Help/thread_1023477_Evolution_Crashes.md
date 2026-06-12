---
title: "Evolution Crashes"
date: 2008-12-27
forum: General Help
---

### Post by Orfintain on 2008-12-27
My Evolution seems to be randomly crashing not sure what to do about it. Other than switch back to thuderbird

---

### Post by Orfintain on 2008-12-28
I realized I can re-create the crash by clicking save draft and then closing the draft immediately afterwards before the save operation goes all the way through.

I was experiencing bug # 27014 and I applied a fix from this website

[http://daveshuck.instantspot.com/blog/2008/01/16/Fix-for-Evolution-email-client-error-Summary-and-folder-mismatch-even-after-a-sync](http://daveshuck.instantspot.com/blog/2008/01/16/Fix-for-Evolution-email-client-error-Summary-and-folder-mismatch-even-after-a-sync)

which I had modified for drafts instead of inbox (twice i ran that fix before this worse problem)

I tried reinstalling evolution and that didn't help either

---

### Post by dcstar on 2008-12-28
> **Orfintain said:**
> 
.......
I tried reinstalling evolution and that didn't help either

And exactly what version are you using?

---

### Post by Orfintain on 2008-12-28
> **dcstar said:**
> And exactly what version are you using?

2.24.2 

Just whatever was in the repos

---

### Post by Orfintain on 2009-01-03
bump*

---

### Post by datakid on 2009-01-04
> **Orfintain said:**
> 2.24.2 

Just whatever was in the repos

I can confirm this - random crashes. Can't really use evolution long enough to see a pattern/ :|

Only one IMAP account.

---

### Post by Orfintain on 2009-01-14
Well I'm glad it's not just me.

I've been considering filling a bug report.. although, I'm afraid it would take all day to get in the proper format ect..

---

### Post by dcstar on 2009-01-15
> **Orfintain said:**
> Well I'm glad it's not just me.

I've been considering filling a bug report.. although, I'm afraid it would take all day to get in the proper format ect..

The first thing to do is close Evolution and rename you (hidden) .evolution folder, then restart Evolution so it creates a fresh profile.

You will have to set your accounts again, and you can copy your existing data from the respective places in the renamed directory.

Doing this will eliminate any corruption in your profile that may have been causing the problem - if it doesn't then it may well be in the binaries which need a bug report.

---

### Post by Orfintain on 2009-01-15
thanks for replying dcstar

"You will have to set your accounts again, and you can copy your existing data from the respective places in the renamed directory."

Should I do the above with the backup settings command or what that defeat the purpose of making a new profile?

If I need to manually copy, what do I need to avoid coping to keep the fresh profile, or should I just copy the entire contents? (I need some contents the mail and address book, and preferable the signatures and calender as well. Do I just want the locals and not the views?)

---

### Post by Orfintain on 2009-01-16
I tried making a fresh profile and it didn't fix the problem. Thanks for trying though.

---

### Post by Orfintain on 2009-01-21
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/319491](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/319491)

The Bug report is listed above, hopefully this will generate some more response on this issue. 

If there is a guide to running a backtrace or valgrind or something I could try to gather more information for bug report.

---

### Post by RoboRutt on 2009-01-21
Heya Orfintain, 

I am with you... Just upgraded (via format/reinstall) from my very old gutsy to Intrepid & have had so many problems that my desktop is un-usable.

Evolution crashing radomly & continuously is one of them.

Will be checking in & very keen if anyone has any hints on where to track down & correct these problems :)

oh - thanks in advance to the ubuntu collective genius !  :)

---

### Post by Orfintain on 2009-01-21
Mine started mysteriously working again. After a reboot. Then stopped working after firefox crashed

Ok it seams to be something that fixes with reboot and is only problemmatic after something else happens possible a firefox freeze and then force quit and firefox process end.

Is there anyway to fix your memory or something w/o rebooting?

---

### Post by Orfintain on 2009-01-22
I rebooted and it won't work again, I've been trying everything to determine what made it work that one time and I have no idea 
alltray? mo-block? compiz?

I ran evolution in terminal and this message popped up a dozen times or so when I opened a draft message that can't be normal anyone have an idea?

(evolution:7486): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

---

### Post by Orfintain on 2009-01-22
I enabled apport and refiled the bug 

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/320326](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/320326)

---

### Post by Orfintain on 2009-01-23
I'm trying to file this bug and I need to do a back trace and I have having trouble getting the debugging symbols installed it
following this guide
 [http://wiki.ubuntu.com/DebuggingProgramCrash](http://wiki.ubuntu.com/DebuggingProgramCrash) 
I get the this point and 

"username@jahbuntu:~$ gpg --check-sigs 428D7C01 # signed by key of Martin Pitt
pub   1024D/428D7C01 2008-09-02
uid                  Ubuntu Debug Symbol Archive Automatic Signing Key <ubuntu-archive@lists.ubuntu.com>
sig!3        428D7C01 2008-09-02  Ubuntu Debug Symbol Archive Automatic Signing Key <ubuntu-archive@lists.ubuntu.com>
sub   2048g/A2C2A7A5 2008-09-02
sig!         428D7C01 2008-09-02  Ubuntu Debug Symbol Archive Automatic Signing Key <ubuntu-archive@lists.ubuntu.com>

1 signature not checked due to a missing key"
Then I get a bunch of ..
"No symbol table info available."

---

### Post by Orfintain on 2009-01-29
The kernal update fixed this issue

---

### Post by Orfintain on 2009-01-31
well kernal 11 seems to have brought it back after it ran for awhile, I tried booting kernal 9 but that didn't help.

---

### Post by Orfintain on 2009-02-06
Hmm there is a "fix released" how to I get it?

[https://bugs.launchpad.net/ubuntu/+source/gtkhtml3.14/+bug/274823](https://bugs.launchpad.net/ubuntu/+source/gtkhtml3.14/+bug/274823)

---

### Post by gabak on 2010-06-03
This bug has been reported on Launchpad, but only 4 people (including me) have said it's a problem. If everyone who's complained in this thread went to the site, clicked on the 'does this affect you' and said 'yes', it might be given higher priority for a fix.
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/584183](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/584183)

[http://ubuntuforums.org/showthread.php?p=9407284#post9407284](http://ubuntuforums.org/showthread.php?p=9407284#post9407284)

---

