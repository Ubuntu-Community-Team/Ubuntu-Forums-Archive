---
title: "Latitude E6400"
date: 2008-09-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rasmus91 on 2008-09-25
Guys please help me on this one, i have a dell latitude E6400. its a good laptop but it would be even better if i could just run ubuntu on it. unfortuneatly i can't seem to install the driver to the 5100 agn. it seems that ubuntu won't read the wifi card. theres is a small lamp that'll light if the wifi switch is on, the computer doesn't read anything. Please tell me how to make this work: im running ubuntu 8.04 64bit. if you want more information just ask, if the information is garthered by typing something in the terminal tell me what to type.

Please help me on this, if this won't work i'm stuck on     Vista ](*,)

---

### Post by jher on 2008-09-29
I just got the E6400 with the wifi link 5300 card.  It looks like we're both S.O.L. for the moment as Intel hasn't released drivers for either card.  I've inquired with Intel support as to the date of a driver release and will post it here when I find out.

---

### Post by jher on 2008-09-30
Here is the reply I received from Intel Support:

[I]Hello Dan,

Thank you for contacting Intel(R) Technical Support.

Please be aware that Intel(R) does not provide any beta drivers due to its policies. 
At this moment there are no Linux* drivers available. We do not have a release date yet.

Regards,

Stefan S. 
Intel( R) Technical Support
[http://support.intel.com](http://support.intel.com)[/I]

---

### Post by moschops on 2008-10-01
> **jher said:**
> I just got the E6400 with the wifi link 5300 card.  It looks like we're both S.O.L. for the moment as Intel hasn't released drivers for either card.  I've inquired with Intel support as to the date of a driver release and will post it here when I find out.

You should check this thread - [http://ubuntuforums.org/showthread.php?t=903240](http://ubuntuforums.org/showthread.php?t=903240) - but beware if you get the latest Intrepid Alpha 6 image there is a bug that could render your hardwire ethernet device inoperable (see the warning on the Alpha 6 download page at ubuntu.com). The beta release which is due out tomorrow (I think) should have a fix that disables the ethernet device to prevent it being damaged so I guess you will ONLY be able to use WiFi - assuming reports that it works are correct.

A solution may be to boot with Windows which you get from Dell included anyway, then use VirtualBox to run Ubuntu as a guest VM until hardware support issues are resolved.  VirtualBox runs very nicely and on a decently equipped dual-core machine should be acceptable so long as you don't need to do accelerated graphics stuff (VirtualBox does not support OpenGL for virtual machine guests).

---

### Post by Paul S on 2008-10-02
> **rasmus91 said:**
> Guys please help me on this one, i have a dell latitude E6400. its a good laptop but it would be even better if i could just run ubuntu on it. unfortuneatly i can't seem to install the driver to the 5100 agn. it seems that ubuntu won't read the wifi card. theres is a small lamp that'll light if the wifi switch is on, the computer doesn't read anything. Please tell me how to make this work: im running ubuntu 8.04 64bit. if you want more information just ask, if the information is garthered by typing something in the terminal tell me what to type.

Please help me on this, if this won't work i'm stuck on     Vista ](*,)

I don't have your card, but noticed this thread, which might help:

[http://ubuntuforums.org/showthread.php?p=5727196](http://ubuntuforums.org/showthread.php?p=5727196)

regards,

---

### Post by rasmus91 on 2008-10-22
How do i install drivers for my graphic card? (guess thats what i need. can't really run any game nice, most crashes. I tried Astro menace, the graphic isn't smooth at all...

---

### Post by hasinasi on 2008-10-23
The touchpad issue has been solved. 
It's already taken care of in the latest kernels. So with the release version of 8.10 (intrepid) it should be taken care of. 

If you need to use another/older kernel, there is a patch available, so than the fix can be included as well. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270643]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270643")

---

### Post by rasmus91 on 2008-10-26
Well... about some touchpad, i didn't have any problems in 8.04... 

What i really need is to know if there's a better driver for my card. one of my buddies have a older intel graphic card, when doing ```
glxgears
``` he gets 1000 fps+ my card SHOULD BE way better than his, but still, i just get 300+ fps, any suggestions?

Thanks in Advance

---

### Post by entner on 2008-11-02
I get around 400 FPS in glxgears. This is on my Latitude E6400 with Intel X4500 graphics. [_More benchmarks in my blog entry_]("http://www.entner.net/blog/dell-latitude-e6400-with-ubuntu-intrepid-ibex-810-english").

---

### Post by undoIT on 2008-11-15
I just tried glxgears on my E6400 with X4500MHD. I am getting between 300 - 350 fps. I'll have to try this on my other laptop for comparison sake. Perhaps Intel still has some major driver optimization to do. I also ordered the 5300 Intel wireless card and it is working perfectly out of the box with Intrepid 8.10

---

### Post by jher on 2008-11-25
> **jher said:**
> Here is the reply I received from Intel Support:

[I]Hello Dan,

Thank you for contacting Intel(R) Technical Support.

Please be aware that Intel(R) does not provide any beta drivers due to its policies. 
At this moment there are no Linux* drivers available. We do not have a release date yet.

Regards,

Stefan S. 
Intel( R) Technical Support
[http://support.intel.com](http://support.intel.com)[/I]

this is working now in the 8.10 official release

---

