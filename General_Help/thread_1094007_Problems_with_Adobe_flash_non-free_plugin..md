---
title: "Problems with Adobe flash non-free plugin."
date: 2009-03-12
forum: General Help
---

### Post by azmo35 on 2009-03-12
Hi, to all my firefox start work strange at few weeks turning gray for long time and the scroll up and down gos slow when gray moves alone up and down,i looked on synaptic and removed this Adobe flash player non-free it works ok but firefox ask me to add this plugin for media content. I have removed this "SWFDEC/LIDSWFDEC 0.6-90" and "AFP non-free" firefox still work. For display all content firefox need this plugin, i have installed in the past the version 10 but not works, reinstall the non-free came the problem.
Help me please to solve this,many thanks azmo.:(

---

### Post by skymera on 2009-03-12
Do you run 32bit or 64bit Ubuntu?

---

### Post by azmo35 on 2009-03-12
Sorry 32bit.

---

### Post by azmo35 on 2009-03-13
Help me please.Thanks in advance.

---

### Post by KayakJim on 2009-03-13
My flash in Firefox 3 also started acting strange about 2 weeks ago on Ubuntu 8.10 32-bit. Unfortunately I haven't had time to look into the matter.

---

### Post by azmo35 on 2009-03-17
Hello is there any body that can help me on this mater,thanks azmo.

---

### Post by azmo35 on 2009-03-20
Hi,again i think i found the problem, and problem is that i have adobe flash non-free and adobe flash 10, so i removed the latest and the problems went away, for now is solved,thanks.

---

### Post by OrangeCrate on 2009-03-20
> **azmo35 said:**
> Hi,again i think i found the problem, and problem is that i have adobe flash non-free and adobe flash 10, so i removed the latest and the problems went away, for now is solved,thanks.

I may be misunderstanding your suggested solution...

If you said, that you uninstalled flash non-free, and installed Adobe flash plugin, that would be the correct solution. Anyway, that's what I did, and I no longer have any flash issues on Hardy.

---

### Post by azmo35 on 2009-03-20
Well that is what i deed but Firefox ask me for flash plugin and leads me to adobe site to install the latest 10.... but with it intalled it kip asking for the flash plugin so again i have to install the non-free and i removed the latest adobe 10.... maybe now is clear!):P

---

### Post by OrangeCrate on 2009-03-20
> **azmo35 said:**
> Well that is what i deed but Firefox ask me for flash plugin and leads me to adobe site to install the latest 10.... but with it intalled it kip asking for the flash plugin so again i have to install the non-free and i removed the latest adobe 10.... maybe now is clear!):P

Now it is. Go to synaptic and search for Adobe flashplugin. This will be the one you want, not the one from Adobe's website.

Package description:

> Adobe Flash Player plugin version 10

This package will download the Flash Player from Adobe. It is a
Netscape/Mozilla type plugin. Any browser based on Netscape or Mozilla can use
the Flash plugin. This package officially supports the following browsers:

Firefox 2.x, Firefox 3.x, SeaMonkey 1.11

Uninstall flash non-free, and then install this package. (Firefox should not be running.)

When you're done, you should have Shockwave version 10 installed in Firefox. (Shockwave Flash 10.0 r22) Check your plugins to be sure.

Edit:

You can also find the new flash package by clicking on  "Status" in the left column in Synaptic, and then clicking on "New in repository". The Adobe flash plugin package should be the first listing.

---

### Post by azmo35 on 2009-03-20
Thanks for the infu i found that in some web sites the content for the flash dosen't work so i will try,azmo.

---

### Post by azmo35 on 2009-03-20
[PHP]When you're done, you should have Shockwave version 10 installed in Firefox. (Shockwave Flash 10.0 r22) Check your plugins to be sure.

Edit:

You can also find the new flash package by clicking on  "Status" in the left column in Synaptic, and then clicking on "New in repository". The Adobe flash plugin package should be the first listing.[/PHP] well i have to say this solve part of the problem because firefox continues ask me for adobe flash in some sites and under tools/ add-ons/ plugins no shockwave flash 10.0 r22 installed, any sugestions thanks.

---

### Post by OrangeCrate on 2009-03-20
> **azmo35 said:**
> [PHP]When you're done, you should have Shockwave version 10 installed in Firefox. (Shockwave Flash 10.0 r22) Check your plugins to be sure.

Edit:

You can also find the new flash package by clicking on  "Status" in the left column in Synaptic, and then clicking on "New in repository". The Adobe flash plugin package should be the first listing.[/PHP] well i have to say this solve part of the problem because firefox continues ask me for adobe flash in some sites and under tools/ add-ons/ plugins no shockwave flash 10.0 r22 installed, **any sugestions thanks**.

Honestly, no. If you're not finding it in the list of plugins, you didn't install it. I've given you the instructions as clearly, and as succinctly as I can. They should be all you need.

---

### Post by azmo35 on 2009-03-20
Don't be mad with me but i'm very good follow instutions and like you saied is on synaptic as the first i closed firefox removed non-free and then install AF 10.0.22.87-22 but no shockwave flash is there something that i can change,again thanks for the sugestions,azmo.

---

### Post by azmo35 on 2009-03-20
OrangeCrate i been mess arrond and manage the plugin shockwave flash but is 9.0 r159 not the 10.0 r22 but for now i still have to use the non-free.
[http://wiki.ubuntu.com/flashplayeer9](http://wiki.ubuntu.com/flashplayeer9)

---

### Post by azmo35 on 2009-03-25
:)Finally i solve my problem with adobe flash.
The solution, on synaptic search for "flash"
adobe flash 10.0.22.87-2
adobe flashplugin-nonfree
if the to are installed remove them "mark for complete removal" and "apply". Open terminal "applications/accessories/terminal" and type locate libflashplayer.so if still installed on a directory like this [/usr/lib/firefox/plugins] go ahead and type gksu nautilus and navigate to that directory and delete libflashplayer.so, this is only if terminal gives you a location,other wise close terminal. Go to system/administration/synaptic search flash "mark for installation" adobe flash 10.0.22.87-2,close synaptic.Open firefox type about:plugins now you have shockwave flash 10.0 r22 file name:/usr/lib/adobe-flashplugin/libflashplayer.so.
Last note: this as made with firefox closed and in the past i have manualy installed from adobe web site, thanks to this thread on launchpad [here]("https://answers.launchpad.net/ubuntu/+source/firefox-3.0/+question/57493"),azmo.:lolflag:

---

