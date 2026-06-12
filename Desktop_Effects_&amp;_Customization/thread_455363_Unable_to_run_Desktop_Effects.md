---
title: "Unable to run Desktop Effects"
date: 2007-05-26
forum: Desktop Effects &amp; Customization
---

### Post by Jilbert on 2007-05-26
I've installed my ATI graphics card and the beryl manager but still I cannot run the Desktop effects and all I'm getting is an error message The "Composite extension is not available" what could be the problem? thanks..

---

### Post by Ub1476 on 2007-05-26
You neede to run in a XGL/AIXGL session. What graphic card do you have and what Beryl version did you install?

```
beryl --version
```

---

### Post by Jilbert on 2007-05-27
thanks. ATI Radeon Express 1100 and beryl version is beryl-core 0.2.1

Here is my laptop specs
AMD Turion 2.0 Ghz
1.42 Gb RAM the rest is shared

Thanks.

I hope you can help me solve my problem.

---

### Post by pnx031 on 2007-05-27
beryl-core 0.2.0
I have the same problem on an 9800xt ;S

---

### Post by WarLocke on 2007-05-27
have you guys read this thread:

[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

---

### Post by Jilbert on 2007-05-27
yes I did. 

I found this one

Unsupported

    * X1300 / R515 based cards.
    * X1600 / R530 based cards.
    * X1800 / R520 based cards.
    * X1900 / R580 based cards.

But my graphics card is X1100 and its not on the list. do you think it the page should be updated?

thanks..

---

### Post by WarLocke on 2007-05-27
are you running an XGL/AIXGL session?  You won't get anywhere if you don't do that first.  

something you might want to read:
[http://ubuntuforums.org/showthread.php?t=362525](http://ubuntuforums.org/showthread.php?t=362525)

---

### Post by Jilbert on 2007-05-27
aha! thanks man I stared using AIXGL but my x server failed to load. I ended up reinstalling the fglx.

I'll surely try the link. it looks like the thread started was able to fix the problem. ill try it later. hee hee. am at work. I dont want my boss catch me playing with my laptop.
:D

---

### Post by Ub1476 on 2007-05-27
I followed the link above, and I see the guide didn't work for you, Jilbert. First, uninstall beryl:

```
sudo aptitude remove beryl beryl-core beryl-manager beryl-plugins beryl-plugin-data beryl-settings beryl-setting-bindings libberyldecoration0 libberylsettings0 libemeraldengine0
```

Follow this guide: [Linky]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29")

Scroll down to ...Alternate method: Using closed source FGLRX drivers from ATI... and follow the guide from there. This will install XGL (AIXGL didn't work for you, right?) and Beryl version 0.2.0. If this works, and you manage to run Beryl, do not update it to v. 0.2.1! It will crash then:p

Here's a thread with people with the same card as you trying to install beryl, some of them succsesful.:)

[Thread]("http://www.rage3d.com/board/showthread.php?t=33876748")

---

### Post by zasf on 2007-05-27
aiglx doens't work with ati proprietary driver fglrx. You need to get xgl working for compiz/beryl, see

[https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

Matteo

---

### Post by Jilbert on 2007-05-28
hi there.. I almost tried everything. including downgrading my beryl manager from 0.2.1 to 0.2.0 but still it didnt work.. 

here are the things that I did. 
1.) I uninstalled beryl from add/remove software
2.) I uninstalled the ATI driver.

then 
1.) reinstalled the ATI driver
2.) reinstalled beryl and had it downgraded to 0.2.0.

I was able to run beryl but it doesn't do the effects. 
what is the best Thing that I will do?
Do you think reinstalling my whole system will help?

sorry I'm noobbie

---

### Post by Jilbert on 2007-05-28
Hi! I was able to get it working with XGL but I can't do it on beryl. The screen gets white everytime I open the beryl manager.

Hmm..

---

### Post by Ub1476 on 2007-05-28
Alright, you are logged in in XGL, right? 

On the login screen >Sessions>Gnome with XGL (or Beryl with XGL, or whatever it stays there)

Right click on the beryl icon, and choose Beryl as your windows manager.

Have you done all that?

---

### Post by nevernamed on 2007-05-28
I couldn't find a place to put this. I was using the built in desktop effects that come with Fiesty, and it asked me to activate the nvidia driver. I said yes, it downloaded the necesary files. It said that I had to run desktop effects again when the new nvidia driver was running. I rebooted. Everything worked fine until the login screen was supposed to come up. The screen went totally black. I still heard the African drums, but I was unable to do anything. control+alt+backspace restarted x and nothing happened. I can boot to the recovery mode... but I really don't know what to do. Does anybody know why this has happened (i heard something about a bug in the nvidia driver in a different thread) and how to correct it? Thanks in advance.

---

### Post by Ub1476 on 2007-05-28
> **nevernamed said:**
> I couldn't find a place to put this. I was using the built in desktop effects that come with Fiesty, and it asked me to activate the nvidia driver. I said yes, it downloaded the necesary files. It said that I had to run desktop effects again when the new nvidia driver was running. I rebooted. Everything worked fine until the login screen was supposed to come up. The screen went totally black. I still heard the African drums, but I was unable to do anything. control+alt+backspace restarted x and nothing happened. I can boot to the recovery mode... but I really don't know what to do. Does anybody know why this has happened (i heard something about a bug in the nvidia driver in a different thread) and how to correct it? Thanks in advance.

You probably need to uninstall the drivers, but I don't know much about Nvidia, so can't help you out, sorry.:(

Start a new thread. You will more response then.

---

### Post by nevernamed on 2007-05-28
Thanks for reading anyway!

---

### Post by Jilbert on 2007-05-29
> **Ub1476 said:**
> Alright, you are logged in in XGL, right? 

On the login screen >Sessions>Gnome with XGL (or Beryl with XGL, or whatever it stays there)

Right click on the beryl icon, and choose Beryl as your windows manager.

Have you done all that?


Yes, I am logged in to Gnome with XGL. Here is what I observed. I was able to run the desktop effects smoothly. I was also able to run beryl 0.2.0 after i unloaded the desktop effects. I even see the beryl splash screen but the screen gets totally white or blank right after until i close the X and start it again using statx from the terminal.

any suggestions?

---

