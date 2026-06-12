---
title: "PPC Problems with root and wifi"
date: 2005-10-13
forum: Desktop Environments
---

### Post by nicholaspaul on 2005-10-13
This is the beast: Powerbook G4, dual boot with Tiger and Hoary Kubuntu. 

When I open Control Center to set up the wifi (which is not being recognised - its an Airport Extreme card), after clicking on Administrator and entering the password (this is a new install, only one user, so i dont think there is a root password - correct me if I'm wrong) the  password box freezes. I can close the Control Center, so i know it hasnt 'crashed' .
Oh and sudo -s gives me the error: 
sudo: unable to lookup ubuntu via gethostbyname()
Password: postdrop: warning: unable to look up public/pickup: no such file or directory. 

Anyone?

---

### Post by nicholaspaul on 2005-10-13
I've since found out that I should use kdesu instead of sudo. 
But I still can't configure the airport extreme - iwconfig doesnt seem to work. What else should i use?

[edit]
Never mind.. for some reason I thought the Apple wifi issues were resolved.

---

