---
title: "Fluxbox event sounds...NO THANK YOU"
date: 2009-04-24
forum: General Help
---

### Post by pw_f100_220 on 2009-04-24
Just installed jaunty...works awesome...fluxbox looks a lot better than it did with intrepid.  I think the only programs that make noise are gnome programs; nautilus and gedit so far...but i use those a lot...

back, forward, new, close, etc.

help me get rid of mouse click sounds please and thank you!

---

### Post by gettinoriginal on 2009-04-24
System > Preferences > Sounds tab > tick or untic as you want.  Also you can highlight alert, left click and hold, you will be given a drop down to change sound (default, disable, or custom).  If some are greyed out, it is because of your choices in the tick boxes at the top.
[ATTACH]110808[/ATTACH]

---

### Post by pw_f100_220 on 2009-04-24
thanks, but that's gnome.  it's already disabled for when i use it.

---

### Post by codeseer on 2009-04-24
> **pw_f100_220 said:**
> thanks, but that's gnome.  it's already disabled for when i use it.

You'll be wanting to remove the 'ubuntu-sounds' package.

---

### Post by pw_f100_220 on 2009-04-24
*really?*  hmmm.  you seem to be everywhere codeseer

---

### Post by codeseer on 2009-04-24
I like to help when I can.

---

### Post by Idlidibo on 2009-05-16
Pardon the thread necromancy, but I felt compelled to reopen this conversation. See, when I upgraded to Jaunty, I wasn't entirely happy with some things, but I liked others, so I configured Gnome the way I wanted it to be, and now I'm generally happy.

And then I logged into Fluxbox, and I was also greeted with these pops, beeps, and boops everytime I clicked in certain programs, and I was really excited when I found this topic. So I did sudo apt-get remove ubuntu-sounds, and now all the event sounds on my computer are gone (log-in screen, gnome startup, and every other place where I had configured my sounds to be.)

tl;dr: Is there a way to get rid of event sounds in Fluxbox without getting rid of them in Gnome?

---

### Post by Albertint on 2009-06-19
Not that this answers your question, but I say it's better just to live w/o gnome sounds. I myself cannot stand these annoying sounds and would wish developers never to use them in the first place. That's just me, anyway.

---

### Post by ABCC on 2010-01-12
This had me pulling my hair out too after a few unrelated issues lead me to disable gnome-settings-daemon from running. Issues solved but it didn't take long for me to realise Openbox had acquired the wonderful system sounds feature and sounded an awful lot like windows...:(

Anyway, after a fair bit of swearing I decided to rename a file:

mv /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules  /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules.disabled

and restarted my X server. According to apt libcanberra-gtk-module "translates Gtk+ widgets signals to event sounds". Not loading it does the trick if you don't care for system sounds at all, theres probably a neater solution by undoing the work of the Xsession script so sound can be disabled on a per user basis. 

To reenable simply rename the file back to the old name. For more info on how check the manpages for Xsession and run-parts.

---

### Post by hoover67 on 2010-11-10
More necromancy here ;-) 

I'm running a gnome-less fluxbox env at the moment, trying to get rid of those annoying mouse freezes / double led blinking of death crashes in Ubuntu 10.04 and beyond, and in order to disable the annoying alert sounds I simply did, as root, 

mv /usr/share/sounds/ubuntu/stereo /usr/share/sounds/ubuntu/stereo_disabled

I could not find an ubuntu-sounds package on my system (currently maverick, 10.10). 

HTH Hoover

---

