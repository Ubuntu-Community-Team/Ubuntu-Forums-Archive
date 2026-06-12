---
title: "What is 'PCMCIA - Failed'? (Worked until I installed nVidia drivers)"
date: 2006-08-16
forum: Desktop Environments
---

### Post by Raavea on 2006-08-16
Before I install the nVidia drivers on my system, everything on bootup is **OK!**

 I've noticed that once I install my nVidia driver *(I re-installed ubuntu a few days ago. Because I like wiping my HD and starting fresh.)* the bootup had one single **Failed**. And that failed is the PCMCIA Driver.

 What the hell is this PCMCIA driver..? I searched the forums, and it seems to be some kind of wireless connecting-to-the-intarweb card thing-a-ma-jig.

 o.O Surely if I need it to connect to the net.. I shouldn't be connected right now?

 But then, occasionally my connection will just vanish. The netgear thing will say I'm connected when I can't get anything internetty at all to work. This requires unplugging my ethernet cable at both ends *(netgear network router and computer base)* and plugging it back in. That seems to work.

 **So what is the PCMCIA drive? What do I do about it not working?** Will I ever stop asking annoying questions?

---

### Post by Firetech on 2006-08-16
PCMCIA (also known as PC-Card) is a standard for Laptop extension cards, like Wireless network or extra USB slots. Mostly only laptops have PCMCIA (there are adaptors available for stationary PCs), so if your computer isn't a laptop, it should fail. It failing is harmless anyway (unless your life depends on a PCMCIA card connected to your PC ;) ).

---

### Post by Ramses de Norre on 2006-08-16
If you don't have/need pcmcia cards and wants to get rid of the ugly failed message: ```
sudo aptitude install sysv-rc-conf
sudo sysv-rc-conf
```
And use the space bar to deselect the pcmcia and pcmciautils services from all runlevels.

---

### Post by mordi on 2006-08-16
I used sysv-rc-conf to stop some services which should not start, however I found out that the command line 

sudo update-rc.d -f script_name remove

does the same thing. Since this command line is the debian way to configure startup scripts, which one is better?

---

### Post by Raavea on 2006-08-17
Fascinating. It must be something my father and I thought was necessary when we rebuilt my computer a few years back.

 No wireless for me thanks, I dislike security holes! ;)

Thanks for the script to remove the message, but I'll leave it there to remind me not to include one in my next rig.


 Mordi, that's an interesting question... I'm willing to bet that they both do the same thing, but the commands are just different. As in, the debian way is the debian way, and the other is either default linux or ubuntu way.

 What do you think?

---

### Post by mordi on 2006-08-17
the reason I asked is that when you disable a script with sysv-rc-conf, if you look in rcX.d, the name of the script will still start with K, meaning the script should still start. if you disable it with update-rc the name of the file starts with k, meaning that it will be skipped at startup.
I guess I am unclear about the difference between the two.

---

### Post by dannyboy79 on 2006-08-19
I just want to make sure you Understand something About wireless and or pcmcia, just because a laptop or desktop could use the pcmcia slot as a way to make it have a wireless connection to an access point or wireless router has NOTHING to do with it having a security hole. Wireless these days can be very secure! WEP is an old standard for wireless and can be hacked if someone really wanted to get onto your wireless connection but they came up with WAP security and is way harder to hack so please make sure you understand that wireless and pcmcia don't mean UNSECURE AT ALL. Your comment, "No wireless for me thanks, I dislike security holes!" really doesn't make any sense! Besides that, you're using linux, which comes damn secure by default!!!!

---

