---
title: "Remove User Log-in Wall."
date: 2015-03-02
forum: Desktop Environments
---

### Post by Lucas Azazer on 2015-03-02
Hello! I could use my help with the Xubuntu log-in screen. My problem is that I ***DONT ***want my wallpaper to be displayed when you click on my account name. I'm posting this because looking around other threads I could only find people with the opposite problem, they couldn't get the log-in wallpaper to match the one on their account- which is what I want, for it not to match. I tried something called, if I remember right, LightDM Greeter or something to that effect to try and remove my wall from the log-in screen, but that doesn't seem to be working on my user account and is only affecting the guest session account. Any ideas?

---

### Post by deadflowr on 2015-03-02
First, I would try setting the permissions for the picture you use on your desktop to 750, or something like that.
(Could also be 770, or 700, as long as the 3rd digit (others) is 0.)
0(zero)=none, from a gui point of view; aka if you try changing permissions using (thundar/whatever xubuntu's file manager is?)

---

### Post by raptir on 2015-03-03
In 15.04 they have added a GUI to configure the GTK greeter, but it essentially just edits the configuration files in /etc/lightdm.

Add some lines in lightdm-gtk-greeter.conf that read...

```

user-background=false
background=**what you want as your background**

```

background can accept an image file for a wallpaper or a hex color value. If you set user-background to false and leave background empty you'll get a black background.

---

### Post by Lucas Azazer on 2015-03-13
> **deadflowr said:**
> First, I would try setting the permissions for the picture you use on your desktop to 750, or something like that.
(Could also be 770, or 700, as long as the 3rd digit (others) is 0.)
0(zero)=none, from a gui point of view; aka if you try changing permissions using (thundar/whatever xubuntu's file manager is?)

> **raptir said:**
> In 15.04 they have added a GUI to configure the GTK greeter, but it essentially just edits the configuration files in /etc/lightdm.

Add some lines in lightdm-gtk-greeter.conf that read...

```

user-background=false
background=**what you want as your background**

```

background can accept an image file for a wallpaper or a hex color value. If you set user-background to false and leave background empty you'll get a black background.

Thanks for the advice Raptir. I manually changed the setting on the config file though it doesn't seem to be working, changed user background to false and put a different directory to wallpaper and even set it to false for a black background- but my wall is still there when I click on my account. Funny enough the guest account doesn't seem to have the same problem and did change.
Thanks to you too Deadflower, though, I don't really understand what you mean with their permissions, don't see any options to change permissions with some numerical setting, thunar is the desktop's file manger by the way.

I don't know it this means anything, but my computer was running Unity originally before installing the Xfce desktop, and the Gnome3 desktop before that. No idea if that might have affected something though.

---

