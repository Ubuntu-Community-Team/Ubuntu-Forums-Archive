---
title: "'Desktop effects could not be be enabled&quot; on X1600...why?"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by Bazirker on 2007-04-25
I get the message 'Desktop effects could not be be enabled" (sic)  when I try to enable them in Feisty on my notebook w/ ATI mobility X1600.  I installed the drivers with Envy yesterday so I'm pretty sure I have official, working ATI drivers.  Why won't desktop effects work?

---

### Post by HaoTian on 2007-04-25
Because the ATI mobility drivers do not support the method used.  This is an ongoing problem.

I'm in the same boat as you.  There is the option of installing Beryl on top of Feisty (it's a bit of work to do, though, since you have to use a different version than is available through Ubuntu's synaptic manager), and using an XGL session to enable very cool desktop effects.

I have the exact card you do in my laptop, so I know it can be done... my problem was that I use an external LCD panel.  I couldn't get the XGL session to recognize the two different resolutions (laptop LCD = 1280x800, LCD panel = 1280x1024) and instead it was using one huge desktop that was 2560x1024... which would work, but I have a large "dead" area on the laptop screen below the 800 pixels to lose things :(

I did have it running for a bit, but with that dead area just didn't see any reason to keep it... it sure was cool, though :)

---

### Post by ronocdh on 2007-04-26
> **Bazirker said:**
> I get the message 'Desktop effects could not be be enabled" (sic)  when I try to enable them in Feisty on my notebook w/ ATI mobility X1600.  I installed the drivers with Envy yesterday so I'm pretty sure I have official, working ATI drivers.  Why won't desktop effects work?
I, like Hao Tian, also have an ATI Radeon Mobility X1600. Are you positive your drivers are giving you 3D acceleration? What's the output of **fglrxinfo**? I personally don't like Envy very much, at least not for ATI stuff.

---

### Post by Bazirker on 2007-04-26
fglrxinfo:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

According to my Catalyst Control Center, I'm running driver version 8.35.5.

---

### Post by wconstantine on 2007-04-26
Well it should stand Your real manufacturer there and not Mesa. Try reinstalling the driver, I used Envy for that. I had x1900 and I got the same message. Then I installed XGL and everything worked fine.

---

### Post by Bazirker on 2007-04-26
OK, uninstalled old drivers and installed 8.36.5 using method 2: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

fglrxinfo gives me the same output as before, problem still isn't fixed.  So, install XGL?  I'll try that.

---

### Post by ericdegen on 2007-05-19
Having this same issue with an HP NC8430 (Ati X1600) are there any other threads with resolution?

Thanks,

---

### Post by Ub1476 on 2007-05-19
Why don't you just install drivers from "Restricted Drivers Manager"?

```
 glxinfo | grep direct
```

Also, direct rendering: yes:)

---

### Post by Bazirker on 2007-06-25
OK I finally got my drivers installed with 3D acceleration working.  flgrxinfo's output is good, and  glxinfo | grep direct tells me I have direct rendering.

fglrxinfo's output:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6473 (8.37.6)
```

It still doesn't work...why?  Why isn't 3D acceration enough?  Are ATI's drivers really that bad?

---

### Post by asnd16 on 2007-06-30
o I have this issue but it wored before and now I am unable to get it working? 

> Direct Renering: NO

I have not restricted drivers on my system.

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2

---

### Post by Ultra Magnus on 2007-06-30
Hey - I had problems of this sort - I have X1400 - I used a guide on [www.mylittleubuntuguide.com](www.mylittleubuntuguide.com) to get it too work - I have to use a script to create a separate session with XORG to enable desktop effects.

---

### Post by toasty_ghosty on 2007-07-01
I have a X1900 and I have updated and are using the restricted drivers. But my fglrxinfo reads:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

So how can I fix this? I take it that means I'm not using ATI drivers? Even though I'm using the restricted drivers.

---

### Post by Bazirker on 2007-07-02
OK, I got it working on my system!  I just used several guides to set up my graphics drivers with 3D support, then XGL, and finally Compiz (Ubuntu calls it "desktop effects").  Each of these steps went essentially exactly as documented in these guides; I didn't have to do any tinkering outside of what these guides detail.  I did try several different guides for things, and these happened to be the ones that worked for me.

Step 1:  I installed proprietary ATI drivers (fglrx) using method 2 from this guide (method 1 didn't work for me).  Just because you have fglrx installed doesn't mean you've got 3D support!!!  This method is the only one that got fglrx installed AND got me 3D acceleration:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Step 2:  Get XGL up and running.  I did this using this guide, using method A for Gnome and ATI:
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

Step 3:  Turn on Desktop Effects, aka Compiz.  I did this by simply going to System > Preferences > Desktop Effects and clicking "Enable."  If you try this and get an error message of some sort, make sure you have the composite extension enabled in xorg.conf.

Enter this code to get to xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```
Find this section, and make sure it looks like this, namely that it says "Enable"
```
Section "Extensions"
	Option	    "Composite" "Enable"
EndSection
```

