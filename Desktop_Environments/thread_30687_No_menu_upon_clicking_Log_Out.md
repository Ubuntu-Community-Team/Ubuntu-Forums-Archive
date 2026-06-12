---
title: "No menu upon clicking Log Out"
date: 2005-04-29
forum: Desktop Environments
---

### Post by beeldings on 2005-04-29
Perhaps I am overlooking something, but when I click the Log Out entry under the System menu in Gnome, it ends my session and returns me to the GDM. However, this hasn't always happened, I used to receive a menu upon clicking Log Out. From this menu, I could reboot the computer, shut down the computer, log out/end session, etc. But for some reason this menu no longer appears and I am logged out instead. I would like to point out that I can reboot and shut down the computer from the command line (sudo reboot and sudo shutdown -h now) and I can also turn off the computer by pressing the power button on the case. This isn't a huge problem, just a little annoyance. I can deal without the menu, but I taught my parents to shutdown and reboot the computer using that menu, and I don't want to throw too much at them with the CLI.

I feel as though I should mention that I previously used the 386 kernel when I had the menu. I recently upgraded to the 686 kernel, perhaps this has something to do with the menu not appearing?

---

### Post by shakin on 2005-04-29
I don't know what the problem is, but you should be able to access the shutdown and reboot actions from the GDM login screen, so you don't have to teach your parents to do it on the command line.

---

### Post by beeldings on 2005-04-29
> I don't know what the problem is, but you should be able to access the shutdown and reboot actions from the GDM login screen, so you don't have to teach your parents to do it on the command line.

I neglected to mention that I was able to access the Reboot and Shutdown commands from the GDM screen. I'm going to reboot the computer and run Linux with the 386 kernel and see what happens. I'll keep you posted.

---

### Post by Professor X on 2005-04-29
Go to System -> Preferences -> Sessions and find the option 'Ask on logout'.  Enable that option.

Hope that helps.

---

### Post by beeldings on 2005-04-29
[QUOTE=Professor X]Go to System -> Preferences -> Sessions and find the option 'Ask on logout'.  Enable that option.

Hope that helps.[/QUOTE]

Thanks for pointing that out, I don't remember disabling that option.

---

