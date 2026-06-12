---
title: "Desktop stopped working"
date: 2004-12-23
forum: Desktop Environments
---

### Post by Fator dee on 2004-12-23
The problem is that my desktop stopped working quite completely. The panels are not working, they don't give any pop-up-windows when right clicking on them and the  same for the background. Also the panels are completely empty, they don't show any of my icons or applets that there were before. So the desktop is totallu unusable at the moment and I don't have a clue what to do to repair it :sad:. 
Otherwise the system seems to be working fine.

---

### Post by Fator dee on 2004-12-23
Well, I tried to kill gnome-panel from terminal and it responded with "There's already a panel running blaahblaah" and from the spurr of the moment I killed trashapplet and then all my icons and other applets appeared to the panels  :?
Although the background is still unresponsive to my right-clicking and when I try to start the "Computer -> Desktop Preferences -> Desktop Background" the application just crashes. Nautilus also won't start.

---

### Post by Fator dee on 2004-12-23
Info on the Nautilus problem. After a while this message popped to my screen.

nautilus --sm-client-id 117f000001000110381814700000212740018 --screen 0
No response to the SaveYourself command.
The program may be slow, stopped or broken.
You may wait for it to respond or remove it.

Although I have no idea what that means, I hope someone could help.

---

### Post by varunus on 2004-12-23
Does this still happen if you log in as a different user?  (If you dont have one, you can make one from the console with "adduser")

I've had this problem with certain desktop themes, namely the "Plastig" one...what theme are you using?

---

### Post by Fator dee on 2004-12-23
[QUOTE=varunus]I've had this problem with certain desktop themes, namely the "Plastig" one...what theme are you using?[/QUOTE]

I'm using the "Mist" theme.
And what makes this thing even more disturbing, I rebooted my computer and all the problems disappeared.

Feel's like I'm using Winblows again  :-s

---

### Post by Rhodan on 2004-12-23
I have had similiar problems to you, and a reboot solved it ... Winblows indeed ...

---

### Post by varunus on 2004-12-24
Hm, I've had problems like this after doing a fairly large apt-get that upgraded several core libraries...the only way to make it really use the new libraries is to go to a low runlevel and then a high one, or to reboot.

Hehe, can't do much about that, no matter what OS you use...

---

### Post by dave_euser on 2004-12-29
[QUOTE=varunus]Hm, I've had problems like this after doing a fairly large apt-get that upgraded several core libraries...the only way to make it really use the new libraries is to go to a low runlevel and then a high one, or to reboot.

Hehe, can't do much about that, no matter what OS you use...[/QUOTE]
 I had the same issue with Hoary...ended up logging in an root, deleting the .Xauthority and .ICE* from my user's home directory, kill the same in /tmp, and then killing all the processes that I had running under my normal account - restarted gdm, logged back in, and everyhting was OK.

---

### Post by xleon on 2004-12-29
I have something similar. Gnome would not start, so had to reinstall GDM. Now can get to the Ubuntu desktop and the intro panel states it's started Nautilus correctly etc.

On the desktop is nothing, only the wallpaper. No applications bar, pulldown menus, clock or anything. I CAN however, right click and get the menu "Open Terminal / Create Folder / Create Launcher" etc.

Tried reinstalling Nautilus but this has not helped. Can anyone suggest anything pls?

Edit: I realise it's not Nautilus that provides the panes with the clock etc.  I can use Gnome and Nautilus with no problems, but with out a menu bar, I have to start everything from the terminal which is a hassle. Any hints would be welcome.

---

### Post by xleon on 2004-12-29
Fixed by having to install gnome-panel which somehow either got corrupted or removed.

---

### Post by wallijonn on 2005-01-04
xleon,

Thank you. 

You helped me fix the same problem after my installing gdesklets. It blew up gnome-panel and gave me a !prefs-key=/apps/panel/profiles/default/applets/mixer (no schema) exists problem.

---

### Post by jbh on 2005-01-04
i had the exact same problem, CTRL_ALT_BACKSPACE fixed it

---

