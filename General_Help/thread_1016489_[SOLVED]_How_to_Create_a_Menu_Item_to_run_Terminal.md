---
title: "[SOLVED] How to Create a Menu Item to run Terminal as Root"
date: 2008-12-20
forum: General Help
---

### Post by tommygunner on 2008-12-20
I would like to create a menu item so that it does something like:

sudo su

What is the best way to do this. I can't do this directly in the menu it seems. 

I also created an menu item to run Nautilus as sudo using "Create Luncher" and then linking to this file in the menu.

Also, if I have to create a bunch of Launcher files for this, is there a good place to store these?

---

### Post by logos34 on 2008-12-20
I thought Nautilus included a default scripts item

File>Scripts>

-Browse as Root
-Open with gedit (as root)
-Scripts folder

(I'm on 8.04)

---

### Post by tylerspaska on 2008-12-20
run 'alacarte' and you can add 'root terminal' to the 'system tools' menu

---

### Post by marmuta on 2008-12-20
There should already be a hidden entry "Root Terminal" in Applications->System Tools. Just unhide it with System->Preferences->Main Menu (alacarte).

You can actually use "sudo su" too if you choose "Application in Terminal" in the launcher.

For gui applications it's safer to use gksu insted of sudo. So better do "gksu nautilus".

System Tools or System->Administration are probably good spots to put it in, though it really doesn't matter where. You could even add a new menu for your own stuff in alacarte.

---

### Post by tommygunner on 2008-12-20
> **tylerspaska said:**
> run 'alacarte' and you can add 'root terminal' to the 'system tools' menu

Cool, thanks. I see "Root Terminal" now there. It was unchecked by default, fixed now.

---

### Post by logos34 on 2008-12-20
forgot about 'root terminal' in sys tools (but then I just sudo -i if I need to in cli)

So, anyone, does Intrepid Nautilus have a gksudo nautilus script menu item under File?     I thought it was default (at least I think it is in 8.04--or maybe I put it there and don't remember?)

---

### Post by marmuta on 2008-12-20
I believe i've added an open-in-root-terminal manually to the nautilus scripts. But that was long ago. 
Nowadays I just sudo apt-get install nautilus-open-terminal and then sudo from there.

---

### Post by mc4man on 2008-12-20
> gksudo nautilus script menu item under File? I thought it was default

Never seen it unless it was added like a nautilus-action

There is a nautilus-gksu package (open as administrator) but it's optional

---

### Post by logos34 on 2008-12-20
> **mc4man said:**
> 
There is a nautilus-gksu package (open as administrator) but it's optional

I just tried to install that and I apparently didn't already have it...

oh well

---

### Post by tommygunner on 2008-12-20
Yes, I too installed nautilus-gksu and nautilus-open-terminal.

I can see the Open as Administrator thing now in Nautilus but am not sure what nautilus-open-terminal does.

Regarding, the Root Terminal menu item, it works but has an ugly  font instead of the nice bold font the default Gnome-Terminal one has.

---

