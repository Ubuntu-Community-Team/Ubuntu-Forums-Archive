---
title: "Dell XPS M1330 UBUNTU PREINSTALLED"
date: 2008-02-18
forum: Dell  Ubuntu Support
---

### Post by cygnis1 on 2008-02-18
I am looking at the xps m1330 laptop with 7.10 preinstalled.  Does anyone have one?  Does it work well "out of the box"?  It looks like it has the intel video card installed.  Does it support 3D effects out of the box?  Would like to play with Compiz Fusion if it works without any problems.  
Cygnis1

---

### Post by itsbradman on 2008-02-18
You have the option of the nvidia graphics card.  I would reccommend that.

---

### Post by cygnis1 on 2008-02-18
It appears to only offer the Intel video card.

---

### Post by jpittack on 2008-02-18
America's offerings are a bit behind.  Give it awhile.

---

### Post by Keffin on 2008-02-18
I have an Ubuntu preinstalled M1330. I'm very happy with it, but the one thing that doesn't work fully is compiz, so the intel X3100 graphics card has been blacklisted. It appears that  _[it will still be blacklisted for Hardy](http://www.realistanew.com/2008/01/12/compiz-updates)_, but search the forums or google and you can find guides to get it going - note this may be with reduced functionality, and I haven't been bothered enough to try.

---

### Post by Beloch on 2008-02-18
> **cygnis1 said:**
> It appears to only offer the Intel video card.

It looks like it's available through this [link]("http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&l=en&oc=DYCWTU1&s=dhs"), but that's just for the U.S. I think.  Are you somewhere else?

Dell has created ubuntu images for the m1330, among other laptops, that you could use to reproduce a factory ubuntu install (minus Dell's proprietary DVD playing software, which you don't need anyways)  They're available [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO").

You might want to consider buying a Vista machine if you can't get the options you want with the Linux machines.  In the U.S., the base Vista machine is $45 more than an Ubuntu machine with the same specs, but I seem to recall that some options cost different ammounts, so depending on how you spec out your system the Linux machine may cost more than an identically spec'd vista machine!

Personally, I wound up ordering a Vista machine since us canucks don't have any other options.  (Dell doesn't sell it up here.)  I haven't gotten mine yet, but the current plan is to do a fresh install anyways rather than using those images.

---

### Post by lawr_rawr on 2008-02-18
You can save money if you buy one with Vista and install Ubuntu from the iso on Dell's wiki. I did this and had no problems. 

Also, if you are willing to buy a refurb, you can save a ton! The outlet.dell.com selection is pretty poor right now, but I think they post new systems on Tuesdays. I saved about $600 off of an identically configured new system. 

Just make sure to get an Intel wireless card (I have the 4965 N card) and the Nvidia graphics card.

---

### Post by gecko113 on 2008-02-18
Well i just switched over to ubuntu 7.10 and i have an XPS M1530 n i had no problems with running Compiz and it actually works welll

---

### Post by drobvice on 2008-02-19
> **Beloch said:**
> It looks like it's available through this [link]("http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&l=en&oc=DYCWTU1&s=dhs"), but that's just for the U.S. I think.

How did you find that link?

*Edit - NM.  I could have sworn the last time I went to the site (yesterday) I didn't get the option of the nvidia card.

---

### Post by drsaamah on 2008-02-19
Just to let you know your options... I bought the M1330 with windows vista because at the time the 1330n wasn't available in the US.  Anyways, I downloaded the Ubuntu .iso that Dell provided for the 1330n and everything worked perfectly for me.  The only probably I had was a screen brightness issue but that ended up being gnome.  Spending the extra money definitely sucked, but I'm sure you would rather have a computer with the specs YOU want since you can install Ubuntu yourself.  If you have any questions about the computer let me know, I'll be more than glad to help!

---

### Post by jamboarder on 2008-02-22
Got my M1330 with Ubuntu 7.10 preinstalled a couple weeks ago.  Everything works beautifully.  The intel integrated graphics is blacklisted by compiz but it was relatively painless to un-blacklist it (search the fourms here) and I haven't noticed any problems.  I prefer the KDE desktop so I installed kubuntu-desktop did my standard customization to get it looking better than the default kubuntu looks.  It basically looks like this now:
[http://ubuntuforums.org/g/images/37315/1_Aya_Theme_SS2.png]("http://ubuntuforums.org/g/images/37315/1_Aya_Theme_SS2.png")

Man, did it feel good to get a decent looking and performing laptop with linux preinstalled!

---

### Post by pormogo on 2008-02-28
have any other m1330n owners had somewhat ridiculously poor reliability from both the ipw3945 module as well as the iwl3945 module. My wireless functionality is broken almost every time I come back from a suspend or a hibernate. I've looked around searching and searching to find an answer but all I've come up with so far is a list of threads with people identifying the same issues. I tagged mine onto the Hibernate/suspend issues thread so it's on the last page (currently) if anyone wants to look at it. 

Any one happen to have any ideas how to fix this. I've been able to get just about everything else working to my liking (and can easily deal with no video in compiz for right now) but having to screw around with modprobe everytime I come back from a hibernate or suspend just to get my wireless card working is getting old (and sometimes that doesn't even seem to work, reloading the module that is).

