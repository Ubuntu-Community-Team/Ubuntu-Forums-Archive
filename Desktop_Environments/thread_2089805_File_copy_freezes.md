---
title: "File copy freezes"
date: 2012-11-30
forum: Desktop Environments
---

### Post by Paul A C on 2012-11-30
I have just installed Lubuntu 12.10 on an old NEC Powermate.
 
The issue I have is I cannot copy files over the Network to either of my hard disks in the machine. The first file (or 2) copy, then the copying freezes. I have tried the following:-
 
I am copying from another Lubuntu PC here is a summary of what does and does not work:-
1.)Using PCManFm to sda3 (Reiser) Fail (File 1 14K)
2.)Using PCManFm to sda2 (ext4) Fail (File 1 0bytes )
3.)One file at a time Pass Reiser OK ext4 OK
4.)Using Nautilus to Reiser Fail 15 files created, some 0 bytes
5.)Using Nautilus to Ext4 Fail 9 files created, some 0 bytes
6.)From USB to Reiser OK almost instant
7.)Replace Network card (3Com) with NE2000 Compatible still fails after 1 file.
8.)Using CP command from terminal. Same error, hangs during second file
9.) copy **to** this PC from the other PC Pass, works just fine.
The fact that the USB copy works 'seems' to indicate a Network issue, but I downloaded updates all OK, and I have used BBC Iplayer to view/listen, and as test 9 above shows, I can copy to the PC from another one, it is only copying from another PC to this one that does not work! I guess that is a work-around of sorts, but hardldy satisfactory.
 
Installed version 12.04 of Lubuntu with identical settings on the same PC
 
Filecopy using PCManFM (default file manager) worked perfectly. Looks like a 12.10 specific issue. No one else seen it?
 
I wanted to try 12.10, because I understand that a long standing problem in DOSEMU is resolved in this. Currently I am stuck at 10.4 (which has other issues).

---

### Post by SteveDee on 2012-12-01
> **Paul A C said:**
> ... I can copy to the PC from another one, it is only copying from another PC to this one that does not work! ....

No, you are not alone.

I have the same issue, and now you have reminded me, I'll take another look at this.

I suspect its a permissions thing. I notice that the file manager Permissions > Access Control has changed from showing: Owner/Group/Other/executable (in earlier versions) to: View Content/Change Content/Execute in the 12.10 version.

---

### Post by SteveDee on 2012-12-01
I've posted a bug report: [https://bugs.launchpad.net/ubuntu/+bug/1085394](https://bugs.launchpad.net/ubuntu/+bug/1085394)

---

### Post by Paul A C on 2012-12-02
Thanks Steve for confirming this, and reporting it as a Bug.  I'll try to add my name as 'affects me too' on the Bug.

Not sure if it is permissions though, since:-
1.) the first file copies fine, and I can copy as many as I like if I do it one at a time.
2.) I can copy the same files all at once if I do it via USB

Odd.

I am now installing 12.10 on another computer (raided the garage and my spares cupboard and found enough working bits) Will be interesting to see if I get the same problems.

Install completed, and file copying works fine!  Now install updates and see if that breaks it!

---

### Post by Paul A C on 2012-12-13
Unfortunately, I am still seeing this issue, tried to copy several hundred files in about a dozen directories/sub directories, (using drag and drop in PCFMan) and froze at about 4%.

---

### Post by SteveDee on 2012-12-14
> **Paul A C said:**
> Unfortunately, I am still seeing this issue...

There is something very odd about network comms with 12.10.

