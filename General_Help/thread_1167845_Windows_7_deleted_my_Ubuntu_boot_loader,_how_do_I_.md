---
title: "Windows 7 deleted my Ubuntu boot loader, how do I get it back?"
date: 2009-05-23
forum: General Help
---

### Post by Mashuteichou on 2009-05-23
Basically, its as simple as that.  I loaded Windows 7 because I was curious, beings Vista was worse then Windows 2000, and XP came after, I figured maybe they might of made a good OS for once.  

Once I installed, I played around with it for a few days, noticing a few things changed, but an overall failure again.  So I though, "Well, lets go back to Linux.  Because Linux is my friend."  I restart, and Windows 7 instantly loads.  So out of sheer desperation, I loaded XP because Windows 7 is still glitchy.  I used XP to find a program called EasyBCD which I used to change the boot loader.  

I realized that Ubuntu was considered gone.  I checked the HD, and it doesn't show up in Windows.  But when I used it a partition manager on the Live Ubuntu CD, it showed Windows XP and Windows 7 as being OS, but Ubuntu was just blank.  That is, blank in the idea that there was no record of how to load it.

Then I read some more stuff, and I found out that Windows 7 specifically, (And some said Vista and XP), delete the Ubuntu (any linux) boot loader.   

I found a post on a windows forum, and I tried it, but it didn't work.  It had to do with loading the CD for ubuntu and using the terminal to put the Grub loader into the Ubuntu Partition.  

So, is there anyway to salvage it, or do I have to kill my hard drive and start over, leaving Windows 6 ft under?

---

### Post by chriskin on 2009-05-23
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) 

:)


edit : of course ubuntu wouldn't show up in windows, windows can't even see ext drives if you don't add apps that do it for them

as for the bootloader thing, it is a pain but windows always does it , not just 7

(by the way, you didn't like 7? ok they are not the linux killer they advertised it to be, but they are pretty decent for windows :) )


my solution is by using the cd , but it is by definition better than any advice you will ever get at a windows forum -  the tutorial has worked for me maaany times :)

---

### Post by Mashuteichou on 2009-05-23
Thank you very, very much.  I will go do that as soon as it all prints. ^_^

---

### Post by chriskin on 2009-05-23
> **Mashuteichou said:**
> Thank you very, very much.  I will go do that as soon as it all prints. ^_^

the useful thing is just some lines

Sudo grub
find /boot/grub/stage1 
(it will give a (hdx,y)
root (hdx,y)
setup(hdx)

no reason to print all of that :P

---

### Post by chriskin on 2009-05-23
oh, and if you want to find windows after the installation and the grub won't find it, there is instructions on the same page

---

### Post by Mashuteichou on 2009-05-23
Well, I was hoping they made Windows 7 better then Vista, but its just what my Vista was after I customized it.  The control panel is different again.  Some controls are different...again.  The stupid User control thing that pops up when you open something isnt as annoying, but still an option.   Its just overall disappointing.  (I Didnt even expect much from Microsoft, I mean, all they want is money, and all I want is a user friendly OS.  Which is Ubuntu.  ^_^) 

They might change a couple things, Im not too sure.  The only thing I liked in it was the Network setup stuff.  Its a 100 times easier then XP, and just a redone version of Vista.   All the cool fancy features, like in Vista, are just stupid.  I mean, Ubuntu has better features, easy to use, and for some reason has way, way less resources being used.   For example.  In Vista, the average ram used out of 3, or 4gb, if I used 64bit, was 1.5gb.  Well, thats on the fresh restart average.  After a day, I could have it over 2gb.   XP takes about 400-500mb at start up, and after a couple days maybe a gig.  Ubuntu is about the same.    So Ubuntu is on par with Vista, yet runs easy like XP.   There is something wrong with that picture.   ^_^

And now to do the bootloader stuff.

---

### Post by Mashuteichou on 2009-05-23
I always print any instructions I use.  Chances are, I will have to redo windows in a couple days because its, you know, windows.  So I will have to do it again.  So I just print, staple, and put in my massive "How to fix what Microsoft breaks" folder.  And yes, I do have that.  xD

---

### Post by chriskin on 2009-05-23
memorizing always worked better for me, can't say i have an organized style of storing folders 

if you have any problem with the commands, tell me (/us)

---

### Post by lindsay7 on 2009-05-23
I looked at the instructions that Chriskin gave you and there should be one more line after "setup(hx)"

You should add, "quit".

---

### Post by chriskin on 2009-05-23
> **lindsay7 said:**
> I looked at the instructions that Chriskin gave you and there should be one more line after "setup(hx)"

You should add, "quit".


yeah true, sorry :$

but he got it from the site i directed him to , so no harm :)

---

### Post by lindsay7 on 2009-05-23
Chriskin, No prob, just wanted it to be clear in case some got hung up if the used this post to fix their problem. I figure the OP got it right anyway.

---

