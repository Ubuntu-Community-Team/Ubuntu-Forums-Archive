---
title: "what happened to the menu?....."
date: 2006-07-30
forum: Desktop Environments
---

### Post by someguyouknow on 2006-07-30
i am missing some options on the right click menu for icons on the desktop.....
i use to be able to right click and copy or move items to another location but now i am not able to.....
any help?.....

---

### Post by someguyouknow on 2006-07-30
hmmm.....
guess not.....
i dunno why it just disappeared.....

---

### Post by ryno on 2006-07-30
have sorta same prob except i got no menu what so ever after trying to run menu editor. anyone out there with some info on the subject. Im trying out xubuntu and so far its not looking good.

AMD 3000+
512 DDR
20 gig hd
fx5500 
sb pci128

---

### Post by someguyouknow on 2006-07-31
you have no menu on right clicks on the desktop or on icons?.....

---

### Post by -Phi- on 2006-07-31
The menu getting eaten by the editor is a [known issue]("https://wiki.ubuntu.com/XubuntuDapperReleaseNotes#head-b38e122d8c9dc3a3a68b3b1704231a9e90ca7361") for Xubuntu. Their suggested solution may not work. A more permanent solution is to copy the default menu.xml from /etc/xdg/xfce4/desktop/menu.xml to ~/.config/xfce4/desktop/menu.xml (note that ~ is your home directory, and that if you use a specific region menu, you may need to choose menu.xml.YOURCOUNTRYCODE  such as .eu, .fr, .ca)

I'm not sure if this is what the original poster is asking.

- Phi

---

### Post by someguyouknow on 2006-07-31
nah..... 
not a solution for me.....
no worry, i can live with it.....
i just want to know what happened to it.....

---

### Post by someguyouknow on 2006-08-03
[IMG]http://i35.photobucket.com/albums/d155/someguyouknow/snapshot8.jpg[/IMG]
Thats how it looks now.....
There was no share option, and there was the option to move/copy the item to another location right about the properties option.

---

