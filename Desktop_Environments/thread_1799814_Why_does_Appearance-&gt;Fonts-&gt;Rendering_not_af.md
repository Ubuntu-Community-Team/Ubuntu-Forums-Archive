---
title: "Why does Appearance-&gt;Fonts-&gt;Rendering not affect Firefox?"
date: 2011-07-08
forum: Desktop Environments
---

### Post by Luke M on 2011-07-08
Why does Appearance->Fonts->Rendering not affect Firefox? Is this a bug or intentional for some reason? Firefox itself has no way of changing these preferences, as far as I can tell. This is a default ubuntu 11.04 install.

---

### Post by nomko on 2011-07-08
There is the option of changing the font in FF. Take a look here: [http://support.mozilla.com/en-US/kb/Changing%20fonts%20and%20colors](http://support.mozilla.com/en-US/kb/Changing%20fonts%20and%20colors)

---

### Post by Luke M on 2011-07-08
No, there is no rendering option, only font selection.

---

### Post by lovinglinux on 2011-07-08
> **Luke M said:**
> No, there is no rendering option, only font selection.

See the fourth item at [http://www.webgapps.org/tutorials/firefox/troubleshooting/rendering-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/rendering-issues-and-solutions)

---

### Post by Luke M on 2011-07-08
> **lovinglinux said:**
> See the fourth item at [http://www.webgapps.org/tutorials/firefox/troubleshooting/rendering-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/rendering-issues-and-solutions)

What does this do?

---

### Post by Luke M on 2011-07-08
I found a solution here:

[http://linuxtweaking.blogspot.com/2011/01/ubuntu-10x-firefox-font-rendering-fix.html](http://linuxtweaking.blogspot.com/2011/01/ubuntu-10x-firefox-font-rendering-fix.html)

As a Ubuntu user you may notice Firefox does not obey the Gnome Appearance Setting with respect to the font rendering.

To make Firefox match your Gnome font rendering setting, simply erase the following file links in the /etc/fonts/conf.d folder

10-antialias.conf
10-hinting.conf
10-hinting-slight.conf

In a terminal type,
[INDENT]cd /etc/fonts/conf.d

sudo rm 10-*.conf[/INDENT]Restart Firefox for the changes to take effect.

**How to restore the symbolic links**
[INDENT]sudo ln -s /etc/fonts/conf.avail/10-antialias.conf /etc/fonts/conf.d/
sudo ln -s /etc/fonts/conf.avail/10-hinting.conf /etc/fonts/conf.d/
sudo ln -s /etc/fonts/conf.avail/10-hinting-slight.conf /etc/fonts/conf.d/

[/INDENT]

---

