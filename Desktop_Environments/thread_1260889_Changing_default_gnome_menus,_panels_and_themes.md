---
title: "Changing default gnome menus, panels and themes"
date: 2009-09-08
forum: Desktop Environments
---

### Post by ryan88 on 2009-09-08
Hi,

I am looking to change the default settings for the following:

[LIST=1]
[*]Gnome menu items
[*]Gnome panel icons
[*]GDM theme
[*]GTK theme
[*]Icon set
[/LIST]
I know that the gnome menu items can be configured from /etc/xdg/menus, but I am at a loss as to where to configuration files are for the other things.

I would be very grateful for any help anyone can give.

Thanks,

Ryan

---

### Post by mcduck on 2009-09-08
1. Right-click the menu applet and select "Edit Menus"

2. Icons in panels come from the same theme as the rest of your application icons. 

3. System/Administration/Login Window

4. System/Preferences/Appearance

5. same as above.

---

### Post by ryan88 on 2009-09-08
Thanks for your reply, but that is how to change your personal settings. I am after a way to change the default settings so that the changes i make will be the same for each new user, sorry that I didn't make that clear.

Thanks,

Ryan

---

### Post by wojox on 2009-09-08
You're not gonna let your users customize their desktop? What kind of sysadmin are you? :lolflag:

---

### Post by mcduck on 2009-09-08
> **ryan88 said:**
> Thanks for your reply, but that is how to change your personal settings. I am after a way to change the default settings so that the changes i make will be the same for each new user, sorry that I didn't make that clear.

Thanks,

Ryan

Setting the GDM screen will affect all users, that setting isn't personal since GDM is loaded before users log in.

For the rest, the settings are stored in gconf, and as far as I know running gconf-editor as root allows you to set the keys to mandatory (meaning that they affect all users and those user's aren't able to change the value themselves).

Gnome also has two tools specifically made for configuring user's desktops and locking down the setup, Pessulus and Sabayon. You might want to check them out.

But unless you really want to take the ability of customizing the desktop away from the users, and instead just wish to configure the default setup for new users, all you need to do is move the relevant configuration files to /etc/skel. I usually create a new user, configure the desktop to how I like it, and then copy all dotfiles from that user's home into /etc/skel (and then remove that user again).

---

### Post by ryan88 on 2009-09-08
Thanks for your reply mcduck. Yeah i want users to be able to change their settings, I just want to change the default for each new user, so I'll try your approach of creating a new user and copying the files over to /etc/skel, thanks for the tip!

Thanks,

Ryan

---

