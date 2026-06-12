---
title: "Installing mobo drivers/.run files not working"
date: 2005-06-05
forum: Desktop Environments
---

### Post by Curlydave on 2005-06-05
I'm following the instructions to install the nvidia nforce chipset drivers. I type in "sudo sh /home/david/Desktop/NFORCE-Linux-x86-1.0-0301-pkg1.run", but it tries to open it in gedit and errors me up. How can I fix this? Thanks!

edit: weird, i did it again and it works. NVM!

edit again: Now it won't install because it says I don't have a precompiled kernal interface to match my kernal. It then tries to install one, but can't find a source tree for my kernel. What's up?

edit again: I rebooted into my 386 kernal instead of K7 and it works now. Odd. What's the difference between the two, practically speaking. I actually have an AMD cpu... you'd think K7 would be more appropriate.

---

### Post by ltmon on 2005-06-05
First up... I'm not sure you really need to install the NForce drivers, I've been using an nForce2-gt for a few years and have never bothered.  But if there is a significant advantage to using them, let me know :)

The difference between the 386 kernel and the k7 kernel is simply that one is compiled with all the extra bits and pieces that k7 allows and 386 doesn't.  This should mean that the k7 kernel won't work on and 386 pc, but will give you a performance boost on an AMD athalon.  There is also a 686 kernel, which I believe will work on a p4 and an athalon.  Some have reported that the 686 kernel is marginally faster.

As for not being able to find the source for your k7 kernel, I'm confused.  The source should be the same for both kernels.  Maybe something in the way Ubuntu is set up makes the source not found when using a non-default kernel??

---

### Post by Curlydave on 2005-06-05
Thanks for the info. I just reformatted. (I'm in the experimentation stage of linux) One of the first things I did was then install the K7 kernal, reboot into it, and delete the 386 kernal to avoid confusion. I did not bother installing the nforce drivers, as I found they are just for networking and and audio.

Why I wanted them is because in windows if you don't have them, your 3d performance is poop. My 3d performance in Linux is, coincidentally enough also poop, so I thought that this might have been the problem. Oh well, I guess not.

---

