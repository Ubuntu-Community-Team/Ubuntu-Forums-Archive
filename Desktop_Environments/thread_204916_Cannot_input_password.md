---
title: "Cannot input password"
date: 2006-06-27
forum: Desktop Environments
---

### Post by artmoe on 2006-06-27
I just did a fresh install of Dapper. The install went fine. Now I want to change the boot order so that my Windows XP Pro will be the first OS to boot. However when i try to change the boot order by typing in my password so that i have admin access, my password doesn't input. Of course I've checked my "num lock", and have tried typing in another box outside of the password box. For some reason Ubunto Dapper doesn't allow me to gain admin rights to make changes. Is there a workaround for this or did something go wrong during the install? Thanks.

---

### Post by bDerrly on 2006-06-27
You said you checked "num lock", how about "caps lock"?  Also, can you attain admin privileges from the console with the same password using sudo?  Try `sudo su' and see if you get a root prompt.  You're using the same user account as the first account created during install, correct?

---

### Post by artmoe on 2006-06-27
[QUOTE=bDerrly]You said you checked "num lock", how about "caps lock"?  Also, can you attain admin privileges from the console with the same password using sudo?  Try `sudo su' and see if you get a root prompt.  You're using the same user account as the first account created during install, correct?[/QUOTE]
Yes, I've checked the caps lock. And I'm using the same user account as the one I firest created during install. As fars as gaining admin privileges, when I go to applications, accessories, terminal and type "sudo su", a password request comes up, but cannot type any numbers or letters. I've tried the key pad and numbers above the letters.

---

### Post by RRS on 2006-06-27
[QUOTE=artmoe]Yes, I've checked the caps lock. And I'm using the same user account as the one I firest created during install. As fars as gaining admin privileges, when I go to applications, accessories, terminal and type "sudo su", a password request comes up, but cannot type any numbers or letters. I've tried the key pad and numbers above the letters.[/QUOTE]

When you type your password in terminal it remains blanked, no **'s or anything for security reasons. Simply type in your password and hit "Enter".

---

### Post by artmoe on 2006-06-28
[QUOTE=RRS]When you type your password in terminal it remains blanked, no **'s or anything for security reasons. Simply type in your password and hit "Enter".[/QUOTE]
Wow. You're right. That was pretty dumb. 
Now that I can get admin rights and have looked in the boot menu to change my boot order, I followed a "how to" that says look for "default O" but cannot find it. Do you have any ideas on how to change my boot order from Ubuntu to Windows XP. I don't want to have to always select "Windows XP" when I turn my computer on. Thanks.

---

### Post by aysiu on 2006-06-28
[quote=artmoe]followed a "how to" that says look for "default O" but cannot find it.[/quote] It's at the very beginning of the /boot/grub/menu.lst file.

---

### Post by marlboroman on 2007-12-04
the same thing just got me I was about to take my key bord to bits :confused:

I'm glad some on else got to ask this qustion :)

---

