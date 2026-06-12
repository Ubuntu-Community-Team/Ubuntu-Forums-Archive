---
title: "wallpaper not static !!"
date: 2010-09-03
forum: Desktop Environments
---

### Post by rebrov on 2010-09-03
i downloaded some wallpapers and put them all in my software partition and choosen one to be my wallpaper and it worked fine but ...when i make restart the old wallpaper of ubuntu show up again and the wallpapers that i just added them to my desktop wallpaper manager its not there and here we go again 

when i add them again and choose one to by my wallpaper it will be fine and once restart old paper shows again !! 

any idea ?

---

### Post by simonmoon42 on 2010-09-04
> **rebrov said:**
> i downloaded some wallpapers and put them all in my software partition and choosen one to be my wallpaper and it worked fine but ...when i make restart the old wallpaper of ubuntu show up again and the wallpapers that i just added them to my desktop wallpaper manager its not there and here we go again 

when i add them again and choose one to by my wallpaper it will be fine and once restart old paper shows again !! 

any idea ?

I would guess the partition isn't being mounted on bootup or is being mounted after the wallpaper is loaded. Try putting the new wallpaper on the system partition.

---

### Post by Silent Warrior on 2010-09-04
What's the exact path to the wallpapers you want to use? When you change the wallpaper, do you click 'Apply' or just exit? (Just checking.)

---

### Post by rebrov on 2010-09-04
> **Silent Warrior said:**
> What's the exact path to the wallpapers you want to use? When you change the wallpaper, do you click 'Apply' or just exit? (Just checking.)

ooh i think u right because my software partition that contains the images not mounted during boot

and yes i click Apply but when i reboot i think i have to mount the partition again thats why it will choose the static wallpaper fromt he root partition because its already mounted :) 


thanks alot for Enlighting me :)

---

### Post by rebrov on 2010-09-04
SOLVED with mounting the Software partition that contain the pics with adding this command in /etc/fstab

/dev/sda3 /media/Software ntfs-3g

then making directory to the same destination

mkdir /media/Software

thats it thanks

---

