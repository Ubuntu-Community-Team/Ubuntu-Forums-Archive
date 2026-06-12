---
title: "partitions  at desktop disappear at restart"
date: 2010-09-03
forum: Desktop Environments
---

### Post by rebrov on 2010-09-03
when i open partition from the menu like Mp3 or software partition it appear on desktop to make it easier to access it again 

i like that however when i restart my pc it disappear again 

can't i make all my partitions on desktop and never disappear ??

---

### Post by tom4everitt on 2010-09-04
What I think you want is called auto mounting. Normally when you plug in a mp3 player for instance, Ubuntu will automatically mount it. It will also be mounted when you click on it in the Nautilus menu. Once mounted, it will stay mounted until you unmount it or restart your computer. 

To have external devices automatically mount during boot, you can either manually edit the file /etc/fstab which controls the mount settings. (There are lot of guides on how to do that if you google it.) If you don't want to get into that, you can also try a program called pysdm, which is available in the software center. 

Here's a blog post related to what you want to do:
[http://sathyasays.com/2008/10/08/how-to-automount-hard-drive-partitions-everytime-you-login-in-linux/](http://sathyasays.com/2008/10/08/how-to-automount-hard-drive-partitions-everytime-you-login-in-linux/)

---

### Post by rebrov on 2010-09-04
> **tom4everitt said:**
> What I think you want is called auto mounting. Normally when you plug in a mp3 player for instance, Ubuntu will automatically mount it. It will also be mounted when you click on it in the Nautilus menu. Once mounted, it will stay mounted until you unmount it or restart your computer. 

To have external devices automatically mount during boot, you can either manually edit the file /etc/fstab which controls the mount settings. (There are lot of guides on how to do that if you google it.) If you don't want to get into that, you can also try a program called pysdm, which is available in the software center. 

Here's a blog post related to what you want to do:
[http://sathyasays.com/2008/10/08/how-to-automount-hard-drive-partitions-everytime-you-login-in-linux/](http://sathyasays.com/2008/10/08/how-to-automount-hard-drive-partitions-everytime-you-login-in-linux/)

ooh i got it ..lol i was doin it all the time in backtrack 4 :) but never knew that its the same in ubuntu :) thanks alot buddy for guiding me :)

---

### Post by rebrov on 2010-09-04
i tried it but didn't work 

when i press places menu and then choose computer ...

then open the software partition the wallpaper that i've choosen shows up at desktop and the software partition shows up also 

but thats all happend once i double click the partition from computer menu

i tried the fstab think but didn't work and it disappear from the computer menu i can't find it there 

i think ubuntu using some mounting script when i double click on it to appear on desktop 

any idea ?

---

### Post by tom4everitt on 2010-09-04
The thing that decides whether a mounted partition shows up on the desktop is whether it is mounted in /media or not.

For example:
[LIST]
[*] If I mount /dev/sda3 to /mnt, it will not show up on the desktop. 
[*] But if I mount /dev/sda3 to /media/some_folder it will show on the desktop. 
[/LIST]


So what you have to do is to create some folders in /media (some_folder in my case) and then tell fstab to mount them on these folders. 

So there is actually no script involved, it's just whether it is mounted in /media or not.

---

### Post by rebrov on 2010-09-04
> **tom4everitt said:**
> The thing that decides whether a mounted partition shows up on the desktop is whether it is mounted in /media or not.

For example:
[LIST]
[*] If I mount /dev/sda3 to /mnt, it will not show up on the desktop. 
[*] But if I mount /dev/sda3 to /media/some_folder it will show on the desktop. 
[/LIST]


So what you have to do is to create some folders in /media (some_folder in my case) and then tell fstab to mount them on these folders. 

So there is actually no script involved, it's just whether it is mounted in /media or not.


ya i forgot to reply i tried that and it worked :) thanks 

just put at the fstab this commands

/dev/sda3 /media/Software ntfs-3g

and create directory with the name 

mkdir /media/Software 

and thats it :) 

SOLVED

---

### Post by tom4everitt on 2010-09-05
Excellent

---

