---
title: "Desktop disappears on log out/in."
date: 2006-07-28
forum: Desktop Environments
---

### Post by Crypty on 2006-07-28
Hi. I have pretty big problem right now. Ubuntu is running great and I have the AIGLX+Compiz quinn package installed, also working fine. When I go to log out and log back in, it will do it's little loading thing for a second, then show my desktop, then all the sudden everything will disappear off the screen except for my wallpaper. At this point it goes unresponsive to everything I have tried and I have to reboot. 
My PC is a hp dv1340 laptop. 1.86ghz PM, 1GB ram, intel 915gm gpu. 
Any ideas?

---

### Post by hotani on 2006-07-28
Yup, same thing here. My advice: Stop using Compiz. That worked GREAT for me! ;)

If you do a ctrl+alt+backspace, that will restart X and then you'll be able to log in. I think it is a problem with the startup script that kicks off compiz (in your sessions -> startup apps) bombing out. 

That and the recurring "alt key problem" (alt key minimizes current window, so basically no alt-tab) are just 2 of the many reasons I've chosen to disable compiz on all my machines (2 desktops and a laptop).

---

