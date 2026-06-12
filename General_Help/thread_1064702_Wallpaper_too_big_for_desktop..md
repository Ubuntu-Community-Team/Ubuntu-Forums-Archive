---
title: "Wallpaper too big for desktop."
date: 2009-02-09
forum: General Help
---

### Post by G-Dub on 2009-02-09
Hello, I am running ubuntu 8.10 on my HP Mini 1000. I recently changed the desktop to one of massive proportions (aka very high resolution). Now when ever I start ubuntu and log in it goes to a screen filled with lines and colored blocks. I cannot do anything with it. I can log into fail safe terminal mode though, is there a way to delete the desktop wallpaper via terminal?

---

### Post by jman6495 on 2009-02-09
It's Not Your Wallpaper , You Have Configured Your Reolution Higher Than Your Screen Can Take.

Solution :
When Your Computer Is Starting Up And It Says Press Esc To Enter Grub ,Press Esc And Select Ubuntu Recovery (Or Similar)

After A While You Will Be Presented With A Menu.
Go To The "Fix X" Option And hit Enter.
After Thats Done Click Resume Normal Startup,
it Should Boot Normaly.


Hope This Helps ,
DONT SELECT THAT RESOLUTION AGAIN! :-)

   Jman6495

---

### Post by G-Dub on 2009-02-09
Thanks for your fast reply Jman! I actually tried fixing x-server already, it didn't work. I even went in the console and tried ```
sudo dexconf
``` and ```
sudo /etc/init.d/gdm restart
```

When I boot the computer up, it shows me the Ubuntu logo and asks for my user name and password. At this point I am also able to select my session type. But whenever I login to Gnome it gives me those lines.
The only thing I did was change the desktop background to a really hi res background. After I restarted the computer, it gave me those lines.

---

### Post by stalkingwolf on 2009-02-09
after you are booted to the desktop , right click on the desktop
(any open place will do). select change desktop background, then select one of the default backgrounds. click apply.

that should get you back.

---

### Post by G-Dub on 2009-02-09
i can't right click when i boot up! it gives me the colored stripes like in that picture.

---

### Post by sujoy on 2009-02-09
take a backup of /etc/X11/xorg.conf and then run xorgconfig. go through the setup and you should be alright.

---

### Post by jman6495 on 2009-02-11
try reinstalling Gnome
i think you need to type CTRL+ALT+F1
Logon From Terminal
type sudo apt-get install gnome
(I Think)

   Jman6495

---

