---
title: "boot problems"
date: 2006-03-20
forum: Desktop Environments
---

### Post by iowanscott on 2006-03-20
when going through the initial loading screen my computer freezes at the system log deamon. i have been using ubuntu for a while and i have stuff on there i dont want to lose so i dont really want to re-install. what i dont understand is the only thing i did the last time i was able to boot it was copy a cd. :confused:   any suggestions would be greatly appriciated.

---

### Post by rjwood on 2006-03-20
You do not need to reinstall.. Please try to give a more detailed description of what the screen looks like and what is happening...

---

### Post by jerrykenny on 2006-03-20
I had the same problem when I foolishly had been tinkering with my default runlevels . . . 

Have you been using the Boot-Up-Manager, or some other script editing method to speed up your boot procedure, and maybe disabled some vital servives ?

You can always boot into the rescue mode, and undo this, or use the install cd in rescue mode . . . just boot into the install cd and type "rescue" at the boot prompt . . . at least you can maybe back up your data this way . . .

---

### Post by iowanscott on 2006-03-20
yes i was fairly certain i wouldn't need to although it may be faster. but when i choose to start ubuntu. the initial screen where it goes through and loads all of the components and sets the clock and stuff. when it gets to the loading system log deamon it freezes.

---

### Post by iowanscott on 2006-03-20
no i havent been trying that yet. like i had said the last time i ran it i only ripped one of my cds and then ended up turning the computer off then when i tried to boot the next day i had this problem.

---

### Post by rjwood on 2006-03-20
what did you use to copy your cd?  Do you get any errors or anything? try restarting and boot into another kernel if you have one on your machine.. or boot into safe mode

---

### Post by iowanscott on 2006-03-20
i used the cd ripper that was already installed i dont remember the name offhand . but i didnt have any errors and i tried booting into previous kernels and safe mode both and i still lock up at the same point.

---

### Post by rjwood on 2006-03-20
try ctrl+alt+backspace---if nothing try ctrl+alt+f4

---

### Post by iowanscott on 2006-03-20
i have a dual boot with xp on both my laptop and desktop. ive had problems before with xp trying to overwrite grub and things i wonder if possibly that is the cause of my problems?

---

### Post by jerrykenny on 2006-03-20
Can you boot into "rescue mode" ?  as soon as the pc leaves the bios stuff, press "escape" and you'll see the hidden grub-bootloading-menu.

The second option (usually) is rescue mode.

Boot into this, and you might be able to execute certain tasks, like sudo apt-get update,  sudo apt-get dist-upgrade . . . .

just saw the above posts, never mind . . . . can you look at the post on optimising breezey? theres a post on speeding up the boot process (so you can notive it or something like that . . . )

Maybe try following that procedure (using the rescue facility on the install cd)  just to make sure the boot up scripts are all at default

---

### Post by rjwood on 2006-03-20
ok---I don't know about dual booting...sorry... search forums for 'dual booting'.

---

### Post by Ramses de Norre on 2006-03-20
Overwritting grub doesn't change anything but the mbr, which is fine again since you're able to use grub. So this probably isn't the cause of your problem.

---

### Post by jerrykenny on 2006-03-20
Do you have separate partitons for /var or /tmp ?   maybe the last ripping operation has left an image on here and left no free space on the partition ?

---

### Post by iowanscott on 2006-03-20
eh its a 90GB partition for ubuntu and i only have 2 cd's and like 4 applications. i just dont wanna lose my webpage and all the images for it. its a lot of work to redo..

---

### Post by iowanscott on 2006-03-20
all i know is all the problems stem from not being able to load the " SYSTEM LOG DEAMON"

---

### Post by rjwood on 2006-03-20
try CTRL+C   when it hangs

---

### Post by iowanscott on 2006-03-20
i got it fixed. i got the data i needed and re-installed. i also found out that i had installed a couple updates the last time i had used it and i think maybe that was my problem.

---

