---
title: "xfce - black desktop problem"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Mr..Yeti on 2006-07-20
My xfce desktop has gone black. The icons are visible but they have changed to a different icon theme, and the right-click menu doesn't work.

It all started when I was looking through the menus and found an interesting thing called "Wastebasket Trash Manager" so I started it and then my wallpaper and menu went away.

I have searched the forums and tried other fixes. Including checking that the checkbox is ticked on the Desktop settings window. I have also tried starting xfdesktop as that is what I used to do when the menu wouldn't appear but that doesn't do anything. 

Can you recommend anything else?

---

### Post by Mr..Yeti on 2006-07-21
Does anyone know?
Do you need more information?
13hrs is a long time to go without right clicking on the desktop.

---

### Post by philippe_carlo on 2006-07-21
Did you try to run dpkg --reconfigure for the installation packages? Clearly, there's not an awful lot of ubuntu users using xfce.

---

### Post by Mr..Yeti on 2006-07-21
Does that mean reconfigure all of the packages that i have installed with xfce in their description? (the libs and thunar and applets) Or just the main xfce packages?

---

### Post by philippe_carlo on 2006-07-21
try 'm all, should not do any harm.

---

### Post by Mr..Yeti on 2006-07-21
Ack. It didn't work. 
I reconfigured all the xfce packages but my desktop is still black.

On a completely different note. I got my wacom graphics tablet working with instructions on the new wiki page. 

But I still need help with xfce. Don't go thinking I don't need your help.

---

### Post by -Phi- on 2006-07-21
Do you have nautilus installed? It might have taken over the desktop (though if the check box on the desktop settings is checked, I don't see why it would...) 

Also, does your Applications menu work at all? There's a known issue about the Menu Editor eating the menu (munch).

- Phi

---

### Post by Mr..Yeti on 2006-07-21
I have tried killing nautilus, but no process was killed. 
The thing that confuses me is that the icons in my desktop folder are still on the desktop. However, they have reverted back to the old "rodent" icon theme instead of the default human/tango one.

The applications menu that I added to my panel still works, and it hasn't changed.

---

### Post by Mr..Yeti on 2006-07-22
Come on! 
15 more hours have passed and it's still not fixed. This is the longest problem I have had with ubuntu. Just shows you how good it is. :p

---

### Post by Mr..Yeti on 2006-07-22
You should be happy to know that it is now fixed.

After logging into xfce as a different user and seeing what processes were running I found out the following:
That "xffm-deskview" was running.
and "xfdesktop" wasn't.

so after a killall "xffm-deskview" and a "xfdesktop" everything is working smoothly. So thanks for the help.
:D

---

