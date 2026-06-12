---
title: "volume control and Rhytmbox missing from notification area after upgrading from 10.04"
date: 2010-10-17
forum: Desktop Environments
---

### Post by ockron on 2010-10-17
Hi all.

I upgraded from 10.04 to 10.10 and since then volume control and Rhythmbox is missing from the notification area.

In fact it seems that the volume control is missing altogether?!

Has this happened to anyone else? and please help me fix it.

Thanx :)

---

### Post by Humphreybas on 2010-10-18
When I was using 10.10 beta the volume control dissapeared suddenly from the notification area. I could just re-add it by doing this:

[HTML]right click panel/add to panel/indicator applet
Hopefully this is what ya need?
[/HTML]
[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9950654&postcount=3](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9950654&postcount=3)

---

### Post by ockron on 2010-10-18
I tried that but I do not have anything relating to volume control or sound in the drop down box.


> **Humphreybas said:**
> When I was using 10.10 beta the volume control dissapeared suddenly from the notification area. I could just re-add it by doing this:

[HTML]right click panel/add to panel/indicator applet
Hopefully this is what ya need?
[/HTML]
[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9950654&postcount=3](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9950654&postcount=3)

---

### Post by ockron on 2010-10-18
Hi all.

No fix for the volume control yet, but on the positive side of the ledger I discovered a fix for Rhythmplayer not displaying in the notification area.

In Rhythmbox, go to Edit > Plugins, and find the Status Icon plugin. Click configure. Change the Status Icon from "Never Visible" to "Always Visible." There are some other options there that you can play around with as well.

I found the fix [here]("http://askubuntu.com/questions/5707/how-to-make-rhythmbox-use-notification-area-instead-of-indicator-applet")

So if someone out there can help me with the volume control I will be very grateful :)

---

### Post by JOHNNYG713 on 2010-10-18
Go to synaptic and try reinstalling indicator applet! Then add to panel.

---

### Post by ockron on 2010-10-18
> **JOHNNYG713 said:**
> Go to synaptic and try reinstalling indicator applet! Then add to panel.

I tried that and still no luck .. maybe I should re-install ubuntu?

---

### Post by elbows on 2010-10-19
I'm having the same problem on a fresh install of 10.10.

Oddly enough, I can run gnome-volume-control-applet from a terminal and it works fine. It's just missing from the Add to Panel... menu.

Does anyone know how the list of panel applets is populated? Maybe there's a config file that can be fixed by hand.

---

### Post by emacine on 2010-10-23
Hey Guys its working on 10.10. I initially had this problem then I figured that I just had to add the indicator applet. I allowed all the updates run but I am not sure whether that made any difference :)

---

### Post by rvkbob on 2010-10-24
> **elbows said:**
> I'm having the same problem on a fresh install of 10.10.

Oddly enough, I can run gnome-volume-control-applet from a terminal and it works fine. It's just missing from the Add to Panel... menu.

Does anyone know how the list of panel applets is populated? Maybe there's a config file that can be fixed by hand.

I've got the same problem with 10.04. My panel applet disappeared and it is nowhere to be found in the list of applets. If anyone figures out what happened and how to fix it, please notify me. Thanks.

---

### Post by maberib on 2010-10-31
> **ockron said:**
> I tried that but I do not have anything relating to volume control or sound in the drop down box.

I first looked at the "add to panel" menu and didn't see anything that looked sound related and called it quits.  If you're doing what I did - you simply want to add the "indicator applet". It adds a number of things to the panel including a volume control.

---

### Post by kavoura on 2010-11-07
> **Humphreybas said:**
> When I was using 10.10 beta the volume control dissapeared suddenly from the notification area. I could just re-add it by doing this:

[HTML]right click panel/add to panel/indicator applet
Hopefully this is what ya need?
[/HTML]
[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9950654&postcount=3](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9950654&postcount=3)



Thanks, that helps. I was looking for something called Volume, Audio or Sound. I would never have thought to look under Indicator!

:P

---

### Post by CR34M3 CR4CK3R on 2011-06-13
For the sake of people finding this in a forum / Google search:

I had the same problem with the indicator applet showing only the mail icon and not the volume control / Rhythmbox icon in 10.10. The following solved the problem for me:

1. Remove indicator applet from panel **[right click on it -> Remove From Panel]**
2. Re-install the sound indicator. In a console:
```
sudo apt-get install indicator-sound
```
3. Add indicator applet to the panel again **[right click on panel -> Add to Panel... -> Indicator Applet -> Add]**

Credit goes to [Jun Auza]("http://www.junauza.com/2010/12/restore-missing-volume-icon-ubuntu.html")

---

