---
title: "Menu items/launchers not showing up?"
date: 2005-02-18
forum: Desktop Environments
---

### Post by Pointwood on 2005-02-18
Hi, I've tried to add a few applications I've installed (through synaptic) to the Applications menu but they aren't available in the menu although they do exist as I can see them when I run applications:/// 

I could imagine it's just me being a newbie and stupid  ](*,) but I hope someone is able to give me a solution :)

---

### Post by somuchfortheafter on 2005-02-18
the only solution i have found is to add them in manually, find the menu pick any item right click and it should show add new launcher or somthing like that and just fill in the details.

---

### Post by Pointwood on 2005-02-18
Maybe I didn't explain myself properly, but that is actually exactly what I've done: Right click on a menu -> Entire menu -> Add new item to this menu -> fill in the details.

Nothing in the menu when I click on the Applications menu, however, it is there if I run applications:/// and I don't quite understand that, but I'm pretty new to Gnome and Linux in general.

---

### Post by reticular on 2005-02-19
[QUOTE=Pointwood]Maybe I didn't explain myself properly, but that is actually exactly what I've done: Right click on a menu -> Entire menu -> Add new item to this menu -> fill in the details.

Nothing in the menu when I click on the Applications menu, however, it is there if I run applications:/// and I don't quite understand that, but I'm pretty new to Gnome and Linux in general.[/QUOTE]

 Have you restarted GNOME since adding the items? I've noticed I generally need a restart to see the changes. You don't have to restart the whole system, just CTL+ALT+BACKSPACE to restart gnome and the X-Server.

---

### Post by Pointwood on 2005-02-20
Yes, the machine have been rebooted since, but no change :(

---

### Post by WW on 2005-02-20
Are you running warty or hoary? hoary has a known problem with menus:
[http://ubuntuforums.org/showthread.php?t=15720](http://ubuntuforums.org/showthread.php?t=15720)

---

### Post by Pointwood on 2005-02-20
Hmm...that might be it, I use warty & warty-backports. But I've temporarily had the hoary rep. added to install mplayer I believe.

Don't know if it is the right way to do it, but I've got it working (ie. added some entries to the menu) by creating .desktop entries in /usr/share/applications.

---

### Post by kassetra on 2005-02-20
Pointwood: that's how I create all of my extra menus -- only I usually type applications:/// in the nautilus window -- but it takes you to the same place.  :)

---

### Post by Pointwood on 2005-02-20
If you read the thread from the start, you'll see that that is exactly what doesn't work here ;)

---

### Post by kassetra on 2005-02-20
Some things you might not know then:
   
 applications:/// only works if you have changed the permissions in /usr/share/applications because ubuntu doesn't come standard with a user-editable "favorites" menu.
   
 You can add your own favorites menu once through /usr/share/applications and then you'll be able to add all of your favorite applications without changing the permissions.
   
   You can also create subdirectories through the use of folders & .directory files.  Such as I have in this [screenshot]("http://www.linuxpeach.com/ubuntu/screenie.jpg").

---

### Post by Pointwood on 2005-02-20
Ahh....good info, thanks.

I'm quite new to Ubuntu, Gnome and Linux in general. I've made several "test runs" but I've ended back in Windows again :( 

This time it is different though, Ubuntu is my primary OS now :)

---

