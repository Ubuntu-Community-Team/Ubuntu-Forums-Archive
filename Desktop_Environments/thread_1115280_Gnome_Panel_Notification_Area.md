---
title: "Gnome Panel Notification Area"
date: 2009-04-03
forum: Desktop Environments
---

### Post by fusa on 2009-04-03
Is it possible to prevent an app to appear in the notification area applet in gnome panel?  Recently universal access preferences is appearing there, also VPN connection.  I have no use for either, so would like to remove them if possible.

---

### Post by kanikilu on 2009-04-03
I've seen this brought up a few times, and from what I can tell, no, there doesn't really seem to be a way to control what does and does not show up in the notification area.

Hopefully someone can prove me wrong, because I would love to hide at least one icon in there ;)

---

### Post by Giblet5 on 2009-04-03
Without coding a custom notification area applet that accepts a black-list type config file, I think the only way to not display apps in the NA is to remove the NA from the panel.....or remove NA display code from the app that you want hidden (if it doesn't already have that option).

eg, For VPN, just use the CLI openvpn command instead of one of the GUI frontends...

---

### Post by fusa on 2009-04-03
Ok, I was looking for a separate configuration for the notification applet, but guess there isn't one.  I did find: [http://ubuntuforums.org/showthread.php?t=993825](http://ubuntuforums.org/showthread.php?t=993825) to get rid of the access icon, and disabled network manager applet from sessions to get rid of that.

---

