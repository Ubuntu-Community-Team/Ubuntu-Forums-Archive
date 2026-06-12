---
title: "Login Window - Backgrounds not showing up"
date: 2006-09-26
forum: Desktop Environments
---

### Post by doogleplex on 2006-09-26
I am relatively new to Ubuntu, and have mild exposure to Unix/Linux systems...

I have an issue where the backgrounds for the Login Window don't show up. I used (in gnome) **System-Administration-Login Window** to assign them...I have even launched manually  using 'sudo gdmsetup' to verify that rights are given to the procedure (even though I am prompted for sudo credentials in the graphic environment, and that is working normally)...The images are the Background Image and Logo Image at the Login Window.

I have confirmed that in /etc/X11/gdm, the gdm.conf-custom file is correctly showing the images I would like displayed. Recently, I believe an updated nvidia-glx was installed, and although I am not certain, I believe this may have occured directly before this issue began. I have tried images from confirmed permissive locations, so I am confident permissions are not the issue. Has anyone experienced this?
Thanks. I haven't included any files here. If necessary, please advise me on which files you may want to see...thank you.

---

### Post by Brunellus on 2006-09-26
I'm moving this to general desktop support in hopes that they'll know what's going on.  I've not played with gdm too much....

---

### Post by doogleplex on 2006-09-26
thank you

---

### Post by doogleplex on 2006-09-26
I am relatively new to Ubuntu, and have mild exposure to Unix/Linux systems...

I have an issue where the backgrounds for the Login Window don't show up. I used (in gnome) System-Administration-Login Window to assign them...I have even launched manually using 'sudo gdmsetup' to verify that rights are given to the procedure (even though I am prompted for sudo credentials in the graphic environment, and that is working normally)...The images are the Background Image and Logo Image at the Login Window.

I have confirmed that in /etc/X11/gdm, the gdm.conf-custom file is correctly showing the images I would like displayed. Recently, I believe an updated nvidia-glx was installed, and although I am not certain, I believe this may have occured directly before this issue began. I have tried images from confirmed permissive locations, so I am confident permissions are not the issue. Has anyone experienced this?
Thanks. I haven't included any files here. If necessary, please advise me on which files you may want to see...thank you.

---

### Post by doogleplex on 2006-09-27
Oh well, I'll be looking further into this. Obviously the system is fine otherwise, it just seems odd that the content of text file gdm.conf-custom seems ok, and still, no pictures on the login window...I can impose a theme on the login just fine... weirdness.
If I find out, be sure I'll drop a note back in here. Thanks for those 41 (up to now) that gave a look.

---

### Post by doogleplex on 2006-10-02
I ended up putting the amd64-generic Ubuntu 6.06 on this same pc, replacing the partitions and so on, and guess what; after the restricted update and the nvidia-glx update, no backgrounds on the login window...same behavior as before. So it must be one of the updates doing this. The login window is there, but backgrounds just simply cannot be assigned.

---

### Post by doogleplex on 2006-10-17
I believe it's a permissions issue.

---

### Post by kvonb on 2006-10-17
I get the same thing when I log out sometimes, and if I <ctrl-alt-backspace>, sometimes it gives me a "rainbow" effect on the screen and locks up!

I am wondering if it is the ati driver, I'm using 8.26.8.

---

