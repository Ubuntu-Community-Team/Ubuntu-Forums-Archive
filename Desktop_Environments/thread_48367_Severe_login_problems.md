---
title: "Severe login problems"
date: 2005-07-12
forum: Desktop Environments
---

### Post by Aragorn992 on 2005-07-12
I was playing around with alot of the settings in 'application preferences', I forget exactly which ones I set / changed but I know one was to automatically login my user 'aaron' on first boot. At no time did I enter or change my password.

Now everything is fine except whenever I need to enter a password (e.g. locked screen, loging off then on again, doing sudo stuff) it ALWAYS says my password is incorrect. I never changed my password though! (also ive tried using nothing for a password without success)

Something has really stuffed up, is there any way I can reset the user accounts or sort this out? Remember I can't access anything requiring the user password such as 'users and accounts'. I do have a windows dual boot, and many live CDs lying around.

---

### Post by runenes on 2005-07-12
Your password should not have changed without you explicetly changing it. Are you sure you haven't forgotten it, or changed it?

You can try this untesed and little detailed method. NO WARRANTIES:
1. boot up a live cd.
2. become root.
3. open terminal and mount the root partition where ubuntu is installed.
4. type: chroot /mnt/point (Or wherever you mounted the partition).
5. type: passwd YOUR_USERNAME, and type in new password.
6. Reboot.

---

### Post by JayCnrs on 2005-07-12
[QUOTE=runenes]Your password should not have changed without you explicetly changing it. Are you sure you haven't forgotten it, or changed it?

You can try this untesed and little detailed method. NO WARRANTIES:
1. boot up a live cd.
2. become root.
3. open terminal and mount the root partition where ubuntu is installed.
4. type: chroot /mnt/point (Or wherever you mounted the partition).
5. type: passwd YOUR_USERNAME, and type in new password.
6. Reboot.[/QUOTE]
 At boot up where you see Grub and countdown timer press the ESC button, then choose recovery mode and hit enter then follow step 5 and 6 from above, that should allow you to change your password.

---

### Post by Aragorn992 on 2005-07-12
Alright thanks ill try those.

It seems to have changed overnight. I boot up this morning and my old password is working for everything, except when I open up a regular terminal, then type "su" and enter my password it says "Authentication failure" !?!?

However I can just open a root terminal (or any other graphical application), type my password into the prompt and it works fine.

---

### Post by JayCnrs on 2005-07-12
[QUOTE=Aragorn992]Alright thanks ill try those.

It seems to have changed overnight. I boot up this morning and my old password is working for everything, except when I open up a regular terminal, then type "su" and enter my password it says "Authentication failure" !?!?

However I can just open a root terminal (or any other graphical application), type my password into the prompt and it works fine.[/QUOTE]
 When you want to have a root terminal you need to open the terminal then type **sudo -s**, this will then ask for your password, put in your password and you will have a root terminal.  

HTH :)

---

### Post by runenes on 2005-07-13
**sudo** takes your password **su** takes the super users (aka root) password.

---

