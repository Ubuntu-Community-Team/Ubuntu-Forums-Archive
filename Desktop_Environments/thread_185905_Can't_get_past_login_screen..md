---
title: "Can't get past login screen."
date: 2006-06-01
forum: Desktop Environments
---

### Post by dipswitch on 2006-06-01
This has happend a couple of times before but I was able to login in the past using GNOME failsafe. But now I can't login at all except in terminal mode. When I try to login it makes it to the desktop then the mouse will freeze then I hear the drum beat at the screen goes blank and takes me right back to the login screen. Is there anything I can do to get past this?

btw I've booted to terminal and ran 

sudo apt-get update && sudo apt-get dist-upgrade

And it appears I'm up to date but I still can't get past the login screen. Any help with this one? I really don't want to have to install since I had things working so well.

---

### Post by dipswitch on 2006-06-01
Is there a way I could try re-installing gnome or switch to KDE? Maybe reinstalling gnome would resolve this issue?

---

### Post by jonibo on 2006-06-01
Which type of video card do you have?  ATI, NVidia, or something else...?

---

### Post by dipswitch on 2006-06-01
Its an onboard S3 Graphics ProSavageDDR.

---

### Post by jonibo on 2006-06-01
Try this:

1) Try to log in so that it fails once and jumps back to the login screen.
2)  Press ctrl+alt+F1 so it takes you to a terminal
3)  Run the following command:

tail /var/log/messages

4)  Check if there are any obvious errors there... attach the output to a post here if you can.

---

### Post by dipswitch on 2006-06-01
Well. I was finally able to login after serveral dozen attempts. I just kept trying over and over and over until finally it worked. I didn't see any obvious errors but here is what I get from messages.

Jun  1 13:35:58 THEEGGMAN gconfd (dipswitch-4695): starting (version 2.14.0), pid 4695 user 'dipswitch'
Jun  1 13:35:58 THEEGGMAN gconfd (dipswitch-4695): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun  1 13:35:58 THEEGGMAN gconfd (dipswitch-4695): Resolved address "xml:readwrite:/home/dipswitch/.gconf" to a writable configuration source at position 1
Jun  1 13:35:58 THEEGGMAN gconfd (dipswitch-4695): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun  1 13:35:58 THEEGGMAN gconfd (dipswitch-4695): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun  1 13:35:58 THEEGGMAN gconfd (dipswitch-4695): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun  1 13:36:04 THEEGGMAN gconfd (dipswitch-4695): Resolved address "xml:readwrite:/home/dipswitch/.gconf" to a writable configuration source at position 0

I'm logged in now but I'm afraid to logout because I know I won't be able to log back in easily.

---

### Post by dipswitch on 2006-06-01
Ok you all are gonna probably think I'm crazy but I think I've found a pattern. If I try to login without moving my mouse it will take me back to the login screen every time.

But if right after I login and my desktop first appears, if I move my mouse over the applications, places and system menus, it will continue to load the desktop. However if I don't do this at the appropriate time my mouse will freeze and dumps me back to the desktop. Does that sound crazy?

---