Sorry if this turns out to be un-related. But if I attach an external drive to a "server" (not 12.10, say 11.xx, see my notes: [http://captainbodgit.blogspot.co.uk/2012/12/external-drive-network-share-on-linux.html](http://captainbodgit.blogspot.co.uk/2012/12/external-drive-network-share-on-linux.html) ), I can transfer individual text files to it from a remote 12.10 "client". But if I try and open them with a text editor from 12.10, the editor hangs/freezes. 

I can't help thinking there are files missing from 12.10.
I've been through this before, and its quite time consuming comparing files installed on 2 different version of Lubuntu. I don't have time right now, but if anyone wants to try it, here are some tips.

You need a fairly clean install of the previous version (12.04) with applications removed (if possible) to make comparison easier (this may help: [http://ubuntuforums.org/showthread.php?t=1966641](http://ubuntuforums.org/showthread.php?t=1966641))

List all packages and save to file. In a terminal:-
```

dpkg --get-selections > /home/steve/myPackages.txt

```

You can paste the list from this text file into a spreadsheet along with the list from a 12.10 system.

Its then a case of looking for things in 12.04 that are not in 12.10. You can use synaptic package manager to check descriptions of any likely candidates.

You should also use synaptic to add/remove packages that you think may affect networking, as a record is automatically kept via the "History" feature.

---

### Post by Paul A C on 2012-12-14
Thanks for your suggestions, but as you say not anything quick to try, and far from certain it would provide the answer.  What surprises me most is that no one else seems to report this...so is it likely that it is specifically a Lubuntu thing?  (But don't you use regular Ubuntu?)
 
My gut feeing is that it may be a Samba issue, but I see no posts on Samba related forums either.
 
I am debating trying another distro, Mint perhaps, or just a basic LXDE desktop install and add the packages I need.
 
I don't mind helping trouble shoot, but in the end I want a PC that works (and copying files isn't really optional).
 
(Issues I've had since 10.4 include problems with printing (CUPS related), and DOSEMU.  This version fixes CUPS/Printing, Flash now works (broken in my 10.4) and there is a just about acceptable workaround for what I want out of DOSEMU.  But being unable to reliably copy files, I just couldn't believe it.)

---

### Post by Paul A C on 2013-01-13
Now working fine...
Ended up re-installing 12:10 from scratch (because I messed up flash and some other stuff), and did an initial update, and I have just copied several thousand photos from a Windows share, and a few hundred files from a Linux share.

---

### Post by Paul A C on 2013-01-13
Is there a proper way of marking a thread solved?

Blessed if I can find it;)

Typical, after posting, spotted it, seems a bit hidden to me (under thread tools)

---

### Post by TPirog on 2013-03-07
Why dos this say SOLVED when there doesn't seem to be a Solution? What am I missing?

---

### Post by Paul A C on 2013-03-07
> **TPirog said:**
> Why dos this say SOLVED when there doesn't seem to be a Solution? What am I missing?

See post of 13 Jan.  Re-installing, and applying all upgrades seems to have (more or less) fixed this.  I say 'more or less' because since then I have had copies of large numbers of small files occasionally freeze part way through, but much less often than before updating at about 13 Jan?

[COLOR=#000000]TPirog, are you still having problems?  Have you tried applying all updates recently?

Paul[/COLOR]

---

### Post by TPirog on 2013-03-07
Ignore post

---

### Post by TPirog on 2013-03-07
> **Paul A C said:**
> See post of 13 Jan.  Re-installing, and applying all upgrades seems to have (more or less) fixed this.  I say 'more or less' because since then I have had copies of large numbers of small files occasionally freeze part way through, but much less often than before updating at about 13 Jan?

[COLOR=#000000]TPirog, are you still having problems?  Have you tried applying all updates recently?

Paul[/COLOR]

[COLOR=#000000]Thanks for replying.[/COLOR]

[COLOR=#000000]As far as I know I have installed all updates. I run Software Updater and it says my software is all up to date. is that what you mean?[/COLOR]

---

### Post by TPirog on 2013-03-07
> **Paul A C said:**
> See post of 13 Jan.  Re-installing, and applying all upgrades seems to have (more or less) fixed this.  I say 'more or less' because since then I have had copies of large numbers of small files occasionally freeze part way through, but much less often than before updating at about 13 Jan?

[COLOR=#000000]TPirog, are you still having problems?  Have you tried applying all updates recently?

Paul[/COLOR]

Reinstalling doesn't seem like a viable option as I just installed the OS yesterday and I got it working perfectly other than the copying issue. Other than that I am delighted with it.

---

### Post by Paul A C on 2013-03-08
Yes, as far as I can see you must have the most up to date software then, so I am at a loss to know what is the cause of the problem.  I suggest you visit this bug report: [COLOR=#000000] [/COLOR][https://bugs.launchpad.net/ubuntu/+bug/1085394](https://bugs.launchpad.net/ubuntu/+bug/1085394) and add your name to it as 'it affects me'.  The more people that are affected by something the more likely it is that it will be fixed.

Out of interest, is the hard disk you are using a fairly old/slow one?  Mine is, and I am wondering if it is a sort of time-out issue.

P

---

### Post by TPirog on 2013-03-08
> **Paul A C said:**
> Yes, as far as I can see you must have the most up to date software then, so I am at a loss to know what is the cause of the problem.  I suggest you visit this bug report: [https://bugs.launchpad.net/ubuntu/+bug/1085394](https://bugs.launchpad.net/ubuntu/+bug/1085394) and add your name to it as 'it affects me'.  The more people that are affected by something the more likely it is that it will be fixed.

Out of interest, is the hard disk you are using a fairly old/slow one?  Mine is, and I am wondering if it is a sort of time-out issue.

P

My Mac has an SSD. It's a core 2 duo, with 8 GB ram and the SSD. It flies in all respects except when I am copying data from Windows.

---

### Post by Paul A C on 2013-03-08
Your setup seems very different to mine.  You say you have installed Lubuntu on a Mac?  Also you have an SSD.

I wonder if you would do best to start another thread.  I doubt many will look at this one since it is solved (for me), and I am certainly at a loss of what you should try next.

---

