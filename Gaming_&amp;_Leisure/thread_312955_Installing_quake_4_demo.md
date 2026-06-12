---
title: "Installing quake 4 demo"
date: 2006-12-05
forum: Gaming &amp; Leisure
---

### Post by rajeev1204 on 2006-12-05
hi

i just wanted to share my knowledge on how i got to install quake 4 demo on my pc cos its a popular game.

so here goes....

first step is to install as sudo so u have permission to write to the usr/local/games folder where it installs by defualt.

u can also try ur home directories if u want to skip permissions and stuff

after install is ok , u will run it as instructed 

most probably u will face a sound problem- like someone playing a badly tuned guitar . so next time when u run the game type at terminal

"sudo quake4-demo +set s_driver oss" .this will solve the sound issue. 

running as sudo is important or u wont be able to save changes u made in the game.cos the save files need right prmissions. u wont have this problem if u save it to ur home directory so u can also run without sudo.


i hope this can be of some help

regards
rajeev

P.S this is just  a simple post to solve a few simple problems when installing the DEMO.

---

### Post by pay on 2006-12-05
instead of running it as root, I recommend that you change the permisions of the folder. ie```
sudo chmod 775 /path/to/quake4-demo
```

---

### Post by rajeev1204 on 2006-12-05
hi

yes i did read that here . iam new to linux so not familiar with a lot of things

thanks a lot for the reply . i will remember that

also, could u tell me what that command does?


regards

rajeev

---

### Post by amo-ej1 on 2006-12-05
man chmod will teach you that changes the permissions so an other user than the owner (which is probably root) can read and execute the file

---

### Post by pay on 2006-12-05
chmod changes the permision. read (r)= 4 write (w)= 2 execute (x)=1. The first number is for the owner, the second number is for the group and the thrid number is for other users. 775 means rwx (4+2+1) for the owner and group and rx (4+1) for other users. Alternatively you can use chmod rwxrwxr-x /path/to/quake

---

### Post by pay on 2006-12-05
Also if you have multiple users wanting to play that game then you can try (I think) ```
sudo chown -R <your_username>:games /path/to/quake4
sudo gpasswd -a <their_username> games
```that should make you the owner of the quake4 folder and the quake4 folder part of the "games" group and the second command would add a user to the games group.

---

### Post by rajeev1204 on 2006-12-05
thank u man

what should i "pay" u!?:-D

---

### Post by pay on 2006-12-05
I accept money:)

---

### Post by aBitLater on 2008-01-17
thanks for the tip about the sound

anyone know how to make the kernel a low latency kernel, as suggested by the readme?

> 
You need a low latency kernel for optimal performance (this applies to both client and server installations). Make sure your kernel is configured with CONFIG_HZ_1000=y. You should also enable other low latency settings, such as the various preemption settings


and what are the ramifications for the rest of my system if I change the latency of the kernel for this game.

The demo runs ok on my computer, but the graphics are choppy.  (ATI Radeon 9700 Pro with 128 MB video ram), Ubuntu 7.10, 1GB RAM

Thanks,
Brian

EDIT: I also saw this in the terminal after quitting the game:

Shutting down SDL subsystem
idRenderSystem::Shutdown()
********************************************
*      BITDEMON MEMORY LEAKS DETECTED      *
********************************************
48 Bytes leaked in 2 allocation(s)
********************************************
shutdown terminal support

---

### Post by IamOdysseus on 2008-01-17
Hi, I have installed Quake 4 Multiplayer Demo and works. But when I leave I don't know how to open it again (I don't have an acces to go there with destkop or menu).

Thanks.

---

### Post by IamOdysseus on 2008-01-18
I have fixed it, I found the folder.

---

