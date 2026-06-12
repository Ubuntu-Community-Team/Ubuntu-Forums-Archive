---
title: "Shortcuts and folders on the desktop have disappeared."
date: 2009-04-24
forum: General Help
---

### Post by 3ktl on 2009-04-24
All of the folders that were on my desktop have suddenly disappeared. And when i right click on the desktop nothing happens but only on the desktop. and the file that dont show on my desktop show up in my desktop folder. I cant even drag files to the desktop.HELP! What happened?

also the icons only disappear when i plug my iPod touch in. ubuntu 9.04 wasn't doing this before. when i unplug it they reappear. HELP. very annoying

---

### Post by wwusnobrdr on 2009-04-24
Hard to say exactly what happened.  Open up a command prompt and see what ls -al ~/Desktop tells you and post here.

---

### Post by 3ktl on 2009-04-24
bash: /home/asa/Desktop: is a directory
 thats what it says. 
I deleted the metedata file from the desktop folder on accident earlier today but i just restored and the icons come back until i plugged in my ipod touch then they went away again.

---

### Post by 3ktl on 2009-04-24
Thankyou for responding but i have solved the problem by reinstalling nautilus.

---

### Post by Seventh Reign on 2009-04-24
Did you try just Rebooting? .. That happens to me several times a week.  Rebooting always fixes it here.

---

### Post by allCuExpMa on 2009-08-17
or just restart the X-Server, works fine for me....T[m]

---

### Post by asmoore82 on 2009-08-17
Yes, the situation you describe is when nautilus crashes.

You can recover from it by hitting Alt+F2 and running ```
nautilus
```

---

