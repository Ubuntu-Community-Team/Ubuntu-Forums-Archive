---
title: "Macbuntu Animations + Dock"
date: 2011-10-05
forum: Desktop Environments
---

### Post by Fasih on 2011-10-05
So I had Ubuntu 11.04 and put MacBuntu on it but it wasn't compatible so  I think some of the features were not working. So then I downgraded and  got Ubuntu 10.10, downloaded Macbuntu and installed it. This is on a  fresh installation of Ubuntu 10.10. Now the Dock at the bottom is slow  as I navigate through it and also, none of the features are working.  only the look is changed. the genie effect isnt there, neither is the  cube or anything else. could there be a reason why it's not working? I  have a NVIDIA GT GeForce 525M graphics card with 6GB of RAM and a i5  processor.

---

### Post by Copper Bezel on 2011-10-05
Do you have the proprietary drivers for the NVIDIA card installed?

If you open the System Monitor, is Compiz running?

---

### Post by Fasih on 2011-10-06
I checked and it's not running, and it won't let me install the NVIDIA driver. It says I'm running an X server.

---

### Post by Copper Bezel on 2011-10-06
What method did you use to attempt to install the driver? It should appear in the list when you open System > Administration > Additional drivers. 

If it's not listed there, you could try _[this]("http://www.ubuntugeek.com/how-to-install-nvidia-260-19-12-drivers-in-ubuntu-10-1010-04-using-ppa.html")_ - a PPA for newer drivers. If you do, though, change the last command like so:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

But really, you didn't need to downgrade to 10.10 (which has older drivers, which apparently don't support your graphics card so that Compiz can't run, etc.) MacBuntu is just a set of package installations and settings adjustments that you can set up manually fairly quickly and easily.

---

### Post by Fasih on 2011-10-06
So should I just upgrade back to 11.04?

---

### Post by Copper Bezel on 2011-10-06
Probably best in the long run, yeah, if you can stomach the hassle. I mean, I know this is probably getting tiresome, but it would be my suggestion. That should bring in support for your graphics card without having to make the MacBuntu tweaks manually, since they're already installed.

Edit: And then we can troubleshoot the parts of the MacBuntu interface that aren't working and get them going again.

---

### Post by Fasih on 2011-10-06
Okay I updated to 11.04 and the dock is smooth now, but I'm still not getting any of the effects like the genie effect or the cube. I checked the system monitor and compiz is there and sleeping.

I have some effects, but the 3D cube isn't working and I cant seem to find the genie effect.

---

### Post by Krytarik on 2011-10-06
> **Fasih said:**
> I have some effects, but the 3D cube isn't working and I cant seem to find the genie effect.
But you know that you need to enable both of them on your own first, right!? As both of them aren't enabled by default - would be ridiculous if it were so, btw. ;-)

For enabling the "Magic Lamp" effect (you call it "genie"), set it up under "CompizConfig Settings Manager -> Animations". If you've done a fresh install, you need to install the package "compizconfig-settings-manager" first.

For enabling the Cube, see this guide, regardless if you are running Unity or not:

[http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Greetings.

---

### Post by Fasih on 2011-10-06
In the animations option, when I click it, there are no animations for selection o.O

---

### Post by Copper Bezel on 2011-10-06
Well, you won't see animations for any given tab, but rules under which they appear. Each of these rules has an animation set to it when you double-click it.

[img]http://dl.dropbox.com/u/17749392/Screenshots/111002/Screenshot-6.png[/img]

Jump over to the minimize tab and double-click the rule listed (there should only be one, "any") and set it to "Magic Lamp" in the drop-down menu. If there isn't a rule, create one (New) and set it to apply to all windows (with just the word "any", without quote marks.)

---

### Post by Fasih on 2011-10-06
Yeah this is what I have shown...
[http://imageshack.us/photo/my-images/802/nothing.png/](http://imageshack.us/photo/my-images/802/nothing.png/)

---

### Post by Krytarik on 2011-10-06
> **Fasih said:**
> Yeah this is what I have shown...
[http://imageshack.us/photo/my-images/802/nothing.png/](http://imageshack.us/photo/my-images/802/nothing.png/)
LOL:P Seems like Macbuntu is happily breaking Compiz in Natty 11.04. Another - but already 'solved' - thread here:

[http://ubuntuforums.org/showthread.php?t=1841311](http://ubuntuforums.org/showthread.php?t=1841311)

Basically following the solution from there, try this:
```
sudo apt-get install --reinstall compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-main compizconfig-settings-manager compizconfig-backend-gconf
```

---

### Post by Fasih on 2011-10-06
^^ Thanks for that! Thank you everyone, Macbuntu is working perfectly fine. It looks so awesome :)

---

