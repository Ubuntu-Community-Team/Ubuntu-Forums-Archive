---
title: "Ubuntu Crashed!!!! Help"
date: 2006-07-30
forum: Desktop Environments
---

### Post by moataz on 2006-07-30
hello, 
while i was upgrading using the upgrade manager in ubuntu, my laptop battery went dead and the laptop shut down, now everytime i boot up ubuntu i dont get anything on the screen except the background after i log into my account. any advice on how to restore my computer. thanks

---

### Post by Seaman on 2006-07-30
When you have (unsuccesfully) logged in to your account press **ctrl+alt+F2** and you will come in to command-line interface. Login and enter the command **sudo apt-get dist-upgrade** which will complete your upgrading. When it is finished with the updating, run **sudo reboot** (which will make the computer reboot). Hopefully this will help, if not, try selecting the gnome fail-safe before logging in.

---

### Post by x64Jimbo on 2006-07-30
Can you change to text terminal?? Ctrl+Alt+F2
If so, you can do this:
sudo aptitude update
sudo aptitude upgrade
That should get you up and running.
[edit] hee hee great minds think alike [/edit]

---

### Post by moataz on 2006-07-30
hey guys, thanks alot for the help its up and running and im posting from it right now
one last problem u guys though, my GRUB loaded now has 4 entries for ubuntu, 2 for safe mode and 2 for the regular log on. how do i get rid of that?

---

### Post by Seaman on 2006-07-30
Why do you want to get rid of that? It is recommended that you have some safe  modes and one or two older kernels to boot from except your current. If you want to remove the alternatives anyway you can do so in */boot/grub/menu.lst*
**EDIT: A reminder, be carefull while editing menu.lst**

---

### Post by x64Jimbo on 2006-07-30
> **Seaman said:**
> Why do you want to get rid of that? It is recommended that you have some safe  modes and one or two older kernels to boot from except your current. If you want to remove the alternatives anyway you can do so in */boot/grub/menu.lst*
**EDIT: A reminder, be carefull while editing menu.lst**
I removed them from my default boot because I don't like the clutter. However, I didn't delete them. I commented them out. So in case I ever need to use them again and my system is fubar, I can simply boot a livecd, uncomment the lines, and play with older configs. That's what I would recommend for cleaning up your GRUB menu.

---

