---
title: "gnome inhibit applet icon"
date: 2009-12-02
forum: Desktop Environments
---

### Post by Jimbo5584 on 2009-12-02
I am trying to customize my icon theme.  Currently I have almost all the icons for the apps that I regularly use customized.  However I have not been able to find an icon for the inhibit applet in the gnome panel.  

It seems that the icon that is shown in the "Add To Panel" menu is not the same as the actual panel icon.  The add to panel icon looks like a circuit board with Z's while the applet icon looks like a drive with Z's and when clicked is a circle slash with Z's.

I did manage to locate the circuit board icon in /usr/share/icons/hicolor/scalable/gnome-inhibit-applet.svg, but have been unsuccessful locating the others.  

Is it even possible to change the panel icons for this applet?  I sure hope it is otherwise my icon theme is going to look really strange with one icon out of place.

---

### Post by benju on 2011-03-25
I realize your post is from 2009, so I don't know If you're still interested, however the Inhibit applet uses the 'gnome-session-hibernate' icon to display the 'Automatic sleep enabled' mode and that's why It's so hard to find ( very little relation, go figure? ) it's located in

/usr/share/icons/Humanity/apps/22/gnome-session-hibernate.svg ( the 22px one )

hope it helps ( It was giving me a massive headache too ;) )

---

### Post by eitsuop on 2011-04-03
For those who are finding this page through Google like I did: here is my solution.

In your icon set's actions folder, in whatever size of icon you're using (likely 22 or 24,) gpm-hibernate is the Sleep Enabled version, while gpm-inhibit is the Sleep Inhibited version.

---

