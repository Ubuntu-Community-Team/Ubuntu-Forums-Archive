---
title: "DVD-RW drive keeps reading/writing by itself..."
date: 2006-08-08
forum: Desktop Environments
---

### Post by Fyda on 2006-08-08
Hi,

I'm bewildered by the odd behaviour from my DVD-RW drive in Ubuntu. Normal CDs and DVDs don't act up, but DVD-RWs (on which I have archived my files) do.

The behaviour is as follows: after I insert the DVD-RW, the system mounts it normally. Nautilus launches, browsing to the mounted disc. As I open and browse through the folders, however, the drive starts to read and write. The *reading* should be fine, but what's with the *writing*?

I close the Nautilus browser; the drive continues working for at least another full minute. I have no idea what it's doing. Listening to the drive, I can hear that it is spinning, stopping, spinning, and stopping the disc repeatedly, while the read and write indicators light up.

This behaviour takes priority over anything else I might want to do; I tell the system to eject the disc, and have to wait until it's done this bizarre ritual before it finally does so. But that is only an annoyance.

The real irritation here, the real problem, is that I can't copy anything from the disc to my HD because of this. I try to copy a file from the disc to ~/Desktop, and after waiting through the ritual (the "Copying a file" dialogue stuck at 0% while it does that), it finally gives me this error message:

***Error "I/O error" while copying "**(FILEPATH HERE)**".***

So, so far it looks like I'd have to boot into WinXP (which I haven't done for at least a month) to get at my files. Which isn't that much trouble, but I'd prefer to fix this issue in Ubuntu. Can anyone please tell me what I'm doing wrong?

---

### Post by computergroove on 2006-08-08
Have you tried to retrieve your data in XP? You might have a damaged disk. Drive could be going bad too. If it works in XP we can look at other things.

---

### Post by Fyda on 2006-08-08
Thanks for replying so quickly!

I'm in Windows XP right now. It has no problem accessing the disc and copying the file to HD for me - there is none of the odd behaviour that I described in Ubuntu.

I guess some background on the disc and drive might help?

The disc was burned using Sonic MyDVD in Windows 98SE, prior to installing Ubuntu and WinXP. (That software was bundled with the burner. Not terrific, but I didn't have Nero on hand.)

The drive is a Lite-On DVD-R/RW burner, which WinXP has identified as the [SOHW-812S](http://www.techwarelabs.com/reviews/storage/liteon_sohw812s/).

I can think of two possibilities, neither of which I know how to confirm:

A) Burning the disc in Windows somehow made it unfriendly with Linux (and potentially other OSes - I have no Mac machine to test this, though).

B) Ubuntu isn't properly configured to handle the disc, for whatever reason.

Strange...

---

### Post by computergroove on 2006-08-08
I have burned data to RW discs before and have had rediculous problems getting another computer to read them. I think that whatever program you use to burn the disk assumes that you will use it (your program) again to access the data and after it writes the data to the disk it leaves it "open" (as in not finalized) for future modifications. I'll bet that thats it. Can you save your data and use Dapper to reformat the disk or better yet get another disk and format it in Ubuntu and see if the strange behavior continues? Post your results.

---

### Post by Fyda on 2006-08-09
Okay, I've taken a fresh DVD-RW disc and burned some of the same files (from the glitchy disc) to it in Ubuntu. Looks like you are right - it's not acting up at all.

Thanks for your help, and sorry for all the trouble - I guess it's not an Ubuntu issue, but rather, a general-CD-burning-software-in-Windows problem. :(

I just wish there were some program or something that would enable Ubuntu (or any other OS, for that matter) to work with weird, proprietary-ish discs like this.

---

### Post by computergroove on 2006-08-09
Heh, they dont work right in the operating system that they were designed for. Hence you are now using linux.

---

