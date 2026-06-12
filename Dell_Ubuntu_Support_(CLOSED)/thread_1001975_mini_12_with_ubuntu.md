---
title: "mini 12 with ubuntu?"
date: 2008-12-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sledhead45 on 2008-12-04
Has anyone tried loading ubuntu on this yet? It has the us15w Poulsbo chipset and the atom z520 processor. Supposedly it will be shipping with ubuntu soon. Im just wondering if anyone has got ubuntu loaded onto it, and if so how does stuff like compiz/suspend/hibernate/cpu scaling/networkManager/etc work. Not surprisingly, I can't find much info via google on this (presumably since it's such a new setup.) Thanks,

--travis

---

### Post by hrsrd on 2008-12-06
):P

Hi !!

I second the question. . . 
if feel very curious about this fact, is it possible or not???

Do we all gave to wait patiently until dell pops out the cork???

If anyone knows, please tell . . . 

Thanks,.,.,,

---

### Post by rigormotis on 2008-12-09
I got a mini 12 and unfortunately, no, Ubuntu does not work, nor will any other Distro that requires X as there is currently no Linux driver for the Intel GMA 500 graphics chip.

I'm hoping that they are planning on getting support for this soon, and that this is the reason why there isn't an official Dell Ubuntu version available.  Otherwise, I'm worried that they are planning on re-releasing the laptop with a different graphics chip (they're french site says it comes with a GMA 900, which does support Linux) and then abandon users of the GMA 500 version.

I'll probably put Arch Linux on it when I can, but don't know how long that will be.  It's a nice laptop, well designed and gets 6 hours of battery life with the 6 cell battery.  Vista is very slow until you remove a lot of the crapware that it comes with and then its better, but not nearly as quick as Linux or XP.

---

### Post by rigormotis on 2008-12-09
I just looked on the Japanese Dell site (where the Mini 12 has been available for a couple months now) and they do offer one with Ubuntu pre-installed on a GMA 500 chipset.  So it looks like I ought to be in luck, eventually.

---

