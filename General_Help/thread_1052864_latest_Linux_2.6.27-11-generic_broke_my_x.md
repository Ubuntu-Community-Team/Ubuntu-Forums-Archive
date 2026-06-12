---
title: "latest Linux 2.6.27-11-generic broke my x"
date: 2009-01-28
forum: General Help
---

### Post by sdowney717 on 2009-01-28
Linux 2.6.27-11-generic broke my x, no picture, screen is black

I get the login sounds and can type my user and password in from a black screen. Then it loads but still the screen is black

Going back to 2.6.27-9 screen works

I have a x1300 ati card using the ATI proprietary drivers

---

### Post by Nepherte on 2009-01-28
Perhaps regenerating the config file or reinstalling the driver helps.

---

### Post by exploder on 2009-01-28
I think Nepherte is right. I would try reinstalling the driver.

---

### Post by GepettoBR on 2009-01-28
Yes, usually drivers have to be rebuilt when newer kernel versions are installed. I have to do it all the time with my wireless card.

---

### Post by First_Delirium on 2009-01-28
I'm also having this same problem, Ubuntu loads and the login/desktop screen is nothing but a series of skewed, inverted color ubuntu logos lining the top of my screen.  I can also load 2.6.27-9, but will reinstalling my drivers for ATI using 2.6.27-9 work for 2.6.27-11? 

I'm using ATI Radeon 3200.  I'm also using the same version driver the OP is using. (Which may go without saying?)

---

### Post by Nepherte on 2009-01-28
> **First_Delirium said:**
> I'm also having this same problem, Ubuntu loads and the login/desktop screen is nothing but a series of skewed, inverted color ubuntu logos lining the top of my screen.  I can also load 2.6.27-9, but will reinstalling my drivers for ATI using 2.6.27-9 work for 2.6.27-11? 

I'm using ATI Radeon 3200.  I'm also using the same version driver the OP is using. (Which may go without saying?)
You will have to install the drivers in 2.6.27-11 using the terminal.

---

### Post by sdowney717 on 2009-01-28
could you uninstall the ati driver under the old working kernel
then reboot with the new kernel into the desktop
then install video driver using the downloaded driver from ati website?

---

### Post by Nepherte on 2009-01-28
That's possible too. I usually boot in the new kernel directly, switch to a virtual terminal (ctrl + alt + F1) and remove/install the new driver, but that's just me.

---

### Post by sdowney717 on 2009-01-28
Even the cntrl alt F1 had left me a black screen.

---

### Post by zika on 2009-01-28
> **sdowney717 said:**
> Even the cntrl alt F1 had left me a black screen.

[http://ubuntuforums.org/showpost.php?p=6631114&postcount=14](http://ubuntuforums.org/showpost.php?p=6631114&postcount=14) explains how I've got out of it today ... ;)

ATI HD 3650: reboot, chose "recover" line, used xfix, uninstalled ATI driver, cleaned any instance of fglrx in Synaptic and then decided: weather to install ATI driver again.  not yet... :) after scrolling through Xor.0.log I discovered that Ubuntu found radeon and used it but my xorg.conf is as empty as it ever was ... ;) it works for me, since I do not use compiz, videos are fine, everything is fine and quicker than ever. probably I'll install ATI driver at some point ... I was preparing myself to try uninstalling it for some time and 2.6.27-11-generic made me do it and I do have any regrets ...

---

### Post by sdowney717 on 2009-01-28
yes, I removed fglrx using synaptic and got the low graphics mode problem on the reboot.
I told it to go ahead and boot anyway and I am running the radeon driver with decent resolution BUT the refresh rate is horrible, the monitor flashes hurt my eyes. I am going to build the ati driver package and reinstall. I found in the past I cant run google earth with the radeon driver

