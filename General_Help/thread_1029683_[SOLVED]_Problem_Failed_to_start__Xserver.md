---
title: "[SOLVED] Problem: Failed to start  Xserver"
date: 2009-01-03
forum: General Help
---

### Post by cactusgal on 2009-01-03
First, let me say I know this problem has been posted before. I've scoured all the references and tried everything I found.

I'm quite new to Ubuntu (any Linux, for that matter), having dabbled with it a little in virtual machines since 4.10. Now, since I build and up-grade my own PCs and really don't much like the bugginess and proprietary nature of Windows, I have a spare PC so I'm delving more into Ubuntu especially since I discovered the Studio edition.

At first everything was running fine but I wasn't very happy with the graphics effects. I have an ATI Radeon 9250 Pro and understand, from my research, that Ubuntu can have problems with it. So, thrilled that installs are so much easier now (couldn't ever seem to figure that out in the past) I thought I'd look for another graphics driver set. Guess I screwed up because since I installed it (and can't even remember what it was or find it again) I get this message 'Failed to Start X server'.

sudo dpkg-reconfigure xserver-xorg gives me only a keyboard to reconfigure

sudo apt-get install xserver-xorg tells me I have the latest version

sudo dpkg-reconfigure -phigh xserver-xorg really does nothing either as I have to proceed somewhere from there and not really sure where/how. I just end up going in circles and accomplishing nothing

One article I read suggested running a live disk (I have 8.04) and replacing the xorg.conf on the hard drive with the one on the disk. I'd really like to try that but it won't let me and I can't figure out how to get permission. There is quite a difference in content between the one on my hard drive and the one on the disk.

I really don't want to do a new install unless I absolutely have to and I've learned so much already by trying all these things. I've spent a few years messing with Windows to the point of breaking it a few times and always managed, with a lot of research and experimentation, to fix it and I want to be able to do the same with Ubuntu so any help/suggestions would be greatly appreciated.

Regards,
cactusgal

---

### Post by cactusgal on 2009-01-03
Well, sorry to have bothered anyone but it looks like I've solved my problem. I researched how to edit xorg.conf in the console and that didn't work so I thought, what if I use: sudo apt-get remove (instead of install, just taking a chance here) xserver-xorg and that worked to remove the whole thing then: 'sudo apt-get install xserver-xorg' and it worked like a charm! Everything is back to normal now. Hope maybe this helps someone else who might be having the same problem.

Regards,
cactusgal

---

### Post by stderr on 2009-01-03
Hi cactusgal, welcome :)

Glad you got it sorted. Let us know if you run into any other problems!

---

### Post by cactusgal on 2009-01-04
Thanks. I rather amazed myself that it worked. I was really just guessing as I don't know many commands yet. At least it's easier to figure out than DOS.

Guess I should have marked this 'Solved'

Regards,
cactusgal

---

