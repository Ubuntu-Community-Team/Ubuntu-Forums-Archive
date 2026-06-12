---
title: "Changes to fglrx drivers?"
date: 2007-09-02
forum: Desktop Effects &amp; Customization
---

### Post by Romanus81 on 2007-09-02
When I first got Ubuntu I was able to get compiz fusion working easily by using these two Howto's:
[Installing Ubuntu 7.04: ATI X**** Cards]("http://ubuntuforums.org/showthread.php?t=414194")
[How To : Compiz Fusion for ATI cards + Xgl in Feisty]("http://ubuntuforums.org/showthread.php?t=488385&highlight=glx")
About two weeks ago I had to reinstall ubuntu, I did nothing different other than these two howto's, I did see [this]("http://ubuntuforums.org/showthread.php?t=500930&highlight=fglrx+mesa") thread, which several users said we could fix it by going back to the older drivers. How do I do this? Is there another reason why I can't get compiz fusion working?

---

### Post by ricardoec on 2007-09-02
A lof of water has gone under the bridge and expect a lot in the next few days.

I see that you are usng the OpenSoruce drver. I had to go to the ATI binaries 8.39.4) to get my XGL session running.

A new version of the Open drivers are supposed to be coming but until then... go to manual instalation Howto. I dont reccomendo otherways.

Cheers

---

### Post by michael37 on 2007-09-02
I can think of two reasons why your CF is not running.

1. Setting up Xgl is very tricky and error prone.  Unless you are 1000% sure that you duplicated all steps, simply try a reinstall.  It may just work on the second try.

2. There were several reports of newer fglrx drivers (esp installed with Envy from ATI latest source) breaking CF.  Unless you are running a awfully rare video card, the Fiesty Fawn fglrx video driver (version 8.34, provided by restricted drivers manager) works with CF.  That's what I use.

---

