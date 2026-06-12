---
title: "Slow startup for Fluxbox"
date: 2005-04-13
forum: Desktop Environments
---

### Post by 014&lt; on 2005-04-13
Hi

I've recently installed the server version of hoary. After I had done that I installed the X window system and Fluxbox. The problem with Fluxbox is that the startup is so slow. It takes a really long time before it's ready. I've never experienced this problem before on either slackware or debian.

I search the Fluxbox forum at sourceforge for answers and then I found this post:

[http://sourceforge.net/forum/message.php?msg_id=2971985](http://sourceforge.net/forum/message.php?msg_id=2971985)

The replay said that it could be a network problem and there was a link for how to solve it:

[http://forums.gentoo.org/viewtopic.php?t=276942&highlight=hostname+domainname+howto](http://forums.gentoo.org/viewtopic.php?t=276942&highlight=hostname+domainname+howto)

That howto is for gentoo. And my problem is when I get to step 5. Then I don't know what to do anymore. I can't find the program domainname. Is there any other solution to this problem?

---

### Post by Stormy Eyes on 2005-04-13
[QUOTE=014<]That howto is for gentoo. And my problem is when I get to step 5. Then I don't know what to do anymore. I can't find the program domainname. Is there any other solution to this problem?[/QUOTE]

I think you're stuck because Ubuntu doesn't use the same init scripts Gentoo does. It doesn't *have* "/etc/init.d/domainname". If you're in GNOME, try using the Network Settings app in the System menu. I'll give more detailed instructions when I get home and am sitting in front of my Ubuntu box.

Of course, if you want a *box WM, you could try Blackbox; version 0.70 just came out and it's quite pretty.

---

### Post by Psquared on 2005-04-13
Can Blackbox be setup to run Gnome apps? How difficult is it?

---

### Post by Stormy Eyes on 2005-04-13
[QUOTE=Psquared]Can Blackbox be setup to run Gnome apps? How difficult is it?[/QUOTE]

Not difficult at all. Make sure /etc/profile includes the following line.

**export OOO_FORCE_DESKTOP="gnome"**

Then run **sudo apt-get install gtk-chtheme** so you can change GTK themes. You'll notice that Nautilus has ugly icons if you run it outside of GNOME. You'll have to add the following line to **~/.gtkrc-2.0** after setting your theme with gtk-chtheme.

**gtk-icon-theme-name = "<themename>"**

You'll also have to reset the "gtk-icon-theme-name" every time you change your theme, unfortunately, as gtk-chtheme creates a new gtkrc-2.0 with every theme change.

---

### Post by 014&lt; on 2005-04-13
In debian you can set programs to start at boot time by writing:

update-rc.d "programname".

That's the thing I try to do with domainname. But since I can't find the program it's no good.

Here is the man page for domainname:

[http://www.die.net/doc/linux/man/man1/domainname.1.html](http://www.die.net/doc/linux/man/man1/domainname.1.html)

Why can't I find this program on ubuntu. What program can I use instead?

---

