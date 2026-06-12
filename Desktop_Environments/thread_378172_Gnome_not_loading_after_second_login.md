---
title: "Gnome not loading after second login"
date: 2007-03-06
forum: Desktop Environments
---

### Post by newbie455 on 2007-03-06
I am having a slight problem with gnome and I can't seem to find a solution anywhere. When I logout, I am taken to the splash screen. At the splash screen, I login, but all I get is a blank manilla page with a white box in the top left corner. I don't get the typical gnome loading box in the center of the screen.  Nothing happens even after waiting a few minutes. To fix this I have to reboot, and everything works fine until I logout and log back in.

By the way, this is a fresh install of 6.06 that I just upgraded to 6.10 hoping that would solve the problem.

Anyone else who has had this problem or knows what is going wrong here, I would appreciate your help. Thanks.

---

### Post by hameda on 2007-05-21
i am having the same problem. any helpers?

---

### Post by Freaky_Llama on 2007-05-27
Issue still exists on Feisty. Happens the same way as described. Only difference is that his machine has 2 users. If I log out and let my wife log in, then after she logs out, I get the problem on login.

I'd use fast user switching, but when I activate it, my trackpad is frozen and I can only type. Even after logging in, the mouse won't move.

---

### Post by Hex_Mandos on 2007-05-27
Try creating a new user account. When logged in, press Ctrl + Alt  + F1 to enter a virtual terminal. Log in with your username and password. Type the following command:

```
sudo adduser so-and-so
```

where "so-and-so" is the name of the new account you're creating. Press Ctrl + Alt + F7 to return to the graphical mode (or type sudo reboot to restart your computer), and log in to your new account.

Probably not the best solution, but it could work. Once, my account's GNOME was screwed like yours, but others' remained intact.

---

### Post by Freaky_Llama on 2007-05-28
I actually just installed the new Kernel update and it is working now. I highly doubt thats what fixed it, but I tried it afterwards to test and its fine.

I still have the issue with a dead trackpad but thats for a different thread.

Thanks.

---

