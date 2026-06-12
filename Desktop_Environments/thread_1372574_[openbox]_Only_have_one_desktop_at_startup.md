---
title: "[openbox] Only have one desktop at startup"
date: 2010-01-04
forum: Desktop Environments
---

### Post by chickengirl on 2010-01-04
I'm running an eeepc which originally had Easy Peasy installed. I didn't like EP's custom interface so I installed xubuntu on top of it. Then later I installed openbox which I am using now. My problem is I always have only one desktop when I log in and have to manually create the other three. I have obconf set for 4 at start up but something is overriding it. I assume it's some leftover setting from Easy Peasy's setup but I can't find it.

Any help or suggestions would be muchly appreciated.

---

### Post by spiderbatdad on 2010-01-04
Not very familiar with open box, but I believe Xubuntu uses gdm to some extent, particularly for login. You might look at gconf-editor apps>>metacity>>general>>num_workspaces. You can set the default value by double clicking the existing value.

---

### Post by chickengirl on 2010-01-04
> **spiderbatdad said:**
> Not very familiar with open box, but I believe Xubuntu uses gdm to some extent, particularly for login. You might look at gconf-editor apps>>metacity>>general>>num_workspaces. You can set the default value by double clicking the existing value.

I looked up that value, it was set for 2. Changed it to 4, no effect. Still have one desktop when I load up openbox.

---

### Post by MooPi on 2010-01-04
Wow that's a perplexing problem. Have you switched back to XFCE side and see if it's something on that side thats hanging it. I personally would drop Xubutu and start with the minimal install CD. I have a feeling you can handle this as I've read some of your previous posts. Openbox is so slick and unhindered by system settings. I'm alway tinkering with other DE and seem to wander back to Openbox.  Look up your openbox rc.xml file in ~/.config/openbox. It should list the number of desktops you've set up. I'm going out on a limb here and say they should match. Your not using some wild and funky gtk theme are you ? Here is a great guide to Openbox: [http://urukrama.wordpress.com/openbox-guide/#Autostart](http://urukrama.wordpress.com/openbox-guide/#Autostart)

---

### Post by chickengirl on 2010-01-04
> **MooPi said:**
> Wow that's a perplexing problem. Have you switched back to XFCE side and see if it's something on that side thats hanging it. I personally would drop Xubutu and start with the minimal install CD. I have a feeling you can handle this as I've read some of your previous posts. Openbox is so slick and unhindered by system settings. I'm alway tinkering with other DE and seem to wander back to Openbox.  Look up your openbox rc.xml file in ~/.config/openbox. It should list the number of desktops you've set up. I'm going out on a limb here and say they should match. Your not using some wild and funky gtk theme are you ? Here is a great guide to Openbox: [http://urukrama.wordpress.com/openbox-guide/#Autostart](http://urukrama.wordpress.com/openbox-guide/#Autostart)

rc.xml is set for 4 desktops. I switch around my gtk themes from time to time and it doesn't affect it.

As I recall, I actually had the same problem in xubuntu except that in xfce I couldn't even add more desktops. I'm going to go load up xfce and see what I can find there.

---

### Post by MooPi on 2010-01-04
Is a clean install a possibility for you. Other alternatives could be a one DE setup, or maybe Eeebuntu. Easypeasy looks to moblin for my taste. Eeebuntu looks promising as it gives the user three separate choices for a desktop. I haven't used Openbox on a multiple session computer for some time so I'm not going to be of much use for your solution sadly.

---

### Post by chickengirl on 2010-01-04
Now here's something weird. I was able to get both gnome (unr) and xfce to startup with 4 desktops. Openbox still only starting with 1.

The plan is actually to wipe the computer and do a clean install of Crunchbang when they have their next release. I've got way too much cruft on this thing.

---

### Post by MooPi on 2010-01-04
Is there no way I can talk you into a minimal Ubuntu install and build up from there. Nothing against Crunchbang, but I find it extremely satisfying knowing how everything is setup. You'll run into crazy Britsh settings as well. My browser searches always came back with a Great Britain slant. Let me know if your willing as I'd  volunteer some time to help.
Good luck either way.

---

### Post by spiderbatdad on 2010-01-05
[http://www.mail-archive.com/arch-commits@archlinux.org/msg03878.html](http://www.mail-archive.com/arch-commits@archlinux.org/msg03878.html)
This seems apropos. Apparently a patch to fix openbox workspace number in gdm.

---

