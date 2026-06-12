---
title: "is there a way to change ubuntu 11.10 to look like maverick?"
date: 2012-01-25
forum: Desktop Environments
---

### Post by Rnegade21 on 2012-01-25
I'm really not happy with the new ubuntu look. i'm wondering if anyone can give me instructions to make ubuntu 11.10 look exactly like ubuntu maverick, without changine distros. just some way to get rid of the side toolbar, and get the maverick theme

---

### Post by carl4926 on 2012-01-25
Install Gnome3 shell and use the advanced tweak tool to set the Desktop to use icons

or use the Gnome 3 with Cinnamon.

---

### Post by Rnegade21 on 2012-01-31
> **Rnegade21 said:**
> I'm really not happy with the new ubuntu look. i'm wondering if anyone can give me instructions to make ubuntu 11.10 look exactly like ubuntu maverick, without changine distros. just some way to get rid of the side toolbar, and get the maverick theme


I figured it out. thanks for the reply

im sure someones probably posted this before me, but if anyone want to know how to make ubuntu 11.10 really look like it used too here's a tutorial,  [http://www.omgubuntu.co.uk/2011/12/how-to-make-ubuntu-11-10-look-and-feel-like-gnome-2/](http://www.omgubuntu.co.uk/2011/12/how-to-make-ubuntu-11-10-look-and-feel-like-gnome-2/)

the one thing you dont want to do on this tutorial is this part:

**Compiz**

The GNOME Classic Session doesn’t play too nice with Compiz in Ubuntu 11.10. But we can fix that.

[LIST]
[*]Open a Terminal
[*]Enter: *gksu gedit /usr/share/gnome-session/sessions/gnome-classic.session*
[*]Change the line:
[/LIST]
*RequiredProviders=windowmanager;notifications;*

[LIST]
[*]to:
[/LIST]
*RequiredProviders=windowmanager;*
With this fixed you can login to your GNOME 2.x style session using ‘GNOME Classic’ instead of the ‘GNOME Classic (No effects)’.




this will cause problems and it seems to be unecessary

---

