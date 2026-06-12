---
title: "Firefox Does Not Work"
date: 2009-06-18
forum: General Help
---

### Post by medcalf on 2009-06-18
Hi, I am an Ubuntu newbie and have just installed it side by side on my new windows machine.  All seems fine apart from getting onto the net via Firefox.  Every time I start it it appears top left in a small window and then an Alert box appears which says: Could not initialise the applications security component.  The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read write restrictions and your hard drive is not full, it is recommended that you exit the application and fix the problem. If you continue to use this session you might see incorrect application behaviour when accessing security features.'  I am not sure where the application files are kepy so I found a dir called 'usr' and tried to apply read write to that but it would not let me.  Any help appreciated and thanks in advance.

Steve M

---

### Post by mynameinc on 2009-06-18
> **medcalf said:**
> Hi, I am an Ubuntu newbie and have just installed it side by side on my new windows machine.  All seems fine apart from getting onto the net via Firefox.  Every time I start it it appears top left in a small window and then an Alert box appears which says: Could not initialise the applications security component.  The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read write restrictions and your hard drive is not full, it is recommended that you exit the application and fix the problem. If you continue to use this session you might see incorrect application behaviour when accessing security features.'  I am not sure where the application files are kepy so I found a dir called 'usr' and tried to apply read write to that but it would not let me.  Any help appreciated and thanks in advance.

Steve M

May be a corrupt install.  Did you MD5 the image and "Check CD for defects"?

---

### Post by Cheesemill on 2009-06-18
/usr doesn't hold user files, it stands for **U**nix **S**ystem **R**esources

Your FireFox profile settings are in ~/.mozilla

---

### Post by medcalf on 2009-06-18
No I didn't checksum it, I downloaded 9.04 and did what it said ref the installation.  Is it possible to uninstall it and try again and if so how?

---