---

### Post by youthforlinux on 2008-02-29
I have owned the XPS M1330 for 6 months now.  I bought it with Vista obviously and I didn't really like all of the bloatware so I installed ubuntu on it.  CUreently I dual-boot Vista and Ubuntu on it, but only really use VIsta for my TV Tuner...Its really easy to get ubuntu running on it...I didn't have to do anything to get internet, and it was easy to get the NVidia Drivers to work...plus i had the option of more RAM and the NVidia Video Card.

---

### Post by cygnis1 on 2008-02-29
I think it is cheaper to get the minimum ram from dell then upgrade via Crucial.  You can get 4 gigs for about the same price as 2gigs from Dell.  Did you have any problem getting Compiz Fusion to work?

Cygnis1

---

### Post by jonathanmotes on 2008-02-29
> 
I have an Ubuntu preinstalled M1330. I'm very happy with it, but the one thing that doesn't work fully is compiz, so the intel X3100 graphics card has been blacklisted. It appears that it will still be blacklisted for Hardy, but search the forums or google and you can find guides to get it going - note this may be with reduced functionality, and I haven't been bothered enough to try.
__________________

The issue with X3100 graphics has been fixed as of Hardy alpha 5. I tested it on my new Inspiron 1420 - it works great with Compiz!

---

### Post by LuisAugusto on 2008-03-01
**Drsaamah**

It seems that you have a Solid State Hard Drive.

Does it really boosts the speed?

Is it to slow for moving data?

Does it worth it´s price?

Thanks in advance :)

---

### Post by forceofnature on 2008-03-09
concerning the pre installation distro is it 32 bit or 64 bit?  I installed the 64 bit distro on my m1330 and it seems to work fine with exception of DVD playback.  I can't play back DVD's at all no matter what player and half of them lock up.

---

### Post by drsaamah on 2008-03-10
LuisAugusto,
I definitely enjoy the solid state harddrive.  It is definitely faster than my old harddrive.  Then again I believe my old hard drive was 5400 rpm.  So it depends whether you're going to get the 5400 or 7200 rpm drive.  As far as whether or not its worth the money... that's a personal decision.  I personally, fell that it was worth the money but I also got this laptop with the intention of it lasting for quite some time.  Sorry it took so long for me to respond.  Let me know if you have any other questions.

ForceofNature,
Your DVD playback issue isn't a 64-bit issue.  It's a proprietary issue.  I installed the 32 bit distro on my 1330 and like MANY others had to fight to get DVD playback.  I think to get it to work you need to :
~Install the libdvdread3 and libdvdcss2 libraries from the medibuntu repos (as with Ubuntu on any machine)
~Install a package called 'regionset' ie "sudo apt-get install regionset"
~Set regionset to your region.  So for North America I think its "sudo regionset" And then '1' and it should be set.  You only get to change the region like 4 or 5 times, so be careful.
~And finally... install something OTHER than totem.  I don't know if its just me but after doing the above I still couldn't get totem to play dvds.  I tried dl-ing every gstreamer package, i tried totem xine... everything.  But VLC plays my dvd (after doing the above) without a problem.
Hope that helped.  By the way, how is the 64 bit distro working on your 1330?  I'm thinking of making the 64-bit switch when hardy is finalized but I want to see what kind of issues that are.  Thanks mate!

---

### Post by forceofnature on 2008-03-10
Drsaamah,

I have the m1330 with the x3100 graphics.  So far the only issues with 64 bit is strange compiz functionality.  I was able to get limited compiz cant seem to get the control panel up but I dont really need compiz other than getting emerald to work.

Initially emerald did not work with compiz.  So I installed Gnome GL desktop and that seemed to allow emerald to work.

Scrolling feature on touch pad works vertically but not horizontally but I am not sure that is a 64 bit issue.  Camera does not work either.  It would be nice if it did but I dont really care about the built in camera.

Overall I like the speed of 64 bit.  Everything pops.  

Thanks for the DVD tips I will try it now.

Kevin
forceofnature

---

### Post by forceofnature on 2008-03-10
Ok I tried the DVD tips and no luck.  I was not able to install libdvdcss2 it reports as not available so maybe I need to add a software source.  If you have the address can you provide it?  DVD playback is not a priority but it sure would be nice.

Thanks,
Kevin

---

