---
title: "No top panel, no launchers 11.10"
date: 2011-10-14
forum: Desktop Environments
---

### Post by francois203 on 2011-10-14
Hi,

After upgrading to Ubuntu 11.10, I can't see the top panel bar or the launchers. I tried resetting the unity and compiz and it worked on my second or third trial. However, as I was changing the parameters in compiz after that, I hit reset default parameters and now I can't see the panels or launchers anymore. I tried to reset the unity and compiz but nothing worked... However, the panel and launchers work in the 2D version.

Any suggestion?

---

### Post by kurt18947 on 2011-10-14
Your graphics system is a little weak, probably.  Many systems won't display Unity 3D until proprietary drivers are enabled. Are there any additional drivers available for your system? You could tap the "super"(windows) key to bring up the dash and type "add". The additional drivers app should be there.  The 2D version is less demanding of the graphics system and I don't see much difference between 2D and 3D.

---

### Post by collisionystm on 2011-10-14
> **francois203 said:**
> Hi,

After upgrading to Ubuntu 11.10, I can't see the top panel bar or the launchers. I tried resetting the unity and compiz and it worked on my second or third trial. However, as I was changing the parameters in compiz after that, I hit reset default parameters and now I can't see the panels or launchers anymore. I tried to reset the unity and compiz but nothing worked... However, the panel and launchers work in the 2D version.

Any suggestion?



do you know what video card you have?

hit alt + F2

type

unity --reset

---

### Post by riwid on 2011-10-14
I have the same problem. Unity 3d worked without problem on 11.04 on my new lenovo e320 with intel hd graphics. 3d-unity actually worked to start with on 11.10 but after changing in compiz manager it stopped working. I can't do anything when I log in. No commands works - I can't start anything. 2d-unity works however.

---

### Post by marcswdb on 2011-10-14
It may be a problem with the flgrx driver, i.e. the conflict between flgrx and radeon. Try to remove everything of flgrx.

---

### Post by ShabZev on 2011-10-14
Same here. After an upgrade from 11.04 to 11.10, Unity 3D worked fine. But some fonts were not aliased, and the font rendering tab in Appearance disappeared, so I looked in other places... I was looking in the Compiz settings and suddenly my desktop went awry.

After relogging there was no launcher. The usual alt-F2 and other shortcuts didn't work either. the only access to a terminal would be via ctrl-alt-F1. I can login and use the desktop with Unity 2D and Gnome 3, though.

As for the graphic card drivers, I've always used the NVidia proprietary drivers without any trouble.

---

### Post by turtle153 on 2011-10-14
I had exactly the same problem, but I could use Ctrl-Alt-T to open a terminal as Alt-F2 didn't work. unity --replace seems to do the trick.

---

### Post by ShabZev on 2011-10-14
Didn't think of ctrl-alt-T! Thanks to that I managed to restore Unity 3D.

After login to the corrupted Unity 3D:
* ctrl-alt-T brings a terminal
* I tried the command "unity --replace" but it seems that it didn't do any good, by itself
* then "ccsm" to open the Compiz settings
* the Unity plugin was disabled, so I enabled it and resolved all the shortcut/behaviour conflicts with the first options ("... anyway")

and it's back!

---

### Post by riwid on 2011-10-14
Enabling unity plugin from terminal worked for me too!

---

### Post by qwill on 2011-10-14
I have the same problem. What is weird is that it's occuring only in one user account. Unity launches ok for all other users.

I tried the unity --reset; I resetted the compiz configs ... nothing.
What worked is to add compiz in the autostart applications (Normally, it should start on its own).

I'm clueless now ...

---

### Post by trekguy on 2011-10-14
ccsm

enable Unity Plugin

Success!!!!  Thank You!!

Whew

---

### Post by ericmo on 2011-10-15
Thanks, ShabZev! The ccsm thing solved my problem.
I was going nuts, did Ctrl+Alt+F1, sudo reboot endless times.

---

### Post by dumitru on 2011-10-15
I had the same problem. unity--reset didn't help, shortcuts were not working. The only thing that helped:

1. Ctrl+Alt+T   (retrieve terminal)
2. Type ccsm  (open CompizConfig)
3. Enable Ubunty Unity Plugin (check the box)

---

