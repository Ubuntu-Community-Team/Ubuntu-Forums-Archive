---
title: "help with iphone"
date: 2009-04-22
forum: General Help
---

### Post by rreyes1316 on 2009-04-22
I just about have my ubuntu machine set up and am almost ready to give WinXP the BOOT:) I am; however, stuck with using itunes for backing up my phone and updates--so I think. So the question is how should I set this up? I have the 9.04 amd64 version set up. Should I continue to dual boot XP just to access itunes or can I install itunes with wine? Or perhaps set up virtual XP with itunes on it? The XP I have is the 32bit version, however. And I have noticed Rythmbox, VLC, and Amarock do not recognize my iphone. Well . . .if setting up using wine is the answer, it appears that I am unable to set it up. I have downloaded the 32 and 64 bit version. 

I hope someone has experience with this.

---

### Post by Gizim on 2009-04-24
> **rreyes1316 said:**
> I just about have my ubuntu machine set up and am almost ready to give WinXP the BOOT:) I am; however, stuck with using itunes for backing up my phone and updates--so I think. So the question is how should I set this up? I have the 9.04 amd64 version set up. Should I continue to dual boot XP just to access itunes or can I install itunes with wine? Or perhaps set up virtual XP with itunes on it? The XP I have is the 32bit version, however. And I have noticed Rythmbox, VLC, and Amarock do not recognize my iphone. Well . . .if setting up using wine is the answer, it appears that I am unable to set it up. I have downloaded the 32 and 64 bit version. 

I hope someone has experience with this.

Having the same problem i have a iPhone 3g and iTunes is holding me back from making a full switch. I was thinking of running a Virtual Machine of Windows and installing iTunes on it.

---

### Post by paradigm2 on 2009-04-24
Hope this helps?

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

I don't have an iphone so have no idea but wanted to give you the link to look over.

---

### Post by rreyes1316 on 2009-04-24
Which would be the best choice? Leave my dual boot set up as is and use iTunes there or setup windows in a virtual setup with iTunes in that configuration? If I do a complete install of ubuntu on my drive and use windows in a virtual setup, do I need to install the service packs, antivirus, and any other junk that goes with windows xp?

I will try the suggested links mentioned and post my results this weekend. Keep me posted Gizim on what you have tried. We should have a solution by the end of the weekend.

---

### Post by rodney757 on 2009-04-24
I had a dual boot with windows xp for my iphone but it is a pain to have to restart every time you want to use itunes so I'm in the process of setting up virtualbox. If yout computer can handle it, I recommend virtually installing windows.

---

### Post by rreyes1316 on 2009-04-24
Yes. That would get annoying. I wonder how little of the XP os I can install. Do you think I need to install SP 2 & 3? Do I need to setup the network? I never buy music from iTunes. Oh, wait, but I would have to update my iPhone os when needed. I looked at the "how-to" for the itunes setup and it seems to be a bit over my head. 

Hope we can cont. this as we try to set up the virtual box. When do you think you'll do this? I will make an effort to set it up by the end of this weekend.

---

### Post by rreyes1316 on 2009-04-24
Wow! Just setup windows with virtual box at home durring my lunch break. This was incredably easy! I hope setting up iTunes goes as smoothly.

---

### Post by rreyes1316 on 2009-04-24
OK. I got XP and iTunes on the virtual box but I am unable to mount the usb cable for the iphone.

Any suggestions?

---

### Post by rreyes1316 on 2009-04-25
Has anyone else been able to sync up? I tried the suggested links and still cannot get it to work.

---

### Post by Gizim on 2009-04-25
> **rreyes1316 said:**
> OK. I got XP and iTunes on the virtual box but I am unable to mount the usb cable for the iphone.

Any suggestions?

Same issue cant get the USB to work

---

### Post by rreyes1316 on 2009-04-25
Did you try the steps suggested on one of the sites suggested? I put in my devgid number but still no success.

[http://blog.taragana.com/index.php/archive/use-iphone-and-ipod-touch-for-ubuntu-810/](http://blog.taragana.com/index.php/archive/use-iphone-and-ipod-touch-for-ubuntu-810/)

4. Find your devgid:

    grep vboxusers /etc/group

5. Type this in (and remember to type your own number and your own username):

    vboxusers:x:123:username

6. Now, add this line to the bottom of /etc/fstab, replace the devgid number with your devgid:

    none /proc/bus/usb usbfs devgid=123,devmode=664 0 0

Restart and it should work.

---

