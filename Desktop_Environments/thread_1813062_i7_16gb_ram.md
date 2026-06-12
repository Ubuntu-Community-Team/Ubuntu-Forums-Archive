---
title: "i7 16gb ram"
date: 2011-07-27
forum: Desktop Environments
---

### Post by mandza on 2011-07-27
hi everyone,
i have a laptop:
i7 processor
16GB RAM DDR3
1.5GB Ati radeon.

which ubuntu i need to install? is it metter 32 or 64 bit? like on windows that 32 bit dont support ram over 3.5GB.
please any help.

---

### Post by varunendra on 2011-07-27
I'd suggest Ubuntu 10.04.3 32-bit with PAE kernel. It would have the stability of 32 bit, and PAE will allow you to use upto 64GB of RAM (see [here]("https://help.ubuntu.com/community/EnablingPAE")).

I think PAE automatically gets installed during installation if you are using 4GB or more RAM. If not you can install it manually from synaptic. For a general discussion on this, have a look at comments on this page: [http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

However, if you are going to use mostly some particular applications whose 64-bit stable versions are available, and you are not having trouble with other, 32-bit apps, 64 bit will definitely give you much better performance. So it is recommended if you get all your hardware working out-of-box, and do not need to manually install 32-bit drivers, and other 32 bit apps are running just fine. But be informed - stability of drivers/applications IS an issue with 64-bit desktop version for larger segment of users.

---

### Post by TBABill on 2011-07-27
> **varunendra said:**
> But be informed - stability of drivers/applications IS an issue with 64-bit desktop version for larger segment of users.It is? Not since Ubuntu 9.10 and earlier have I seen issues with users on 64 bit systems. I only run 64 bit on all my systems and have yet to see an issue that 32 bit would handle better. With the powerhouse of a system the OP has listed there is no way I'd suggest 32 bit over 64 bit. 
 
Think of it this way...even on Windows it'd come with a 64 bit version due to the large amount of RAM and the PAE has been shown by tests on Phoronix to be slower than the 32 bit kernel while the 64 bit is faster on every test :)

---

### Post by varunendra on 2011-07-27
> **TBABill said:**
> It is? Not since Ubuntu 9.10 and earlier have I seen issues with users on 64 bit systems. I only run 64 bit on all my systems and have yet to see an issue that 32 bit would handle better. With the powerhouse of a system the OP has listed there is no way I'd suggest 32 bit over 64 bit. 
 
Think of it this way...even on Windows it'd come with a 64 bit version due to the large amount of RAM and the PAE has been shown by tests on Phoronix to be slower than the 32 bit kernel while the 64 bit is faster on every test :)

Wow, then I guess it's time for me to shift 'MY' ''larger segment of users' to the other side of the coin with your experience! :)

I mostly take interest in network related issues, and most of them are wifi related. In those issues, whenever there's a combination of 64bit + proprietary driver, it mostly results into minor to major problems like frequent disconnection or slow speeds. But here I'd like to clarify that I'm not very frequent on the forums since 10.04. But still, whenever I pick some wireless issue thread which has 0 to 2 answers only (after many hours or even days), and this combination a factor, there are these common problems.

Not only wireless drivers, this is perhaps a problem with flash and wine also (32 bit versions only?). But this kind of experience of yours is now making me think that perhaps I should do my homework again before suggesting anyone on this issue.

By the way, I myself have installed Mint 11 KDE 64 bit on some desktop PCs (Phenom II X2 555BE, 2GB DDR3, 1GB ATI graphics, with no wifi), but have practically experienced no noticeable performance gain using default apps supplied with the distro. Maybe heavier GUI of KDE is the reason. And there is that flash issue (black screen in full screen mode).

That's why I feel more comfortable with 32 bit. But given your experience, I'll try to get more and more first hand experience with 64 bit.

Thanx to anyone who showed courage to read this all ! :D

---

### Post by TBABill on 2011-07-27
My apologies if my message came across in any way derogatory. What I meant to imply was that the 64 bit concerns are generally applicable to older releases and past versions of Adobe Flash. Current systems, apps, drivers and Flash/Java are sufficient to handle video and flash and system performance without degradation in either 32 or 64 bit. With specs like an Intel Core i7 CPU and 16GB RAM, that system is more than capable of running at very high speeds on anything you throw at it and 32 bit would just limit what the machine is capable of. 

Again, if feelings were hurt over the wording of my previous post, that was not my intent. I have installed and assisted with support on many machines from old to new, low power to high, and I try to assist where I can with wireless, installation and other issues users face. I just haven't encountered any issue where 64 bit was a limiting factor to any aspect of system performance related to video, wireless or desktop environment.

---

### Post by varunendra on 2011-07-28
Oh no! I wasn't hurt at all, nor was I trying to establish anything. :)

I was just trying to stand corrected and state that my opinion was based on earlier experience which may not be relevant now.

There's only one example (actually 12 PCs with same hardware and OS) I have of a new hardware + 64-bit OS which I mentioned in my previous post, in which I experienced the flash problem and no performance gain. So it made me think that perhaps those older problems with 64 bit apps still exist. But it is quite possible that the flash problem was graphic card related rather than anything to do with 32 vs 64-bit (I didn't try to troubleshoot it as it wasn't important then), and the lack of performance gain was perhaps the result of heavy KDE environment.

So neither I was hurt, nor was I trying to contradict you. On the contrary, I'm convinced with you as you clearly stated that you are in regular touch with newer 64-bit installations. I still have access to all those 12 PCs, and maybe sometime I'll try out ubuntu 64-bit on some of them to compare its pros and cons (if any) myself.


Hope the length of my post didn't give a wrong impression this time! ;-)

---

