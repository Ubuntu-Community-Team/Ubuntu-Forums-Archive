---
title: "So what's wrong with this desktop launcher?"
date: 2022-08-31
forum: Desktop Environments
---

### Post by kpov-staff on 2022-08-31
Hi, new install of 22.04 on an HP laptop. I have a few .desktop items, one refuses to launch when double-clicked. Here's the details: 

The text in the .desktop is:
[FONT=fixedsys]
[Desktop Entry]
Name=Xtrlock
Comment=Lock keyboard and mouse requiring user password to unlock
Exec=/usr/bin/xtrlock
Icon=/usr/share/icons/Humanity/status/24/stock_lock.svg
Terminal=false
Type=Application
Categories=System;Settings;GTK;HardwareSettings;[/FONT]

The same file is in /usr/share/applications. It has been added to my Dock as a Favorite and it launches from the Dock, no questions asked. But the Desktop launcher does not launch when I click/double-click/smack it with a croquet mallet. It is set to Allow Launching and if I right-click > Open, it launches. 

Other items that I've created .desktop launchers for do launch when clicked. This one is stubborn. I am puzzled. 

Thank you!

---

### Post by vanadium on 2022-08-31
<snip> invalid solution

---

### Post by kpov-staff on 2022-08-31
Thank you, I already tried that but to be thorough I just tried that again and no joy.

---

### Post by ajgreeny on 2022-08-31
I had not even heard of **Xtrlock** but I assume it is a command line application.
Just to test it I have just installed it, copied your launcher text and saved it as **lock.desktop** file and it works perfectly.

However, I use Xubuntu not Ubuntu and I know there are some differences related to using launchers in the two different DE systems.  Ubuntu is the DE version about which I know very little so I will have to let you search more.

Suffice to say, your launcher works fine for me and I have no idea why it's not working for you.

---

### Post by kpov-staff on 2022-08-31
Thank you for taking a swing at it!

---

### Post by col48 on 2022-09-06
I haven't got an answer.. But a couple of thoughts.

Another way of launching from Desktop is single click on the icon to highlight it and then after a short pause pressing Enter.  Or perhaps that's your croquet mallet?

Have you tried copying a launcher that works (ie Copy/Paste in the File Manager looking at the Desktop folder) and carefully editing the copy with gedit to change Name and Exec to what you want?  You never know, that might avoid whatever the real problem is.

---

### Post by Rocket J Squirrel on 2022-09-06
The "highlight it and then after a short pause pressing Enter" approach would be fine for me, but this machine is likely to be used by other technicians or staff if I'm not around, and things need to be straightforward, no puzzling methods to launch the program. Yes, good suggestion about editing and saving-as an existing, working .desktop launcher, and I did try that just in case there was a hidden problem, but no, no that didn't do the job. It is a puzzle. Thank you!

---

