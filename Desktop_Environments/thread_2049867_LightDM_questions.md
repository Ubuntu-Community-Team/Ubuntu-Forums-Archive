---
title: "LightDM questions"
date: 2012-08-29
forum: Desktop Environments
---

### Post by JKyleOKC on 2012-08-29
I've searched and found the way to change the lightdm background image, but still have a few questions about other properties:

The configuration files include mention of a "Greybar-lightdm" theme, but I've not found any other themes suitable for lightdm to replace it. The existing dark dialog with light type doesn't go well with my favorite image, so how can I change to a light background in the dialog and dark type? Is there a list of alternate themes, or even a file somewhere that I can edit? Or can I use any GTK theme in this area, not necessarily one built for lightdm?

Also, on logging out or shutting down the system, I get a dialog that times out for 30 seconds. That's okay but I would like to shorten the period. Where is the script or configuration file that controls this interval?

---

### Post by Toz on 2012-08-29
> **JKyleOKC said:**
> I've searched and found the way to change the lightdm background image, but still have a few questions about other properties:

The configuration files include mention of a "Greybar-lightdm" theme, but I've not found any other themes suitable for lightdm to replace it. The existing dark dialog with light type doesn't go well with my favorite image, so how can I change to a light background in the dialog and dark type? Is there a list of alternate themes, or even a file somewhere that I can edit? Or can I use any GTK theme in this area, not necessarily one built for lightdm?
lightdm themes are called greeters. By default, Xubuntu uses the lightdm-gtk-greeter. Unity, on the other hand, uses the unity-greeter. You can install other greeters and use them. To do so, install the package and change the "greeter-session=" line in /etc/lightdm/lightdm.conf file to match the installed greeter. So for example, to use the unity-greeter in xubuntu:
```
sudo apt-get install unity-greeter
gksu leafpad /etc/lightdm/lightdm.conf
.....
..and set
..greeter-session=unity-greeter
.....
..and test with
lightdm --test-mode
```It looks like the *buntus come with unity-greeter, lightdm-gtk-greeter, lightdm-kde-greeter and lightd-webkit-greeter in the official repositories. I've also come across references to a crowd-greeter, but you may have to find the source and install it.

You could also edit the existing greeter files (for lightdm-gtk-greeter look at /usr/share/lightdm-gtk-greeter/greeter.ui) or you could create your own greeter (see: [http://www.mattfischer.com/blog/?p=5]("http://www.mattfischer.com/blog/?p=5")).

This link may also help: [https://wiki.ubuntu.com/LightDM]("https://wiki.ubuntu.com/LightDM").

> Also, on logging out or shutting down the system, I get a dialog that times out for 30 seconds. That's okay but I would like to shorten the period. Where is the script or configuration file that controls this interval?

Apparently, this 30 second delay is embedded in the code and the only way to currently change it is to make the change in the code and recompile.

---

### Post by JKyleOKC on 2012-08-29
I did some detailed searching, using "sudo find -iname Greybird-lightdm" to locate the actual theme directory, and there found that it's apparently a GTK-3.0 theme that was simply tweaked from Greybird to better handle the widgets used by lightdm.

I tried backing up the active greeter in /etc/lightdm, then edited it to use the "Redmond" theme instead and tried a "sudo service lightdm restart" to test it (didn't know, at that time, about the --test option). It shut down the session as expected, but failed to start up again. I then went to TTY2, logged in, and copied the backup of the original back over the modified greeter. That brought everything back again.

That's when I discovered that Redmond is apparently a GTK-2.0 theme rather than 3.0, and apparently lightdm requires 3.0.

However I'll take your suggestion and try a few other greeters; is there any place that shows screen shots of them to help me decide which to try first?

Many thanks for the additional leads. It's always fun to be a relatively early adopter; this new box uses UEFI, which made getting it to dual-boot into an adventure, and I've still not managed to get my printers working properly from it. Those are problems for another day, though...

---

### Post by Toz on 2012-08-29
> **JKyleOKC said:**
> 
However I'll take your suggestion and try a few other greeters; is there any place that shows screen shots of them to help me decide which to try first?
Other than google, I don't know of any sites. The unity-greeter is probably the best of them. The webkit greeter is very basic and the kde greeter brings in a boatload of kde dependencies.

Crowd-greeter looks interesting: [http://www.openews.net/2011/developer-demo-lightdm-3d-animation-login-screen/]("http://www.openews.net/2011/developer-demo-lightdm-3d-animation-login-screen/"), but it appears that the package is only for 11.10.

---

### Post by Toz on 2012-08-29
> **JKyleOKC said:**
> I did some detailed searching, using "sudo find -iname Greybird-lightdm" to locate the actual theme directory, and there found that it's apparently a GTK-3.0 theme that was simply tweaked from Greybird to better handle the widgets used by lightdm.

I tried backing up the active greeter in /etc/lightdm, then edited it to use the "Redmond" theme instead and tried a "sudo service lightdm restart" to test it (didn't know, at that time, about the --test option). It shut down the session as expected, but failed to start up again. I then went to TTY2, logged in, and copied the backup of the original back over the modified greeter. That brought everything back again.

That's when I discovered that Redmond is apparently a GTK-2.0 theme rather than 3.0, and apparently lightdm requires 3.0.

Yes, you're right. I've installed a number of gtk3 themes and currently use the Bluebird theme ([http://shimmerproject.org/project/bluebird/]("http://shimmerproject.org/project/bluebird/")). I set:
```

theme-name=Bluebird

```
...in /etc/lightdm/lightdm-gtk-greeter.conf and the login screen looks better (lighter colours).

---

### Post by JKyleOKC on 2012-08-30
Changing to the Bluebird theme did exactly what I wanted. Many thanks!

EDIT: Also I discovered that the "lightdm --test-mode" option requires an additional dependency on my system, so I simply tried logging out to see what would happen. That worked. Maybe this will help others down the way...

---

### Post by Toz on 2012-08-30
> **Toz said:**
> Apparently, this 30 second delay is embedded in the code and the only way to currently change it is to make the change in the code and recompile.

Just had a VM of Xfce 4.10 up and running. You can disable the 30 second timeout if you un-check the option to display a confirmation dialog. This is new in 4.10.

---

### Post by JKyleOKC on 2012-08-30
Do you have a PPA address for Xfce 4.10 or would I have to build it from source?

---

### Post by Toz on 2012-08-30
Here is a Web Upd8 article and PPA info for installing 4.10 on 12.04 ([http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html]("http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html")). According to your info, you're using 10.04 - this PPA is for 12.04 only.

PPA is here: [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10]("https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10")

---

### Post by JKyleOKC on 2012-08-30
My main production machine is still on Lucid, but the new box is using 12.04.1 and I will probably be converting the production machine before much longer (as soon as I feel comfortable with the changes involved).

Thanks for the PPA reference!

---

### Post by rickm1945 on 2012-08-31
Is there a theme for Ubuntu 12.04 that is more refreshing than the Dull black and grey?  I'm running Cinnamon Desktop.

---

### Post by vasa1 on 2012-08-31
> **rickm1945 said:**
> Is there a theme for Ubuntu 12.04 that is more refreshing than the Dull black and grey?  I'm running Cinnamon Desktop.
Wrong thread?

---

