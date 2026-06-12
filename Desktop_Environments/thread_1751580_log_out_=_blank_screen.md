---
title: "log out = blank screen"
date: 2011-05-06
forum: Desktop Environments
---

### Post by reiki on 2011-05-06
New to KDE (Ubuntu with Gnome since 2005) and noticed upon logout I get a black screen with just a mouse pointer. It never returns to the graphical login screen. I can use cntrl+Al+F1 to get to a TTY and type sudo restart kdm and it gets me back to the graphical login. 

Googling this I see it is an issue that's been around since at least 2006. Various distribs so probably not *buntu specific.

I edited a file called kdmrc and uncommented a line saying "Terminate-server=true" and now when I log out it goes back to the login screen. But I'm wondering if that's a CORRECT way to resolve the issue. The solution came from a post that is YEARS old.

thanks for any help

---

### Post by jonathan22 on 2011-11-06
Thank you.  That solution worked for me after restarting.  Google search results showed the same blank screen problem continuing in 2011, with the same fix being suggested.  I just installed Kubuntu 11.10 today.

---

### Post by sleepitoff on 2011-11-06
where is the kdmrc file located? I'd like to try this fix 

the black screen logout seems to be a bug with a desktop effect. If I disable desktop effects before logging out, it will log out correctly, but if desktop effects are enabled, I get the same black screen.

edit: 
kmrc is located at /etc/kde4/kdm/ 
there was no line for "Terminate-server=true" listed, so I added it to [X-*-Core] and now logging out is working again. thanks.

---

