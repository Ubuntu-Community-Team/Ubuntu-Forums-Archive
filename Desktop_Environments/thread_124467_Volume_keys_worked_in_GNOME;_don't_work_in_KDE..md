---
title: "Volume keys worked in GNOME; don't work in KDE."
date: 2006-02-01
forum: Desktop Environments
---

### Post by grendel_khan on 2006-02-01
I have a compaq nx9500 laptop, running Breezy. It has special volume buttons--volume up, volume down and mute--above the keyboard.

Now, I had previously used GNOME, and when I used these buttons, a small window, like a mini-mixer, would pop up and display the volume being adjusted. However, when I moved to KDE, the buttons do nothing. I've been advised to look into using lineakd, but I'm fuzzy on why it worked out-of-the-box with GNOME, and I need to putz around with keycodes to make it work under KDE.

Using xev, the keycodes are revealed to be 174 (Volume Down), 176 (Volume Up) and 160 (Toggle Mute). These seem to be pretty standard.

Am I missing something? Did I configure something wrong?

---

### Post by Gerardo Santo on 2006-02-01
I've got an IBM Thinkpad and everything works fine. However you should make sure to have the kmilo (or better the kdeutils) Package installed...

---

### Post by grendel_khan on 2006-02-01
I already had kmilo installed; installing kdeutils installed ten new packages, none of which leaps out at me as being related to the topic at hand. kded is running. (I found some information [on this page](http://www.kde.me.uk/index.php?page=kmilo); apparently kmilo is a plugin to kded.) I can't see a way to configure kmilo or insure that it's working in some fashion. These keys are generic; the generic kmilo configuration should be picking them up.

Thanks for your help so far; any ideas where to go from here?

---

### Post by aysiu on 2006-02-01
I know this doesn't help you, but I have the same experience--all my multimedia keys work in Gnome but not in KDE. I tried picking a different keyboard layout, but my keyboard wasn't listed in the KDE Control Center.

---

### Post by grendel_khan on 2006-02-03
[QUOTE=aysiu]I know this doesn't help you, but I have the same experience--all my multimedia keys work in Gnome but not in KDE. I tried picking a different keyboard layout, but my keyboard wasn't listed in the KDE Control Center.[/QUOTE]

I don't think that would fix it; did GNOME have a non-104 keyboard layout selected? What **is** the GNOME equivalent of kmilo? How the heck do I even configure kmilo?

---

### Post by tmahmood on 2006-02-03
mine didn't work either... and it works perfectly on GNOME.... I have 18 extra keys and only the sleep button don't works. even calculator pops up when I press the calculator button :D

---

### Post by jetpeach on 2006-03-02
goddamn, i searched all over looking for ANY information on configuring Kmilo.  wtf, there's virtually NOTHING.  arg...

man, this is a pain.  i have a logitech elite and configuring these keys is turning into a royal pain in the ***.

---

### Post by grendel_khan on 2006-03-02
[QUOTE=jetpeach]man, this is a pain.  i have a logitech elite and configuring these keys is turning into a royal pain in the ***.[/QUOTE]

Does it work in GNOME?

---

### Post by jetpeach on 2006-03-02
I'm not sure if they worked in Gnome either, I hadn't tried it.- my keyboard is the Logitech Elite so it isn't listed (though I read it's similar to the Logitech Internet Navigator), but in any case, I did discover some useful stuff that got it working mostly in KDE and Gnome.

First, for the Logitech Elite I needed to follow the steps in [this thread]("http://www.linuxquestions.org/questions/showthread.php?t=125333"), up until he says you're 'ready to start assigning keys in KDE.'  If your keyboard is listed in the KDE control panel keyboard layouts though, then just choose it there.  Also, if you're like me and running KDE 3.51 and NO keyboard layouts were showing up whatsoever, you need to run "sudo ln -s /etc/X11/xkb /usr/share/X11" there is some bug that when it upgraded all my keyboard layouts weren't listed.

Then, I installed keytouch from the Sourceforge site using the [DEB file for Ubuntu]("http://keytouch.sourceforge.net/dl-keytouch.html") they have using "sudo dpkg -i package_file_name_here.deb".

Run keytouch from Menu->system and choose your keyboard model (though the Elite doesn't show up for me in this menu, not sure why not, I used Logitech internet navigator it seems to work for the Elite) and then just set your keys.  The volume up/down didn't work until I installed aumix from Synaptic, but now it does (though without an on-screen-display, anyone know how to get this?).

Anyway, maybe this helps someone out.  I hope development of Kmilo gets rolling and some better system for this gets into 6.04 or at least 6.10...

---

### Post by Orval on 2006-03-06
I cannot install keytouch. KPackage and dpkg say that the file is not a valid deb-file. I tried both versions from sourceforge.

---

### Post by antibios on 2006-11-24
Yeah, I can verify this on my Dell Latitude D620.  
XF86AudioMute, XF86AudioLowerVolume and XF86AudioRaiseVolume all work perfectly in Gnome, but in KDE they don't work at all.

I have kmilo installed.

In Kmix, if I set up global shortcuts, I can press the mute button and the shortcut will be linked to XF86AudioMute, so the key is being received correctly, however there after the keys have no effect.

I tried removing Kmilo and it had no effect.

Oh and xev shows that the keys are working properly.

---