### Post by ricardisimo on 2011-10-15
I upgraded to 11.10, and then reinstalled the "Classic" GNOME desktop with
> sudo apt-get install gnome-session-fallback
This worked without issues at work, and I added the launchers I wanted with ALT+right click on the top and bottom panel. Unfortunately, the ALT+right click is not working at home. Nothing, no response. Tested ALT (it works) and my right mouse button (also working). Any clues?

---

### Post by ricardisimo on 2011-10-21
I've been able to grab launchers from the "Applications" and "Places" drop downs, and then drop them either on my desktop or on a panel, but it's real haphazard, not a whole lot of nuance to it, and still no accessibility via ALT+right-click. Any ideas?

---

### Post by jcoles on 2011-10-22
I have to agree, ricardisimo. To get back the Weather widget that I had before the upgrade, I had to add it to the launcher and make 3 attempts to drag it to the top panel before it "took". Then I removed it from the Launcher. What would be wrong with right-click > Add on the top panel? 

Unity takes away more functionality than it adds.

---

### Post by ricardisimo on 2011-10-23
It's slick-looking, I guess.

---

### Post by francois203 on 2011-10-23
ShabZev: Thank you so much, it worked!

I am new to unity because I had disabled it for Ubuntu 11.04. I was wondering if it was possible to close a window from the menu in which all of the windows of an application are shown. For example, if I have 2 windows of google chrome open, i would like to be able to click on the application from the launcher and then close one of them from the window that shows the two wondows without clicking on one of them and then closing it. Is that possible somehow?

Thanks,

François

---

### Post by ricardisimo on 2011-10-25
Still no real progress. Anyone?

---

### Post by dathrien on 2011-10-25
I had the same problem after playing around with ccsm. 
I deleted the /home/"user_name"/.compiz directory, logged out, logged in and everything worked fine.

---

### Post by ricardisimo on 2011-10-25
Thanks, but no such luck. Everything reloaded as before. Now, also, my trash launcher has just disappeared. Something weird going on. Any help appreciated.

---

### Post by ricardisimo on 2011-11-01
Anyone?

---

### Post by ElectricTriangle on 2011-11-06
Bah... I have the exact same problem... install ATI driver in Jockey... reboot... select 'Ubuntu' instead of 'Ubuntu 2D'... log in... performance is TERRIBLE and I notice some minor graphical glitches... change ccsm options... computer crashed... reboot... log in... no top panel, no launcher. I mean, I can get around using the terminal, but this is ridiculous.

Edit : tried Unity --reset and a reboot which resulted in no changes.

---

### Post by ElectricTriangle on 2011-11-06
Opening ccsm in the terminal showed me that Unity was disabled! When I enabled it, ccsm notified me that some key bindings were duplicated, so I changed them. Everything seems to be working now, albeit with some minor graphical glitches... I'm going to keep my fingers crossed.

---

### Post by ricardisimo on 2011-11-09
But I want Unity disabled. I want "Ubuntu Classic" functioning the way it used to (and the way it is in fact functioning on my work computer.) Should I still be poking around in ccsm?

---

### Post by ElectricTriangle on 2011-11-11
> **ricardisimo said:**
> But I want Unity disabled. I want "Ubuntu Classic" functioning the way it used to (and the way it is in fact functioning on my work computer.) Should I still be poking around in ccsm?

Oh, I was just responding to the thread topic. I know that the forum admins here will indeed close a topic if it skews too far from the topic line. Unfortunately, I can't really help you at present, I've never used gnome-fallback at all under 11.10. If you opened a new thread you'd probably have more people responding to your issue, just a thought. I'd definitely be willing to test some things to help you out.

---

### Post by oldos2er on 2011-11-11
> **ricardisimo said:**
> But I want Unity disabled. I want "Ubuntu Classic" functioning the way it used to (and the way it is in fact functioning on my work computer.) Should I still be poking around in ccsm?

Gnome2 is deprecated, Gnome3/Unity is the default desktop environment for Ubuntu, and there's no going back. Some folks have switched to either Xfce, Lxde, or KDE.

You could install 10.04 LTS which still uses Gnome2, and will be supported until April 2013; or Linux Mint which is going to be using a combination of Gnome2 and Gnome3 ([http://www.theregister.co.uk/2011/11/07/linux_mint_12_gnome_3/](http://www.theregister.co.uk/2011/11/07/linux_mint_12_gnome_3/)), but in my opinion either of those solutions is delaying the inevitable. Your choice.

---

### Post by ricardisimo on 2011-11-17
Uggh... I was hoping you wouldn't say that. OK, thanks for the reply.

---

