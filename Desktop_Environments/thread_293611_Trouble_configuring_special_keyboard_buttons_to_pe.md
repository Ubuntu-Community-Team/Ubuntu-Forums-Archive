---
title: "Trouble configuring special keyboard buttons to perform a shutdown sequence"
date: 2006-11-05
forum: Desktop Environments
---

### Post by Turin Turambar on 2006-11-05
Here's what I want:
I'd like to press one button and be able to shutdown the PC.

I know about Configuration Editor / Apps / Metacity / Globalkeybindings & Keybinding_command (that's for mapping the keys to run certain commands & actions).

Firstly, I cannot use the Sleep button of my keyboard! It's mapped as *XF86Sleep*. However, although I did everything I could in Configuration Editor, nothing happened when I pressed that button. It just ignored it. But when I mapped another one like "F2" or "ctrl-break", it was ok. Any hints?

Everything I tested here was to be able to run some programs (like "gedit"). When I actually tried the shutdown, I didn't have any luck.

In keybinding_command I set *gksu shutdown -h now*
However, nothing happened, because gksu couldn't be used with "-xyz" commands. Is there a way to:
1. Enter a root password
2. Shutdown afterwards

Is it possible to call the "Quit" menu (System/Quit) from a command prompt?

Thanks!

---

### Post by Turin Turambar on 2006-11-06
bump

---

### Post by Turin Turambar on 2006-11-12
Duh?!

---

### Post by abbeychase on 2006-11-13
you could always try that button on your computer case.  that always works for me for one button saluting...

---

### Post by Turin Turambar on 2006-11-14
Thanks, but, unfortunately that didn't work...

---

### Post by tater_3001 on 2006-11-14
Is Turin your real first name?
it sounds just like mine .... Turner... :P 
srry no clue bout your buttons...

---

### Post by CatKiller on 2006-11-14
Actually, the Power button on the keyboard has always brought up the shutdown dialogue for me. Which is nicer than Windows that just shuts down when the cat stands on the keyboard when I'm in the middle of something.

But then my keyboard is configured in X as being 105 keys. I haven't counted them, but it seems like it could be about right. Perhaps yours isn't configured for enough keys?

---

### Post by Turin Turambar on 2006-11-16
> **tater_3001 said:**
> Is Turin your real first name?
it sounds just like mine .... Turner... :P 
srry no clue bout your buttons...

No, it's a character from Tolkien mythology... Silmarillion and Unfinished tales. :)

Still no use from power/sleep button though.

---

### Post by iwsx2 on 2006-11-25
I used the Gnome configuration Editor. Apps / Gnome-power-management then changed the value for action_power_button to shutdown. It worked for me. 


/apps/gnome-power-manager/action_button_power

The action to take when the system power button is pressed. Valid values are "suspend", "hibernate", "interactive", "shutdown" and "nothing".

Regards,

Ian

---

### Post by Turin Turambar on 2007-01-03
Hey, thanks! Now that works!! :D

---

