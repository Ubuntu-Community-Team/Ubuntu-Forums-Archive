---
title: "How to make small adjustments to Xfce themes"
date: 2009-02-03
forum: General Help
---

### Post by Dave M G on 2009-02-03
Xubuntu users,

I am using the Xfce interface with Xubuntu 8.10 on my laptop.

Currently the theme I have is Xfce-b5. I like it for the most part, but there are just one or two minor issues I have with it.

I'd like to be able to do just a couple of tweaks, such as change the font colour on the title bars, and change the colours of the side scroll bars.

So far as I can tell, though, nowhere in Xubuntu/Xfce is there any option to customize a theme.

Is it possible to make such adjustments? Can I do it within an GUI and not edit text files?

Thank you for any advice.

Dave M G

---

### Post by Harii on 2009-02-07
try GNOME Color Chooser.

for minor adjustments and tweaks.

---

### Post by Locutus_of_Borg on 2009-02-07
sudo nano /usr/share/themes/[name of theme]/gtk-2.0/gtkrc

edit as you like.  

Changes will not take effect until you either log out, or temporarily switch to a different theme, then back

---

