---
title: "How to change terminal font"
date: 2009-02-10
forum: General Help
---

### Post by camper365 on 2009-02-10
I am using Ubuntu Intrepid and want to change the font in the terminal (when I'm not using X)
I personally think that the font is ugly, and want to change it so that it looks like the BIOS font (it would be really nice if it looked like it does in SystemRescueCD)
I don't know what configuration file to edit, or anything else.

I am looking for the font when you are not using graphics. I think I am looking for the font that is in xfce, but I can't figure out how to use that font scheme instead of the default ubuntu one.

---

### Post by theozzlives on 2009-02-10
Go to edit > profiles, uncheck use system font under the general tab, then select your font.

---

### Post by roshanjose on 2009-02-10
if you are not happy with your current Terminal, then type

sudo apt-get install xfce4-terminal

This has good features and allows you to change font and also is well appreciated

---

### Post by lavinog on 2009-02-10
the op isn't talking about a gui terminal

have you tried increasing the resolution during bootup?
append vga=791 to the kernel line in /boot/grub/menu.lst
You can also try installing startup-manager which will let you configure the resolution for console text.

---

### Post by camper365 on 2009-02-10
> **theozzlives said:**
> Go to edit > profiles, uncheck use system font under the general tab, then select your font.

Where is edit > profiles?

---

### Post by theozzlives on 2009-02-10
> **camper365 said:**
> Where is edit > profiles?

Edit is at the top (where menus go).

---

### Post by camper365 on 2009-02-10
I am not talking about the terminal in GNOME, I am talking about when you press Ctrl+Alt+F1

---

### Post by lavinog on 2009-02-10
> **camper365 said:**
> I am not talking about the terminal in GNOME, I am talking about when you press Ctrl+Alt+F1

Did you read my post?

---

### Post by Locutus_of_Borg on 2009-02-11
on my system /etc/conf.d/consolefont controls the font displayed by tty's
ubuntu may have that in another location

you must use a font specified in /usr/share/consolefonts

---