Now I have desktop effects working!  Play around with things, there's lots of cool stuff hidden here and there.  I think that's everything I did...really not too bad, just make sure you take the time to read what the guides are telling you to do!  Don't rush through, you'll likely make an error and have no idea what went wrong.

I also found these pages helpful in tinkering with compiz:
[http://compiz.org/Ubuntu_Installation_Guide](http://compiz.org/Ubuntu_Installation_Guide) (specifically the "Configuring Compiz" section at the bottom...I really like the compiz-settings utility)
[https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz](https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz)

---

### Post by toasty_ghosty on 2007-07-04
Thanks. Hopefully this works..

---

### Post by BL00dFox on 2007-07-05
> **toasty_ghosty said:**
> Thanks. Hopefully this works..

> **Bazirker said:**
> OK, I got it working on my system!  I just used several guides to set up my graphics drivers with 3D support, then XGL, and finally Compiz (Ubuntu calls it "desktop effects").  Each of these steps went essentially exactly as documented in these guides; I didn't have to do any tinkering outside of what these guides detail.  I did try several different guides for things, and these happened to be the ones that worked for me.

Step 1:  I installed proprietary ATI drivers (fglrx) using method 2 from this guide (method 1 didn't work for me).  Just because you have fglrx installed doesn't mean you've got 3D support!!!  This method is the only one that got fglrx installed AND got me 3D acceleration:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Step 2:  Get XGL up and running.  I did this using this guide, using method A for Gnome and ATI:
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

Step 3:  Turn on Desktop Effects, aka Compiz.  I did this by simply going to System > Preferences > Desktop Effects and clicking "Enable."  If you try this and get an error message of some sort, make sure you have the composite extension enabled in xorg.conf.

Enter this code to get to xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```
Find this section, and make sure it looks like this, namely that it says "Enable"
```
Section "Extensions"
	Option	    "Composite" "Enable"
EndSection
```

Now I have desktop effects working!  Play around with things, there's lots of cool stuff hidden here and there.  I think that's everything I did...really not too bad, just make sure you take the time to read what the guides are telling you to do!  Don't rush through, you'll likely make an error and have no idea what went wrong.

I also found these pages helpful in tinkering with compiz:
[http://compiz.org/Ubuntu_Installation_Guide](http://compiz.org/Ubuntu_Installation_Guide) (specifically the "Configuring Compiz" section at the bottom...I really like the compiz-settings utility)
[https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz](https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz)


I can't thank this person enough. (S)he provided a perfect set of links which helped me to set everything up. Thankyou.

---

### Post by toasty_ghosty on 2007-07-07
Alright. I did all that, but when I change session and type in my user name and info and logon, the screen goes black, and comes back to my login screen. So I log in, and try to start desktop effects, and nothing...I've looked at everything over and can't find anything.

---

### Post by Bazirker on 2007-07-07
I'm no expert, but that sounds like XGL is pooping out on you, I don't think it works without 3D going.  Do you have 3D acceleration running on your graphics card?  That was the hard part for me...what's your fglrxinfo output?

---

### Post by toasty_ghosty on 2007-07-14
I am not at my rig right now, but I do know that 3D is working. It's a quite odd problem. I have tried to follow every thing on the forum but I still cannot get anything working.

---

