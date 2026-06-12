---
title: "Dell Vostro 330 w/Nvidia Optimus: problem w/ext. VGA"
date: 2011-01-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kencamargo on 2011-01-31
My wife bought a Dell Vostro with the Nvidia dual graphics adapter. I can't get the external VGA monitor to work properly; in all settings and resolutions shown the output is wavy and makes the display unreadable (and possibly a health hazard to the eyes of anyone who tries too hard to look at it...). I got Maverick 10.10 (64 bits) on it with all the latest updates, and am not using the Nvidia proprietary driver (this screws everything up). I have read some sparse commentaries attributing this to a kernel bug, but even with the latest kernel upgrade (2.6.25-35) it's still not working. If I boot the machine with Windows (much to my regret), the external display works fine, so it's not a hardware problem.
I'd appreciate any help...
Thanks in advance,
Ken

---

### Post by redy1966 on 2011-02-02
sorry, but there is no solution in sight atm.
have a look at this topic:
[http://ubuntuforums.org/showthread.php?t=1660986](http://ubuntuforums.org/showthread.php?t=1660986)

br
redy

---

### Post by kencamargo on 2011-02-02
> **redy1966 said:**
> sorry, but there is no solution in sight atm.
have a look at this topic:
[http://ubuntuforums.org/showthread.php?t=1660986](http://ubuntuforums.org/showthread.php?t=1660986)

br
redy

Hi Redy,

The thread you mentioned refers to other problems. I managed somehow to get the graphics card working (though not with 3D acceleration & other stuff), but I can't get an *external* monitor to work. This has been reported as a bug, see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614238](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614238), but no current fixes seem to be available.

There's also this: [https://bugs.freedesktop.org/show_bug.cgi?id=28306](https://bugs.freedesktop.org/show_bug.cgi?id=28306) - the picture there is exactly what I am experiencing.

Ken

---

### Post by kencamargo on 2011-03-21
Help anyone? Pretty please?

---

### Post by kencamargo on 2011-03-29
Finally, a cure for the external VGA wavy output problem:    

Install the kernel drm-intel-next available here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2011-02-12-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/drm-intel-next/2011-02-12-natty/")

Then:

sudo dpkg -i linux-headers-2.6.38-997_2.6.38-997.201102120912_all.deb
sudo dpkg -i linux-headers-2.6.38-997-generic_2.6.38-997.201102120912_amd64.deb
sudo dpkg -i linux-image-2.6.38-997-generic_2.6.38-997.201102120912_amd64.deb

(thanks to lcipriani at ask ubuntu)

Ken (now a happy camper)

---

### Post by aridus on 2011-05-27
I would like to try this out to see if it will allow me to use an external monitor with my Dell Vostro 3300. However, the link is dead: can anybody help please?

Thanks!

---

### Post by kencamargo on 2011-05-27
> **aridus said:**
> I would like to try this out to see if it will allow me to use an external monitor with my Dell Vostro 3300. However, the link is dead: can anybody help please?

Thanks!

Hi,

I can't say that with absolute certainty, but I am pretty sure that if you upgrade to Natty it would be the same. What that link had was a Natty kernel that you could install into Maverick.

I'll be upgrading my wife's laptop soon, and I'll post the results here.

HTH,
Ken

---

### Post by aridus on 2011-05-27
Many thanks: I am already running Natty. When you have any further information, that would be great!

---

### Post by kencamargo on 2011-05-27
> **aridus said:**
> I would like to try this out to see if it will allow me to use an external monitor with my Dell Vostro 3300. However, the link is dead: can anybody help please?

Thanks!

Hi - I just unamed this computer (running Natty) and the kernel is listed as 2.6.38-8 - maybe this is the problem, that kernel is 2.6.38-997. I wonder if some expert might clarify that.

Ken

---

### Post by kencamargo on 2011-05-27
Just in case, the kernel packages are here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/current/)

---

### Post by aridus on 2011-05-27
At this point I have become a little confused. If I download the three deb files can I then install them without damaging my natty installation, to see if they solve the external-monitor-flickering-problem?

thanks!

---

### Post by kencamargo on 2011-05-27
> **aridus said:**
> At this point I have become a little confused. If I download the three deb files can I then install them without damaging my natty installation, to see if they solve the external-monitor-flickering-problem?

thanks!

In principle, yes. You'll have a new kernel that will show in your options at boot time, if anything goes wrong you can still boot with the previous kernel.

---

### Post by aridus on 2011-05-27
Thanks - OK, I installed them but they don't show up on the grub menu (I have run sudo update-grub). 

Any further ideas?

thanks!

---

### Post by aridus on 2011-09-08
I used the information in this thread to solve this problem with my Dell Vostro 3300 and Dell external monitor. However, the problem crops up again with 11.10 Beta 1. This surprised me as I presumed the new Linux kernel would have this patch. I would like to draw this to the attention of the people working to finalize 11.10 but don't know what is the best way to do so.

---

### Post by kencamargo on 2011-09-08
> **aridus said:**
> I used the information in this thread to solve this problem with my Dell Vostro 3300 and Dell external monitor. However, the problem crops up again with 11.10 Beta 1. This surprised me as I presumed the new Linux kernel would have this patch. I would like to draw this to the attention of the people working to finalize 11.10 but don't know what is the best way to do so.

I second that. I also don't know how to bring this to the attention to the powers-that-be, but this is getting ridiculous; a bug that has been detected months ago, for which there is a known solution, but said solution keeps being squeezed out from the production kernels...

---

### Post by aridus on 2011-09-12
Please note that I have added a reference to this thread at a thread I have opened in the Oneiric forum ([http://ubuntuforums.org/showthread.php?t=1839707](http://ubuntuforums.org/showthread.php?t=1839707)).

---

### Post by aridus on 2011-09-19
I really would like to see this bug fixed in Oneiric, so... 

I don't know whether it is appropriate but I have lodged a bug report for this (see [https://bugs.launchpad.net/ubuntu/+bug/853838](https://bugs.launchpad.net/ubuntu/+bug/853838)). Perhaps somebody who understands these matters better (kencamargo?) could add any relevant and/or missing information to the report?

Thanks!

---

### Post by aridus on 2011-10-14
As this bug bugs me greatly I like to keep this updated: This is just to confirm that in Ubuntu 11.10 released yesterday 13 October 2011, this bug has not been squashed.

Thanks, Martin

---

### Post by nutsy.ben on 2011-11-09
Same here, 

the problem remains ...

---

### Post by aridus on 2011-11-09
Please see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614238](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614238)

where you will find a link to a patched kernel that solves this problem for 11.10

What happens next I don't know...

---

### Post by josvanr on 2011-12-20
hi, I want to try this, which of the packages do i need to install? Will they replace my old kernel?

josvanr

---

### Post by aridus on 2011-12-21
If you are using Oneiric the problem is now solved (if you enable proposed updates in software sources). See

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614238](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614238)

If you are using Natty I am unsure what the situation is.

---

### Post by josvanr on 2011-12-21
bummer, still on natty because I use xrandr --scale to get a higher virtual resolution and this doesn't work correctly yet on kubuntu 11.10...............

---

### Post by aridus on 2011-12-21
Keep following [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/614238](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/614238)

If you look at the thread I think you will find that the person who has done this valuable piece of work is also working to do it for Natty. Best of luck.

---

### Post by josvanr on 2011-12-21
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614238](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614238)

comment #186 yes ! It worked, thnx! It does replace the old kernel so one can't try them both, but it worked fine.....

josvanr

---

