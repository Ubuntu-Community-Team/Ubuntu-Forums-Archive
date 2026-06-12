---
title: "How to get the c cedilla &quot;ç&quot; in Ubuntu 10.10 with a US International Keyboard"
date: 2010-10-31
forum: Desktop Environments
---

### Post by imcampos on 2010-10-31
I just solved this problem, inspired by a previous post in this forum, that worked perfectly for release 10.04. 
Here's how I did it in Ubuntu 10.10:
Open Applications/Accessories/Terminal
Type gksudo gedit in order to get editing rights to system files. 
The system will ask you for your password.
After that, and if you have the authority, it will open the file browser with editing rights.
Navigate to usr/lib/gtk-2.0/2.10.0/gtk.immodules
There is pair of lines that look just like this:

"/usr/lib/gtk-2.0/2.10.0/immodules/im-cedilla.so" 
"cedilla" "Cedilla" "gtk20" "/usr/share/locale" "az:ca:co:fr:gv:oc:pt:sq:tr:wa" 

You just add :en after :wa and save the file.

The two lines should now look like shown below:
"/usr/lib/gtk-2.0/2.10.0/immodules/im-cedilla.so" 
"cedilla" "Cedilla" "gtk20" "/usr/share/locale" "az:ca:co:fr:gv:oc:pt:sq:tr:wa:en" 

Now exit the file browser, restart Ubuntu, and you're done. If you now type a comma followed by a c it should produce a ç.

---

### Post by hrickh on 2010-10-31
If you use the right-alt key, you should be able to get the cedilla (ç) just by typing right-lat plus comma. No changes needed.

R.
==

---

### Post by julianamd on 2010-11-29
Thank you imcampos! That was really helpful :-)

---

### Post by alroger on 2010-12-14
Thanks man. Can't believe we still have to change this manually.

---

### Post by vanessa on 2010-12-15
Thanks, I was trying to edit the wrong file

---

### Post by StephenDavison on 2010-12-15
FWIW you can get c cedilla on the USA keyboard without making that change.  In Keyboard Preferences, Layouts, I have only "USA" listed.  I selected it, and then opened the Options dialog box.  In the "Compose key position" I selected Menu and Right Alt.  Selecting both just made it easy for me on my MSI netbook's small keyboard.

I get c cedilla with right-alt, comma, c.  I also get accents, tilde,  and umlaut.

accented e: right-alt ' e
n tilde: right-alt ~ n

and so on.

Edited to add:
My keyboard model shows as "Generic 105-key (Intl) PC."  I'm pretty sure that was the default selected during the install inasmuch as I don't remember changing it since.

---

### Post by vanessa on 2010-12-15
Yes, I saw that shortcut above, but I'd rather use the same key combination on all computers that I use. It'd drive me crazy to use '+c on Windows, Option+c on Mac and Alt+,+c on Linux!

---

### Post by StephenDavison on 2010-12-15
Ah, I missed the previous post with the shortcut.  Nevermind.

---

### Post by vanessa on 2010-12-15
Fixed

---

