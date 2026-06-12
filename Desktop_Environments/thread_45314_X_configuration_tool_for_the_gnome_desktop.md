---
title: "X configuration tool for the gnome desktop"
date: 2005-06-29
forum: Desktop Environments
---

### Post by crashedworld on 2005-06-29
Hi!

I'm new to Ubuntu (but not new to Linux, used Gentoo for over two years) and this is the way I like Linux to see... Gnome ist really cool! (And Ubuntu too as it uses Gnome as the primary desktop).
But that's not what I wanted to say.

All the time I've used Linux I created my XF86Config or now xorg.conf by hand.
As Ubuntu is the easy way of living  :) it's time to search for a tool that integrates into gnome an assists me creating my xorg.conf

Does anyone have an idea which tool could do this?

thx

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=crashedworld]Hi!

I'm new to Ubuntu (but not new to Linux, used Gentoo for over two years) and this is the way I like Linux to see... Gnome ist really cool! (And Ubuntu too as it uses Gnome as the primary desktop).
But that's not what I wanted to say.

All the time I've used Linux I created my XF86Config or now xorg.conf by hand.
As Ubuntu is the easy way of living  :) it's time to search for a tool that integrates into gnome an assists me creating my xorg.conf

Does anyone have an idea which tool could do this?

thx[/QUOTE]

Hello. I moved your thread to the correct place. There is no Gnome tool, but ther is a command line tool that comes from Debian. The command you want is this one:

> sudo dpkg-reconfigure xserver-xorg

---

