---
title: "Default Login Window Theme"
date: 2009-05-18
forum: Desktop Environments
---

### Post by izzygalvez on 2009-05-18
I am using **Clearlooks** as my theme in Ubuntu, and I would like to have my login screen use Clearlooks by default, as well. Customizing the Login screen via **System > Administration > Login Window** does not give an the option for a default window theme.

Is it possible to have the login screen use Clearlooks by default instead of Ubuntu Human theme? If so, how can I achieve this?

---

### Post by devosion on 2009-05-18
Clearlooks is a metacity gtk engine / theme and will not work with the login window. There are a variety of gdm themes out there to install and try. I'd recommend gnome-look.org to find what you might be looking for.

---

### Post by izzygalvez on 2009-05-18
Ok. I guess this is what I am trying to do... I noticed you can change the "theme" while you are at the login window. It's in the menu bar, next to **Actions**. So, I set it to Clearlooks. When I log out, it is still set as Clearlooks, but when I reboot, the "theme" is set back to Ubuntu Human.

Is there a way to keep it set as Clearlooks?

---

### Post by sherl0k on 2009-05-18
Make sure that in the "Theme" dropdown it's set to "Selected only" and then use the radio buttons to choose Clearlooks.

---

### Post by izzygalvez on 2009-05-20
Nevermind, I figured it out myself... Since it was mentioned that the login window uses GDM, I looked around in my filesytem for GDM config files. I found **gdm.config** and **gdm.conf-custom** in **/etc/gdm/**

I read both files carefully, and to achieve what I wanted, I added **GtkTheme=Clearlooks** under **[gui]** into the **gdm.conf-custom** file... I rebooted, and it worked! I knew it couldn't be too complicated. I'm surprised **Login Window Preferences** doesn't give you this simple option.

- Izzy

---

