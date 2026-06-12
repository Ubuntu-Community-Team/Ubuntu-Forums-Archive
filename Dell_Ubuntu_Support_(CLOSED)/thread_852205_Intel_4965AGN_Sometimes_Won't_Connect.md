---
title: "Intel 4965AGN Sometimes Won't Connect"
date: 2008-07-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by damis648 on 2008-07-07
Every couple of days, my wireless stops working. Not completely, for I can see networks, just can't connect. I can click on a network from the NM applet, and after about ten minutes it stops trying to connect. After a few reboots, wireless starts working again... any ideas? My card is the Intel 4965AGN. I have seen threads on this, but not any solutions. Any ideas?

Any help is appreciated!

---

### Post by damis648 on 2008-07-07
It is back on again... looking for a solution... any ideas?

---

### Post by stchman on 2008-07-07
> **damis648 said:**
> It is back on again... looking for a solution... any ideas?

Try installing Wicd.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

There is an Ubuntu repo on their site.

---

### Post by damis648 on 2008-07-07
> **stchman said:**
> Try installing Wicd.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

There is an Ubuntu repo on their site.

I have done this before (before I reinstalled trying to fix it) and it did not work. It seems to be a problem with the driver.

---

### Post by LibertyShadow on 2008-07-07
Does the card show up in lspci?  It would look like:

```
<*pci-id*>  Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev <*xx *> )
```

---

### Post by damis648 on 2008-07-07
> **LibertyShadow said:**
> Does the card show up in lspci?  It would look like:

```
Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection 
```

Certainly. The card is working fine most of the time. The only time it doesn't work is when I cannot connect to networks... they show up, but I can't connect. The card always shows up, and I can see networks.

---

### Post by damis648 on 2008-07-08
Bump?

---

### Post by fackamato on 2008-07-09
I'm seriously considering buying this card, to replace the Dell wifi card in my Inspiron 1520 (have to use ndiswrapper, but it works ok).

Out of curiosity, when it's working, are you getting good range?

Is there anything in the logfiles?

---

### Post by damis648 on 2008-07-09
> **fackamato said:**
> I'm seriously considering buying this card, to replace the Dell wifi card in my Inspiron 1520 (have to use ndiswrapper, but it works ok).

Out of curiosity, when it's working, are you getting good range?

Is there anything in the logfiles?

Sure, it used to work PERFECTLY out of the box, with good range and all. The only downside was that the current driver does not support N networking, so you are stuck with G speeds, but all-in-all pretty good.

Back to the support though, it's 4 AM here where I live and I can't sleep OR connect to my wireless. Nobody with any more ideas? I was thinking... should I try to use NDISwrapper?

---

### Post by damis648 on 2008-07-09
Here is another thread on this... no solution...: [http://ge.ubuntuforums.com/showthread.php?t=724275&page=2](http://ge.ubuntuforums.com/showthread.php?t=724275&page=2)

---

### Post by fackamato on 2008-07-09
> **damis648 said:**
> Sure, it used to work PERFECTLY out of the box, with good range and all. The only downside was that the current driver does not support N networking, so you are stuck with G speeds, but all-in-all pretty good.

Back to the support though, it's 4 AM here where I live and I can't sleep OR connect to my wireless. Nobody with any more ideas? I was thinking... should I try to use NDISwrapper?


Yeah, give ndiswrapper a go. If it behaves the same, I think you got a kernel or HW problem. :o

---

### Post by damis648 on 2008-07-09
> **fackamato said:**
> Yeah, give ndiswrapper a go. If it behaves the same, I think you got a kernel or HW problem. :o

Ok, thanks. Will try. :popcorn:

---

### Post by damis648 on 2008-07-09
Hmm... I can't get the driver to switch over to the ndiswrapper one... it keeps starting the connections with the iwl driver... I will look this up and see what I can come up with...

PS At least its working again... :-P for now...

---

### Post by fackamato on 2008-07-09
> **damis648 said:**
> Hmm... I can't get the driver to switch over to the ndiswrapper one... it keeps starting the connections with the iwl driver... I will look this up and see what I can come up with...

PS At least its working again... :-P for now...


You have to unload and blacklist the iwl driver in order for ndiswrapper to work.

Glad to hear it's working :)

---

### Post by damis648 on 2008-07-09
Hmm... I could not get NDISwrapper to work BUT I did find this:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149214/comments/24](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149214/comments/24)
and followed the directions, using the iwlwifi-4965-ucode-228.57.1.21 driver. (The iwlwifi-4965-ucode-228.57.2.21 did not work). It seems to be working after removing the module then re-modprobing. I will use wireless as much as possible over the next couple days and see if this behavior continues after (updating?) the driver.

PS. The reason I put a question mark was I was unsure what the original version with Ubuntu was.

---

### Post by damis648 on 2008-07-09
> **fackamato said:**
> You have to unload and blacklist the iwl driver in order for ndiswrapper to work.

Glad to hear it's working :)

Ahhh... I did not do that... well I would rather use the native driver mentioned in my previous post, so as long as that fixes my problem I hopes I won't have to touch NDISwrapper again. :popcorn: Thank you though, if this driver does not work I will try that. :popcorn:

---

### Post by damis648 on 2008-07-09
After a day of reconnecting and connecting and disconnecting, as well as going to a friend's house and having my wireless work, my problem is solved from the solution two posts above this one. Thanks for everyone's help!

---

### Post by damis648 on 2008-10-03
[UNSOLVED!]

It appears that this has come up again. There seems to be no associated pattern with these random connection problems... It was working last night, but not today. Any more suggestions?:confused:
If I cannot solve this I will order a new card later this month... maybe the card is just bad?

---

