---
title: "Strange printing problem from Evolution"
date: 2007-09-12
forum: Desktop Environments
---

### Post by mvip on 2007-09-12
I recently migrated over an entire organization from the dark side to Ubuntu. The transition went smoother than what I anticipated with some minor problems. I've managed to solve most of the problems, but I have one problem that I fail to resolve.

When printing certain e-mails from Evolution to a network printer (a Brother MFC-8460N), the printer  prints out an error message rather than the actual e-mail. The code that gets printed looks like this: 
```

Error Name; ioerror
Command; fill
Operand Stack;

```

This code gets printed on the paper, not an error message on the screen. Also worth noting is that the printer works flawless for the exception of the printing of certain e-mails. I've tried to google the error without success.

(The system runs Ubuntu 7.04 (32bit))

---

### Post by mvip on 2007-09-14
This is a really annoying error. I'm really the only one experiencing it?

---

### Post by dcstar on 2007-09-16
> **mvip said:**
> This is a really annoying error. I'm really the only one experiencing it?

Try installing CUPS and see if that changes things.

---

### Post by ndaxar on 2007-09-17
Hi, 

Could you resolve this printing problem? I have the same problem with a Brother DCP-8040, with Ubuntu, Linux Mint and Suse, always in gnome.
I can print, but somtimes I have the errors with evolution, openoffice, etc. And I can't print pdf files or jpg files.

Thank you.

---

### Post by trak87 on 2007-10-26
```
ERROR NAME;
     ioerror
COMMAND;
     fill
OPERAND STACK;
```

I'm getting this problem as well on a networked HL-5250DN with Ubuntu Gutsy. I believe I saw this in Feisty as well. My solution, since the printer is capable of emulating an HP Laserjet, is to use one of the HP Laserjet drivers. 

Additionally, my problem is trying to print an invoice from newegg.com with Evolution. I can print other emails, just not this one. I get the above error. However I can print this same email with Thunderbird. My solution is to install theHP LaserJet 6 Foomatic/hpij driver and whenever the normal Brother BR-Script3 won't work, switch to this driver.

It would appear that the BR-Script3 driver is broken or not handling some error condition.

---

### Post by geoffatmk on 2007-12-14
Hi

You are not alone!  I do not know if it is a recent patch but I ahve now started to have the same problem in evolution.  THe problem is worse as it blocks the print queue and then nothing can print until I clear it.

I am on 7.10 vanilla installation and everything was working fine.  Can't tell exactly when it stopped working but I  can only imagine it is a patch OR because I started to use the print to file and print pdf versions (but I only did that to try to print a document that would not print) so the patch is the best guess.

At the moment I am having to copy emails to OO to print them which is not good.

Help please?

Geoff

---

### Post by geoffatmk on 2007-12-14
Sorry I should have mentioned that I am using an hplj 4050 and the error messages I get are;

1.

ERROR: syntax error
OFFENDING COMMAND:
Then a string of garbage............
Stack:

-mark-
/MyPatternData

2.

ERROR: undefined
OFFENDING COMMAND: G

STACK:
1

Does this give any clues?

Geoff

---

### Post by geoffatmk on 2007-12-14
Hi

Further reseach found this;

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/172550](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/172550)

I swapped to an hpijs driver and mail started printing again.  Give it a go?

Geoff

---

