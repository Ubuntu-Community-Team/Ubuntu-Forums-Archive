---
title: "splash screen won't display after login"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by What_the_deuce on 2007-10-30
Hello

Minor glitch i have encountered with Ubuntu 7.10

The usual Ubuntu gnome splash screen won't display after I log in. This may be to do with XGL, but I can't imagine why

Any help would be great, even if it was just pointing me in the direction of where the image is located, so I can add it myself under Preferences -> Splash Screen

Thanks all!

---

### Post by russianbandit on 2007-10-30
I'm seeing the same problem.
I tried doing some searches and haven't found anything that works yet.

---

### Post by smartboyathome on 2007-10-30
It was deliberately removed because it was causing the system to log in way slower.

---

### Post by russianbandit on 2007-10-30
It just doesn't seem right to be presented with a beige background for like 10 seconds after the login.
I much better preffered to see some kind of visual feedback (the splash and the loading progress).
Is this a permanent removal?

---

### Post by smartboyathome on 2007-10-31
> **russianbandit said:**
> It just doesn't seem right to be presented with a beige background for like 10 seconds after the login.
I much better preffered to see some kind of visual feedback (the splash and the loading progress).
Is this a permanent removal?

"They are looking for a splash screen that doesn't take up as many resources." I don't know if it is permanent.

---

### Post by FuturePilot on 2007-10-31
Try this
```
gconftool-2 -t bool -s /apps/gnome-session/options/show_splash_screen true
```

---

### Post by khanh_coltech on 2007-10-31
Or try this:
Alt+F2 -> type: gconf-editor -> select apps -> select gnome-session -> select options -> tick 
in "show-splash-screen"

---

### Post by sweetsinse on 2007-10-31
the beige background i dont think has anything to do with the splash screen.  to change this:

[edit the gdm.conf file, guaranteed to work]
**sudo gedit /etc/gdm/gdm.conf**
{change BackgroundColor and GraphicalThemedColor to whatever you want, black is #000000}

[i have read that editing this will accomplish the effect also]
**sudo gedit /etc/gdm/PreSession/Default**
{toward the end of the file you will see a comment (#) that says "# Default value" change BACKCOLOR to whatever value you like, again black is #000000}

---

### Post by rykel on 2007-11-05
Hi,

Thinking that the ugly GNOME "foot" splash was placed in my system by error, I deleted by "**sudo rm /usr/share/pixmaps/splash/gnome-splash.png**" but after reading your postings, then I realised that the GNOME Splash screen was DISABLED by purpose, right?

Then, how do I get back the png file should it be enabled by Ubuntu devs down the road? Will Synaptic place a fresh copy of the splashscreen into the folder again then?

---

### Post by FuturePilot on 2007-11-05
> **rykel said:**
> Hi,

Thinking that the ugly GNOME "foot" splash was placed in my system by error, I deleted by "**sudo rm /usr/share/pixmaps/splash/gnome-splash.png**" but after reading your postings, then I realised that the GNOME Splash screen was DISABLED by purpose, right?

Then, how do I get back the png file should it be enabled by Ubuntu devs down the road? Will Synaptic place a fresh copy of the splashscreen into the folder again then?
You can get the Feisty one back by installing feisty-session-splashes
And yes it was disabled by default. They thought it was slowing down the login time. Although I have not seen any proof of this.

---

### Post by lattmau on 2007-11-07
after I login, my screen becomes black with an **X** cursor and about 30 seconds - 1min later, my desktop appears.

is this what you guys are experiencing?

---

### Post by What_the_deuce on 2007-11-08
Hrm, i have managed to more or less solve this. Firstly, I installed guitweak session in add/remove

following this, i went to synaptic and installed "Feisty session splashes" or something similar. Just search "Feisty", its one of the only options.

Then, opening up guitweak session, find the splash you want.

When you next login, a nice Ubuntu splash should display.

---

### Post by Forlong on 2007-11-08
> **lattmau said:**
> after I login, my screen becomes black with an **X** cursor and about 30 seconds - 1min later, my desktop appears.
That's because you are using Xgl.

---

### Post by lattmau on 2007-11-08
> **Forlong said:**
> That's because you are using Xgl.

yea, i finally figured that out last night.  

what does running Xgl mean?   i installed it because i needed it to get compiz-fusion working, but I don't really understand it.  

could someone also explain what the different sessions are at the login window ? (i know i'm running xscript or xglscript or something like that and theres options for gnome)

---

### Post by Forlong on 2007-11-08
> **lattmau said:**
>  what does running Xgl mean?   i installed it because i needed it to get compiz-fusion working, but I don't really understand it. 
You need it only when using the proprietary fglrx driver from ATI, because ATI doesn't support AIGLX until their very latest version of the driver (and I might add not very well).
It's kind of an alternate X-server that makes use of openGL for Compiz.
> **lattmau said:**
> could someone also explain what the different sessions are at the login window ? (i know i'm running xscript or xglscript or something like that and theres options for gnome)
If you're on Gutsy you shouldn't need those anymore. Just log in to your regular GNOME session.

---

### Post by lattmau on 2007-11-08
I thought in Gutsy, if you installed xserver-xgl, it automatically logs into Xgl.  I don't think my default login is in Gnome.

If Xgl is only for Ati, did i do something wrong?  I actually have Nvidia card.  Its a Geforce 2 Ti and I enabled the legacy drivers for it.  When I ran compiz in terminal, it stated that Xgl was not found, which is the reason why I installed it in the first place.  After installing xserver-xgl, compiz works.

I'm just unclear what the difference between running Xgl session or Gnome session, because it appears I'm running Xgl (in order for compiz to be working).

---

### Post by Forlong on 2007-11-08
> **lattmau said:**
> I thought in Gutsy, if you installed xserver-xgl, it automatically logs into Xgl.
That's correct.
> **lattmau said:**
> I don't think my default login is in Gnome.
Sorry, I was assuming it was.
> **lattmau said:**
> If Xgl is only for Ati, did i do something wrong?  I actually have Nvidia card.  Its a Geforce 2 Ti and I enabled the legacy drivers for it.  When I ran compiz in terminal, it stated that Xgl was not found, which is the reason why I installed it in the first place.  After installing xserver-xgl, compiz works.
Just because the script tells you that Xgl is not present doesn't mean you need to install it.
But to be frank, that's not the proper thread for this. And if your OK with Xgl then stick with it. :)

---

### Post by FuturePilot on 2007-11-08
If you have Nvidia, that XGL error is normal. You don't need it. Unless if you're using the old Legacy drivers (71xx) because I don't think those have the compositing abilities.

---

### Post by lattmau on 2007-11-08
> **FuturePilot said:**
> If you have Nvidia, that XGL error is normal. You don't need it. Unless if you're using the old Legacy drivers (71xx) because I don't think those have the compositing abilities.

Yeah, compiz wouldn't work without Xgl.  Thanks for the clarification.

---

### Post by Eddie Wilson on 2007-11-08
Disabled in 7.10. If you want them then download and install Gnome Splash found in Synaptic. Then you have the splash screens and an interface in Preferences to use for setting them up.
Eddie

---

