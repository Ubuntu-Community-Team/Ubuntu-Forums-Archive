---
title: "how to configure ubuntu to prompt for a passeord after the screen is locked"
date: 2010-10-27
forum: Desktop Environments
---

### Post by rockercya on 2010-10-27
hi
 
i need to knw is the a way to configure the ubuntu desktop to prompt for a password when relogin after the screen is locked? 
 
it asks for a username and password a at the login prompt if i relogin after logging out out but  when i lock the scree by pressing ctrl +alt + l and try to relogin it will not ask for a password , it just  let me log in automatically to the pc , i think this is a security issue cos anyone else can login to my pc without prowiding credentials ,  
 
how to overcome this issue
 
pls help
 
thanx

---

### Post by lisati on 2010-10-27
One option might be to click on System->Preferences->Screensaver and check both "Activate screensaver when computer is idle" and "Lock computer when screensaver is active"

---

### Post by rockercya on 2010-10-27
hi
 
i tried that but it only works with regular user accounts , not with root account , is there a way to configure to prompt for password for root if trying to log in after the screen is locked??
 
 
thanx

---

### Post by wolvorin on 2012-11-08
I am facing same issue. When I logged in with root, it won't prompt for password for screen lock.

Any help....???

---

### Post by alkh3myst on 2012-11-08
It's not necessary to use the root account; that's why it's disabled by default. Your system is much less secure this way. Even worse, an inexperienced user running the root account can do major damage to their filesystem by accident. Using a normal user account for yourself, "sudo" grants temporary root privileges in the terminal, and "gksudo" (also entered in the terminal) gives you root for apps with GUIs. Spare yourself the heartbreak and delete your root password. Linux is only the most secure OS for those who don't defeat the security by their own actions.

---

