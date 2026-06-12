---
title: "Default keyboard, not default Gnome login screen language"
date: 2005-07-03
forum: Desktop Environments
---

### Post by N'Jal on 2005-07-03
I use a dvorak keyboard and when i am greated to the gnome login screen it's stuck with the qwerty layout, how can i change this? Don't mind editing x.conf as long as someone tell's me what line's to edit.

---

### Post by Tomy on 2005-07-04
[QUOTE=N'Jal]I use a dvorak keyboard and when i am greated to the gnome login screen it's stuck with the qwerty layout, how can i change this? Don't mind editing x.conf as long as someone tell's me what line's to edit.[/QUOTE]
My xorg.conf file looks like this:
 ```
Section "InputDevice"
		Identifier	  "Generic Keyboard"
		Driver		  "keyboard"
		Option		  "CoreKeyboard"
	    Option		  "XkbRules"	  "xorg"
	    Option		  "XkbModel"	  "pc105"
	    Option		  "XkbLayout"	 "dvorak"
EndSection

``` 

This may not solve the gnome qwerty login. When I installed Ubuntu Hoary I selected a dvorak keyboard in the early part of the install and I do have a dvorak gnome login. I belive there is some other setting prior to starting the xserver that also needs to be changed.

On a qwerty system when I switch to a terminal using ctrl-alt-fx I always have to type "loadkeys dvorak" after I login with qwerty. Ctrl-alt-fx on my system comes up to a dvorak login. Unfortunately I don't know how to make this the default if it was not chosen on original hoary installation.

Tomy

edit:
Try this[ thread]("http://ubuntuforums.org/showthread.php?t=31918")

---

### Post by N'Jal on 2005-07-05
It was chosen on installation that's what annoys me.

EDIT: My keyboard was NOT set to dvorak in xorg.conf. It was GB changed it to dvorak and will see what happens.

---

### Post by uberlinux on 2005-07-05
[QUOTE=N'Jal]It was chosen on installation that's what annoys me.[/QUOTE]
I think that you can go to system-->keyboard--> and click the box that says dvorak.

---

### Post by N'Jal on 2005-07-05
You can but that affects local settings rather than global settings.

---

### Post by Tomy on 2005-07-05
[QUOTE=N'Jal]I use a dvorak keyboard and when i am greated to the gnome login screen it's stuck with the qwerty layout, how can i change this? Don't mind editing x.conf as long as someone tell's me what line's to edit.[/QUOTE]

I just remembered how you do this - maybe?

Go to Systems>Preferences>Keyboard. Select the Layouts tab and then move dvorak up so it is the first entry.

Tomy

---

### Post by Tiede on 2005-07-18
Try this:
[http://www.ubuntuforums.org/showthread.php?p=72622#post72622](http://www.ubuntuforums.org/showthread.php?p=72622#post72622).
That is what I did when I needed to change my keyboard layout and it worked greatly. :)

---