quick easy way to do this is here
[http://ubuntuforums.org/showthread.php?t=1017035&highlight=ati](http://ubuntuforums.org/showthread.php?t=1017035&highlight=ati)

a good reason to not use ubuntu repo version of fglrx is it is old.

---

### Post by fragos on 2009-01-28
If you install drivers from the Ubuntu repository they will be updated when the kernel is. If you compile them yourself or install them from a vendor site Ubuntu's package management system won't be able to upgrade them. If you compile drivers yourself they will need to be recompiled after every kernel update that changes the version number.

---

### Post by zika on 2009-01-28
> **fragos said:**
> If you install drivers from the Ubuntu repository they will be updated when the kernel is. If you compile them yourself or install them from a vendor site Ubuntu's package management system won't be able to upgrade them. If you compile drivers yourself they will need to be recompiled after every kernel update that changes the version number.
this is a very good point.

---

### Post by Evagrios on 2009-01-29
So, if I installed them from the vendors site, what do I do to fix this?

---

### Post by bsmith1051 on 2009-01-29
I am running an ATI motherboard with the built-in Radeon 2100, and using the Ubuntu-provided ATI proprietary video drivers.  The kernel update a couple days ago (there's another one today?) did no harm to my video.  So I think the comment about Ubuntu repos is a valid one.

Also, I'd read that there were known problems with the latest ATI drivers with Ubuntu and so that was the reason they (the Ubuntu developers) were intentionally sticking to an older known-good version.

---

### Post by zika on 2009-01-29
> **fragos said:**
> If you install drivers from the Ubuntu repository they will be updated when the kernel is. If you compile them yourself or install them from a vendor site Ubuntu's package management system won't be able to upgrade them. If you compile drivers yourself they will need to be recompiled after every kernel update that changes the version number.
was this at the end a dkms issue? I do not have it installed. looking at the logs that is the difference between yesterday's and today's 2.6.27-11generic (14 and 25). should I install it or is it there by default? would dkms transfer ATI driver installed outside of apt-get, aptitude and synaptic to a new kernel?

---

### Post by GepettoBR on 2009-01-29
> **Evagrios said:**
> So, if I installed them from the vendors site, what do I do to fix this?

You don't. You have to re-install the driver against every new kernel. I have to do that with my wireless network adapter. It's a small inconvenience, but since the drivers we use aren't in the repositories theres no way to tell the package manager that they need to be ported to the new kernel.

---

### Post by sdowney717 on 2009-01-29
I really dont mind recompiling the ati driver since I get the latest driver that way.
But I tend to forget everything when I get a black screen. Very disconcerting!
For a while in the past ATI was updating their driver quite frequently and the one in the repos was not working properly for me. Everything I have run has worked fine with this latest driver.

---

### Post by GepettoBR on 2009-01-29
> **sdowney717 said:**
> I really dont mind recompiling the ati driver since I get the latest driver that way.
But I tend to forget everything when I get a black screen. Very disconcerting!
For a while in the past ATI was updating their driver quite frequently and the one in the repos was not working properly for me. Everything I have run has worked fine with this latest driver.

I'm in nearly the same situation with my wireless driver. Except I don't get a black screen without it, just no internet, and that the repos don't even have an option for my model. The driver is seldom updated, so I keep a copy of the source in my home directory to compile when I do a kernel update.

---

### Post by DrakeGis on 2009-01-30
Same here, this is what I did

1) Download ATI drivers from ATI web page
(for me was from [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html) )
2) Boot with the new kernel 
3) Change the driver installer file to be executable (chmod +x <filename>)
4) Run the installer ./<filename>
5) Reboot

---

### Post by sports fan Matt on 2009-01-30
Im gonna hold off on upgrading to Intrepid till this is resolved with a new kernel. Dont want my system borked again.

---

### Post by weezerisrock on 2009-01-30
> **sox fan Matt said:**
> Im gonna hold off on upgrading to Intrepid till this is resolved with a new kernel. Dont want my system borked again.

As far as I know, this will not be resolved with a new kernel, the option to not have your system "borked" would be to not use the ati proprietary drivers and go back to fglrx drivers in the repos and use those instead.

---

### Post by landloper on 2009-11-04
I installed on a HPPA RISC machine.  No graphical desktop.  I installed the KDE desktop.  When I boot, all is good then it ends up with a blank screen.  I think the desktop loaded, but my video driver isn't working.  It is an HP C3750 with two (I'm only using one) HP A49858B Visualize fxe video cards installed.  I'm completely new at this.  Here's the question:
How do I find and install a video driver?  All I have is command line.  I don't even know where to look for a configuration file that is loading the driver.
I hope I'm in the right place.  I've tried to read these posts and figure out what is going on.  Thanks for the help.

---

