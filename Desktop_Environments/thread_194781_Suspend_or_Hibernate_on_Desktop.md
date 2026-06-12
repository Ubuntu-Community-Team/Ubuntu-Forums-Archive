---
title: "Suspend or Hibernate on Desktop"
date: 2006-06-11
forum: Desktop Environments
---

### Post by matthis on 2006-06-11
Hi, there has been already some threads on this, but none of them solved my problem. I would like to suspend or hibernate by desktop computer; but neither works. Suspending works in windows so I think the hardware is ok.
Here is what happens:
- suspend: suspending seems ok, the power led blinks as it does in windows suspend, but at resume I see the bios logo and then nothing, and the power led is still blinking as if it was in suspend mode.

- hibernate: on reboot, after "mounting root filesystem" I get scrambled lines, and then nothing at all.

I have tried to add resume=/dev/hda5 (my swap partition) to kernel option in grub, but its not any better. 

Thanks for any help;

---

### Post by mority on 2006-06-13
I have the same or at least a similar problem. When I hibernate my desktop system it goes down properly but when I switch the computer on again there's just a blank screen after "mounting root filesystem". I found out that I am able to connect via ssh to the system after that, so it seems the system comes up but there's some kind of display problem, I don't know.

If that matters to someone: I have a [ASRock K7S8X mainboard](http://www.asrock.com/product/K7S8X%20R3.0.htm) in this machine.

I would very much appreciate any hints for further investigation :)

---

### Post by pellgarlic on 2006-06-14
**if you have an nvidia card**: if you have the "nvidia" drivers installed (as opposed to the "nv" drivers which ubuntu installs by default) they can apparently cause problems with the "resume" half of hibernation.
[B]
whether you have an nvidia card or not[/B]: "suspend2" seems to be generally more effective than the default, built-in hibernate function. you could try installing and using that instead.

---

### Post by matthis on 2006-06-14
Thank you very much for you reply, I indeed have an nvidia card with nvidia driver. I will give suspend2 a try and report here.

---

### Post by mority on 2006-06-14
[QUOTE=pellgarlic]**if you have an nvidia card**: if you have the "nvidia" drivers installed (as opposed to the "nv" drivers which ubuntu installs by default) they can apparently cause problems with the "resume" half of hibernation.
[B]
whether you have an nvidia card or not[/B]: "suspend2" seems to be generally more effective than the default, built-in hibernate function. you could try installing and using that instead.[/QUOTE]

Thanks for your reply!

Yeah, I have a nvidia card too :(

Will I have to install suspend2 by hand? 'aptitude search suspend' did not give me any results (yes, I have universe and multiverse in my sources.list).

---

### Post by pellgarlic on 2006-06-14
unfortunately, installing suspend2 is not exactly a simple procedure - it involves patching the kernel (although that may sound scary to a linux newcomer - i know it does to me - it apparently is not too difficult, and as long as you find a good guide, and follow the instructions carefully, it should be possible to safeguard against screwing up your system. usually this involves keeping a copy of your current kernel available and bootable, should the new one not work. the instructions for installing suspend2 can be found here:

[http://www.suspend2.net/HOWTO-2.html#ss2.3](http://www.suspend2.net/HOWTO-2.html#ss2.3)

i am not quite ready to tackle the above procedure, as i am fighting with my alsa drivers and nvidia drivers just now, which are vital for me, (and which seem to be messing around with my kernel also), while hibernation would just be quite handy, but not vital.

there are, however, other ways of trying to get hibernation to work:

[http://enterprise.linux.com/article.pl?sid=06/05/24/1716222](http://enterprise.linux.com/article.pl?sid=06/05/24/1716222)

[https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend](https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend)

i can't vouch for whether any of the other methods will work, but they're probably worth trying before going down the more daunting kernel-patching route.

---

### Post by mority on 2006-06-14
Thanks so much for your effort, man! I will try the two links and probably the suspend2 thing too as soon as I have some time spare and post my results here.

---

### Post by gborzi on 2006-06-14
Look at this page
[http://dagobah.ucc.asn.au/dapper-kernels/](http://dagobah.ucc.asn.au/dapper-kernels/)
it has precompiled kernels for 686 and 386 with the suspend2 patch. I followed the "quick start" and it worked on my compaq evo n610c .

---

### Post by mority on 2006-06-14
[QUOTE=pellgarlic]
[https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend](https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend)
[/QUOTE]

I followed the instructions at this link you posted, pellgarlic, and now it works perfectly :D

Thanks again!

---

### Post by pellgarlic on 2006-06-14
no problem - glad to hear you got it working :)

---

### Post by psyeye on 2006-06-14
Working here, too, but:

Anyone know how to change the command which is executed when running System -> Log Out -> Hibernate ??

When I do "sudo hibernate" at a CL everything's fine, using the menu seems to be using the in-kernel-hibernate...

:confused: 
psyeye

---

### Post by andraycho on 2006-06-29
I did follow following suggestion and it works! =D> 
He even posted kernel for k7 as I requested.

Thanks.

---

Look at this page
[http://dagobah.ucc.asn.au/dapper-kernels/](http://dagobah.ucc.asn.au/dapper-kernels/)
it has precompiled kernels for 686 and 386 with the suspend2 patch. I followed the "quick start" and it worked on my compaq evo n610c .
__________________
Giuseppe Borzi'

---

