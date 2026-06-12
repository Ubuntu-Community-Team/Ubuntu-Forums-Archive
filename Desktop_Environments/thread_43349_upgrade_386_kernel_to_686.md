---
title: "upgrade 386 kernel to 686"
date: 2005-06-21
forum: Desktop Environments
---

### Post by pataphysician on 2005-06-21
i recently installed ubuntu on my laptop with the 386 kernel. after a lot of forum browsing, i've got everything working pretty well (thanks, btw). however, it seems to run a little sluggish. i've noticed at boot and when i run dmesg i get an error:

Warning: CPU frequency is 1400000, cpufreq assumed 600000 kHz.

would switching to the 686 kernel fix that and increase performance? and, if so, how would i go about doing that? would i have to reconfigure anything (i'm primarily concerned with display drivers and the ability to sleep/hibernate, which caused me the greatest grief).

---

### Post by Xian on 2005-06-21
[QUOTE=pataphysician]Would switching to the 686 kernel fix that and increase performance? and, if so, how would i go about doing that? would i have to reconfigure anything (i'm primarily concerned with display drivers and the ability to sleep/hibernate, which caused me the greatest grief).[/QUOTE]
I honestly don't know if that would fix your problem, but if your system is capable of running on a 686 kernel you certainly might considering installing it as it would possibly be more efficient. Run the command below and look at the output. I've included my own:

```
$ uname -a
Linux linux 2.6.10-5-k7 #1 Tue Jun 7 10:08:19 UTC 2005 i686 GNU/Linux
$
```
Notice the "i686" notation in the output. If you have that as well then your box is perfectly able to run the 686 kernel. Now, mine says that but I also have an AthlonXP processor (not the 64 bit) so I decided to install the K7 kernel, which is configured more closely with my system specs.

To install the newer kernel just do a search for 'linux-image' in Synaptic and find a kernel image that would fit your box. For example, I installed the linux-image-k7. Synaptic will then auto-configure everything and set-up grub for you as well, giving you the choice of booting into both your previous and new kernel. When you've decided that you want to stay with the new kernel you can safely remove the previous version using Synaptic once again, but this should only be done after several login sessions.

---

### Post by veritas366 on 2005-06-21
I was interested in trying this.  However it won't let X start up.  I assume this is because of the new kernel with my nvidia graphics card.  How do I get X to work now?  I could just apt-get the Nvidia driver, but what changes will that make and will I be able to start x in the non k7 kernel if the k7 one doesn't work out?

---

### Post by Xian on 2005-06-21
[QUOTE=veritas366]I was interested in trying this. However it won't let X start up.  I assume this is because of the new kernel with my nvidia graphics card.  How do I get X to work now?  I could just apt-get the Nvidia driver, but what changes will that make and will I be able to start x in the non k7 kernel if the k7 one doesn't work out?[/QUOTE]
If you already have the nvidia-glx package installed and working on a previous kernel, you just need to install the linux-restricted-modules for any other kernel type that you have on your system. If you want to try the k7 kernel then you would need to also install the linux-restricted-modules-k7 package in Synaptic.

---

### Post by pataphysician on 2005-06-21
thanks xian, the kernel switch was successful. the error message is gone and there's been a very noticeable performance increase. all i had to do after the switch was install the proper nvidia drivers.

---

### Post by otherdave on 2005-06-22
[QUOTE=pataphysician]thanks xian, the kernel switch was successful. the error message is gone and there's been a very noticeable performance increase. all i had to do after the switch was install the proper nvidia drivers.[/QUOTE]

I just upgraded to the 686 kernel as well. My processor is just a 1.7 Ghz and I don't remember seeing the same message you did, but the 686 kernel seemed a bit faster. I have an ATI card so I didn't need to worry about the NVidia stuff but I had also installed the kernel-restricted package for the new one.

One thing that almost got me, but I found a post somewhere in these forums, is that the 386 kernel doesn't go about 900 megs of ram. I had recently upgraded from 512 mb to 1.5 Gigs and was very unhappy when I saw that /proc/meminfo thought I had 900 megs. If any of you are currently running the 386 kernel, look out for this too :)

---

### Post by drgreborn on 2005-10-04
I'm interested in upgrading to the 686 kernel. I ran into the same problem of X not starting up. Which packages exactly am i supposed to install?
Thank you in advance.

---

### Post by jworr on 2005-10-04
to install as 686 kernel I install these packages: (This kernel is good for intel chips p2 to p4 and relatively new amd chips and up)

linux-restricted-modules-686
linux-686
linux-image-686
linux-image-2.6.10-5-686

reboot and try it out, if it works then you can remove the 386 packages

---

### Post by drgreborn on 2005-10-05
I managed to install the 686 kernel but I cant seem to install the nvidia driver

---

### Post by Perfect Storm on 2005-10-05
What does it say in terminal?

---

### Post by Hugo Bio on 2005-10-05
I have an AthlonXP 2000+ processor, can i install the K7 kernell architecture?
With "uname -a", it returns:

Linux ubuntu 2.6.10-5-386 #1 Fri Sep 23 14:13:55 UTC 2005 i686 GNU/Linux

thanks in advance!

---

### Post by bob_c_b on 2005-10-05
[QUOTE=drgreborn]I managed to install the 686 kernel but I cant seem to install the nvidia driver[/QUOTE]

Did you install the restricted moduels? Are you using the nvidia-glx package from Synaptic or a newer driver? Many times the newer drivers will cry if you don't have proper kernel headers installed.

---

### Post by drgreborn on 2005-10-05
Installed newer driver from NVIDIA's site. managed to fixed it. Yeah you are right I forgot to add the headers before running the installer. Now a new problem came up because of the driver haha its oGL related so wont post the problem here. Thanks bob_c_b.

---

### Post by Rory on 2005-10-16
[QUOTE=Hugo Bio]I have an AthlonXP 2000+ processor, can i install the K7 kernell architecture?
With "uname -a", it returns:
Linux ubuntu 2.6.10-5-386 #1 Fri Sep 23 14:13:55 UTC 2005 i686 GNU/Linux
thanks in advance![/QUOTE]

Yes, you can.  I just did the same.  In terminal, type:
```
sudo apt-get install linux-k7
```

That one command should install all the necessary packages and configure everything.  Once you reboot, you'll see that the k7 kernel is your default but the 386 kernel is still there, in case you have to go back in via that route.  

Let me know how it works for you.

---

### Post by ptiboli on 2005-10-18
I was just looking for that... Gonna try it also very soon... I have a athlon xp 2500+

thanks! :)

---

### Post by denisesballs on 2005-10-18
Is the K7 kernel specific for Athalon XP processors? How is it different than the 686?

---

### Post by bennettg on 2005-11-01
thanks

---

### Post by daahli on 2005-11-01
I have an AMD64, but am running 32-bit Ubuntu. What files should I download?

Thanks!

---

