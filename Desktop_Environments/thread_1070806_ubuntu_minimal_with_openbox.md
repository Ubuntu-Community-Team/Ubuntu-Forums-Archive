---
title: "ubuntu minimal with openbox"
date: 2009-02-15
forum: Desktop Environments
---

### Post by LunaticHiatus on 2009-02-15
installed ubuntu minimal install. after installing only the base system. I aptituded xorg, openbox, obconf, openbox-themes slim, firefox, xfe, synaptic, xfce4-terminal and pypanel.

The trouble I have been having so far is I need to know how to edit my openbox menu and how to autostart pypanel. It also doesn't save my session so when I try to shutdown openbox, it takes me back to command line and when I restart anything I saved in say firefox is gone.

---

### Post by Stan_1936 on 2009-02-17
This **might** help:

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

---

### Post by mikewu on 2009-02-17
There should be a ~/.config/openbox folder. Inside create a file called autostart.sh

Just put any programs you want to autostart and make sure you **end all commands with a &**

If pypanel doesn't start correctly next time, put a sleep infront. That fixed it for me.
(sleep 2 && pypanel) &

As for menus, I just used mmaker to automatically generate menus.

The link that was posted above does have a few other methods of configuring menus and openbox in general. urukrama's website is extremely helpful in configuring anything openbox related.

Hope this helps!

---

### Post by der_joachim on 2009-02-17
Try obmenu. It is a menu editor for openbox. It should be in the repos.

---

### Post by m_duck on 2009-02-17
The standard menu, autostart and config are at```
/etc/xdg/openbox/
```To copy all of these to your home directory run:```
mkdir -p ~/.config/openbox
cp /etc/xdg/openbox/* ~/.config/openbox/
```There is a good example of an autostart file on the [openbox website]("http://icculus.org/openbox/index.php/Help:Autostart"), though I tend to end up deleting most of it.

To edit your menu, edit the ~/.config/openbox/menu.xml file and then reconfigure openbox (in the menu). The file is fairly self explanitory after a bit of looking at it.

Having never used SLiM, I can't answer the session question directly, but when using ~/.xinitrc and startx to login, it must be "openbox-session" that is run, rather than just "openbox".

I think there is a mention of using SLiM to login on the [arch wiki]("http://wiki.archlinux.org/index.php/Openbox"). I would also recommend having a look through urukrama's openbox guide (as mentioned by Stan_1936).

---

