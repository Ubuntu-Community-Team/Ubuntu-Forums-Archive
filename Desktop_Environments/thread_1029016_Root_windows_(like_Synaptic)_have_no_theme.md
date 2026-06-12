---
title: "Root windows (like Synaptic) have no theme"
date: 2009-01-03
forum: Desktop Environments
---

### Post by thaidog on 2009-01-03
Any time I bring up a Window that requires a password (like Synaptic) the Window pops up without the theme my desktop is currently using.

Is there any way to change this?

---

### Post by Tim Sharitt on 2009-01-03
The reason these windows don't share your theme is because they are run as the root user and use the default theme. You can enable the root account and chage its theme to match yours. However, instructions for enabling the root account are frowned on here so you'll have to figure that out yourself :).

---

### Post by ushimitsudoki on 2009-01-03
If you do decide to do this, let me suggest that you don't just use your own theme for root. (So don't just symlink the files, in other words)

Change it with something like a red border or some touch like that, so you can easily tell by looking at it that you are working as root. You can still have a look that matches your desktop with a bit of added safety.

---

### Post by argie on 2009-01-03
If you install themes through the System » Appearance dialog box, they get installed only for your user. If you want the themes to be available for all users, they need to be installed to /usr/share/themes/. If you want programs run as the root user to be themed, you have to allow the root user to see these themes. One way is to copy the theme to /usr/share/themes/. The other way is to copy the theme to /root/.themes/

---

### Post by mcduck on 2009-01-03
One nice trick is to just symlink your personal theme & icon directories into root's theme directories:

sudo ln -s /home/*username*/.themes /root/.themes
sudo ln -s /home/*username*/.icons /root/.icons

This way root will always have the same theme you are using.

Personally, I always set the Nautilus background to red for root user. Just to make sure that I'll never confuse the root Nautilus with one running as my own user. For other programs I don't see much need for having a different look, as I really  can't imagine any situation where I would use root privileges with an app that I also run as normal user.

---

### Post by ushimitsudoki on 2009-01-03
> **mcduck said:**
> 
Personally, I always set the Nautilus background to red for root user. Just to make sure that I'll never confuse the root Nautilus with one running as my own user. For other programs I don't see much need for having a different look, as I really  can't imagine any situation where I would use root privileges with an app that I also run as normal user.

On occasion I have needed to edit a text file as root.

---

### Post by thaidog on 2009-01-03
> **ushimitsudoki said:**
> If you do decide to do this, let me suggest that you don't just use your own theme for root. (So don't just symlink the files, in other words)

Change it with something like a red border or some touch like that, so you can easily tell by looking at it that you are working as root. You can still have a look that matches your desktop with a bit of added safety.

I agree this is a good practise.

---

### Post by mcduck on 2009-01-03
> **ushimitsudoki said:**
> On occasion I have needed to edit a text file as root.

Good point. :D I didn't even think of that since I mostly use nano for editing configuration files. But Gedit allows you to set different fonts & colors for root, I guess that would help distinguishing it when running as root while still keeping the same theme for all running applications.

But sure, if you don't change your themes too often, it would be possible to maintain uniform look on your desktop when using different theme for root.  I suppose using a variation of the same theme normal user has but with highlight color changed to red would look quite nice.. I just change my desktop theme too often to bother with always changing the root's theme as well.

---

### Post by ushimitsudoki on 2009-01-03
Heh. 

Anyway, it's one of the things I really like about XFCE. You get a small red banner in mousepad and thunar saying "warning, you are using the root account" automatically.

One of many nice touches in XFCE.

---