### Post by eloyhc on 2008-12-10
[http://www.alphatek.info/2008/11/09/poulsbo-isnt-that-great-yet-intel-atom-inside/](http://www.alphatek.info/2008/11/09/poulsbo-isnt-that-great-yet-intel-atom-inside/)

---

### Post by eloyhc on 2008-12-10
What about if you get it at France?

[http://configure.euro.dell.com/dellstore/config.aspx?oc=n12m1205&c=fr&l=fr&s=dhs&cs=frdhs1&kc=productdetails~laptop-inspiron-12](http://configure.euro.dell.com/dellstore/config.aspx?oc=n12m1205&c=fr&l=fr&s=dhs&cs=frdhs1&kc=productdetails~laptop-inspiron-12)

---

### Post by kylecronan on 2008-12-26
If you haven't seen it already, check out this thread:

[http://ubuntuforums.org/showthread.php?t=1014534](http://ubuntuforums.org/showthread.php?t=1014534)

Ubuntu works fine on the Mini 12 once you install the right drivers.

---

### Post by pistoncito on 2008-12-29
I recently bought a mini 12 with ubuntu pre installed and dell said that it comes with Intel Graphics Media Accelerator 500. When i receive i could be more helpful

---

### Post by jetpeach on 2008-12-31
our dell mini 12 with ubuntu preinstalled is here today! i love it, i attached the output of lspci which shows all the hardware on it if anyone is curious.

so far it's really great, it is vastly superior to the last netbook we owned. the screen looked great, keyboard is basically full size... i've already raved about it in other posts, so anyway, yes ubuntu on dell mini 12 is great.
jet

---

### Post by arepaking on 2009-01-05
Hi guys!
I've found all your replies very useful. I have been thinking to buy a new Mini 12 to use it with Ubuntu.

I was wondering if the RAM could be upgrade it? Personally, I think that nowadays new laptops should come with a minimum of 2GB. 

The only reason that stops me from buying this model is that I do not know if the RAM can be improved.

One more thing that I would like to ask; Has anyone upgraded the Ubuntu version to 8.10? My understanding is that these laptops comes with 8.04 from factory.

Thanks in advance,
AK

---

### Post by jetpeach on 2009-01-05
The netbook comes with Ubuntu 8.04.1 from the factory - and it comes with a special version, the LPIA version from Dell. LPIA is low-power intel architecture (like i386), which allows the laptop to boot slightly faster and, in theory although I've never seen benchmarks/performance tests, allows it to use less power and perform better with its Intel Atom CPU. I mention this because it provides possible reasons *not* to update to Intrepid...

A number of people have switched to "vanilla" Ubuntu installs with the Dell mini 12 and also upgraded to Intrepid, their are several threads in the forums. There are a few issues right now with Intrepid that take some working out (the chipset is so new that it requires a one or two line change to the xorg.conf file after install to get to work right, and somebody else mentioned fiddling with wireless to get it going, although others didn't have this problem and he had upgraded not done a fresh Intrepid install.

All-in-all, I'm sticking with Hardy and the LPIA install Dell customized. Everything works, standbye, wireless etc, so why mess with a good thing? Only thing that is a real bummer is .DEB files for i386 require hacking before they can be installed on the customized Dell-LPIA.

But again, I can't emphasize how great of a netbook this is. It is well worth the extra dollars compared to those with 10" or 9" screens, and it's still super tiny/light.

I am uncertain about upgrading the RAM, but am very happy with the 1GB setup we got (of course, this is never going to be a "performance" or gaming machine - the CPU is too slow, onboard graphics, etc, but it handles just fine for all the normal tasks).

---

### Post by irwnfv on 2009-01-05
Unfortunately, 1gb is the maximum amount for this netbook.

[http://ark.intel.com/ProductCollection.aspx?codeName=24973](http://ark.intel.com/ProductCollection.aspx?codeName=24973)
It uses the Intel® SCH US15W (Poulsbo chipset) which was made apparently for smaller embedded devices to cut down on power and size.

---

### Post by arepaking on 2009-01-07
> **irwnfv said:**
> Unfortunately, 1gb is the maximum amount for this netbook.

[http://ark.intel.com/ProductCollection.aspx?codeName=24973](http://ark.intel.com/ProductCollection.aspx?codeName=24973)
It uses the Intel® SCH US15W (Poulsbo chipset) which was made apparently for smaller embedded devices to cut down on power and size.

As a side note to this post. I called Dell Sales department and I asked them if I could buy a Mini 12 with 2GB. The sales person told me that the current processor comes with the embedded memory. They call it: "the 2-in-1 Processor and Memory Board" and he showed me the mini 12 service manual (which can be found here: [http://support.dell.com/support/edocs/systems/ins1210/en/sm/index.htm](http://support.dell.com/support/edocs/systems/ins1210/en/sm/index.htm)

He also told me that Dell listen their customers and if people starts to ask (in their forums) for a memory upgrade then they will do it. I guess as a business is all marketing... who knows?

I guess I would have to wait until a new processor comes with 2GB.

---

### Post by catslaugh on 2009-01-14
I’ve been [getting Intrepid working on my Mini 12]("http://ubuntuforums.org/showthread.php?t=1037717").  Current challenge is getting the 1280×800 video mode working.

---

### Post by CrazyDesi on 2009-01-14
Hey I posted this in another forum, but I decided to post here for other opinions.  I am interested in the Mini 12. How long does the battery life last? Is it able to run basic applications well? How is youtube, openoffice, vlc, etc.

---

### Post by jetpeach on 2009-01-16
battery life around 4 hours for us, with wifi on and max screen brightness.

youtube, openoffice, vlc, they all work fine for us. however, normal .DEB packages for programs not in the repos won't install on the Dell configured one unless you reconfigure them for the LPIA-arch (read about LPIA on these forums if you're wondering why this is the case...).

it's truly a great netbook/notebook. screen is very pretty. overall, my girlfriend, who has never used linux, hasn't had any problems with it and uses it for hours every day.

---

### Post by sirebral on 2009-01-16
> **jetpeach said:**
>  however, normal .DEB packages for programs not in the repos won't install on the Dell configured one unless you reconfigure them for the LPIA-arch (read about LPIA on these forums if you're wondering why this is the case...).

I think this bug is fixed in the newest updates.  I am running the 8.04 version of Ubuntu that came with the Mini 9, it uses an LPIA Architecture, and I have not had any problems with non LPIA software.

I updated and the updates fixed the broken LPIA links, those all seem to be working now.  I did get errors, but then it updated passed those and I think it found them.  Normally I would get an error screen after the update saying some of the repos couldn't connect.  So I think one of the repos fixes that error as well.

After updating I just installed skype from the skype page and it works.

---

