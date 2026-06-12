---
title: "RAM issue"
date: 2006-08-09
forum: Desktop Environments
---

### Post by djfreekshow on 2006-08-09
I am fairly new to linux.  I say this up front because this is probably a stupid and simple fix.  So, here's my issue:

I have recently transplanted RAM from one machine to another, both running Dapper.  The one that had 2GB but now has only 1 will no longer boot.  If I am post-GRUB, I am at the point where it says "Uncompressing Linux... Ok, booting the kernel." and it has been hanging there for literally two days now.  I am not sure if there is a simple fix with gedit or something, but I would greatly appreciate any help you can provide.  I get no errors, and have noticed no hardware failure at all.  I checked and couldn't find a post at all like this, so if I'm repeating someone, please link me, as search turned over nothing good.  Thanks for any help.

---

### Post by RESmonkey on 2006-08-09
1. Are you 100% positive that the 2GB comp ran with 2gb?  It could be that that comp only ran on one of your sticks, the other incompatible (ecc/register) and you may have taken out the good stick.  Just a suggestion.

2. Wrong slot?  I don't know if there is a primary slot or anything like that.

Just trying to help, I'm new as well.  Funny thing, I can't get my floppy drive to work : P

---

### Post by djfreekshow on 2006-08-09
Well, I would look into those, but Memtest tells me not to.  The machine is used to running only 1GB, but while one of my little servers was waiting for RMA parts, I threw the RAM in for a little boost, and installed Ubuntu during this time.  I am sure all four sticks are 100% good, and it did identify 2GB in both BIOS and Ubuntu.  I know this beacuse of memtest and because the RAM is now back in an Ubuntu server running well.  As for the primary slot issue, I am 100% sure it is not in the wrong slots, but I will check just to be 120% sure.  I think this is a config file error, just like how my server won't boot without whining if I pull out a HDD cause the mounting is corrupt without the disk there.

---

### Post by RESmonkey on 2006-08-09
Sorry, I don't know anything further :o but I can tell you (I'm confused now) that motherboards have a limit of RAM size.  Mine only supports a gig.

I guess you could put back the gigstick in the first computer, and wait for RMA parts?  Do you really need the boost, like, is this a server that has a need for it?

---

### Post by djfreekshow on 2006-08-10
I'm sorry, maybe I should have specified before.  The desktop that had 2GB has 4 DIMM slots, and uses all four with a max of 4GB.  The server has 2 slots with a max of 2GB, and it uses both slots.  I have (among other things) four sticks of RAM here, each containing 512MB.  The server only runs on 1GB right now, and that 1GB was in my desktop while I was waiting for a new PSU for the server.  No RAM is bad, no mobo is bad, and no OS is corrupt.  I am just trying to figure out why removing RAM would stop me from booting into Ubuntu (even recovery console).  I should have specified a lot more before, my bad.  Perhaps someone else has an idea, but thanks for the help so far.

---

### Post by blueturtl on 2006-08-10
:-x

---

### Post by blueturtl on 2006-08-10
I have added and removed RAM all the while having Ubuntu installed. This cannot be a RAM issue, something else is triggering your problem. I cannot help more, since I don't know your system spesifics, but I advice you to take a logical path in this: what does adding or removing memory affect in your system? Has the BIOS been reset accidentally altering some setting? Maybe some other changes were made to the system prior to the removal of RAM that you do not account as possibilities for the system not booting?

Having done tech support for quite some time I know sometimes these things can be caused by the things we'd least expect like a disconnected wire (duh) or some incredible coincidence (like this one time on Windows I had to disable a DOS-mode Anti-Virus program to get the customer's tv-tuner to work, logical huh?)...

---

### Post by djfreekshow on 2006-08-10
Come to think of it, there is one thing (I am a tech as well, so I don't usually do the stupid small things like loose wires, etc, but they happen every now and again) I may have done, I think I threw in an old NTFS drive on the other SATA channel. The boot order is fine, this I know, but I never installed NTFS support on the OS before I rebooted it, and my fstabs have always hated me.  My server won't boot because of the same issue right now, it's just a hassle to remove it from the racks.  I'll give that a try.

---

### Post by djfreekshow on 2006-08-10
Nope, didn't fix it.  I unplugged the other HDD, and it still hangs at the same spot.  I don't know why it would do this, but no other changes have been made.

---

### Post by blueturtl on 2006-08-10
I'm having the strangest sence of deja vu. I have a vague memory in my head that there was a bug in Ubuntu (or possibly GRUB) involving spesificly hard-disk device order and booting, just like in your case, adding a hd would result in the device order changing or something like that which in turn would result in GRUB not finding the disk with the system on it...

Then again you said the boot order was fine (you can always check though, hit esc to stop grub from automatically continuing and C to edit a selected entry).

Also have you tried to see if the LiveCD/InstallCD boots on the system (if for no other reason then for checking that the problem is indeed with the installed system)?

Wish I could be of more help.

---

### Post by djfreekshow on 2006-08-12
OK, so since my Live/Install CD is trapped in my server DVD burner, I have tried to boot into an alternate boot in GRUB.  First of all, my GRUB boots show up fine, and when I try to boot recovery console mode for 386, the last line in the debug is 

```
[17179572.404000] ACPI: Looking for DSDT ... not found!
```

Now mind you this, it always said that before when I booted recovery console, it just hangs there now.  Before it would pause a moment, then continue to spew out verbose boot code until it produced a pretty GUI environment.  I'm not sure what the issue is, but it's not a RAM issue.  If I find time, I will do two things.  First, I will re-insert the RAM and try to boot it without changing anything else.  If that fails, I will kidnap my install CD from the server to use here and see if I can get a live boot.  Still puzzled.

---

### Post by djfreekshow on 2006-08-13
Well, I think I have figured it out.  I completely forgot about this little detail...  So, here's my solution:

I went to boot with the LiveCD, and it was hanging at the Uncompressing Linux screen again, so it clicked.  I forgot that I had plugged my USB mass storage device (a 10-in-1 card reader) back in.  My BIOS has settings to control this, and they must be setup wrong.  I am tweaking it to get it to work now, and we'll find out if it'll boot sooner or later.  I will update later on tonight.

---

### Post by sdebo on 2006-09-02
Boot order issues would churn errors on screen to this effect.
If it just hangs, and you only changed RAM it must be BIOS and RAM related.
Changing RAM does not effect Ubuntu (tried it)
Possibly it could be your BIOS settings not matching your remaining RAM. Timings and other settings do play funny tricks.  Are all your RAM sticks identical?  Maybe the ones you left in require different BIOS settings.

---

