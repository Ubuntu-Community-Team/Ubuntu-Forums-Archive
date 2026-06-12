---
title: "WoW HELP!"
date: 2006-07-16
forum: Gaming &amp; Leisure
---

### Post by jkatana on 2006-07-16
ok, i got WoW installed by copying all the cd files to the hardrive then running setup... my wine is 9.17 and im on 6.06 ubuntu.. i altered the configurations like i was told and updated my drivers and now i have two problems.. i installed the drivers for Nvidia when i didnt install the drivers for my on board video.. i got the drivers on a CD and it just so happens they are linux format.. how do erase the nvidia drivers, install the right ones, i had wow working 2-3 fps when it should be higher with 128 vid and 736 ram.. so i need to install the right drivers, heres the link to the driver [ftp://dlsvr01.asus.com/pub/ASUS/mb/socka/sis741GX/Linux.zip](ftp://dlsvr01.asus.com/pub/ASUS/mb/socka/sis741GX/Linux.zip) , a mini map fix, and what is up with the mouse thing? if i can fix this much i will be eternaly greatful

heres my crash i get when booting WoW

[IMG]http://i110.photobucket.com/albums/n95/jkatana/Screenshot-2.png[/IMG]

---

### Post by eqisow on 2006-07-16
Try [this script]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html") to install the newest nvidia drivers from the nvidia site. The only caveat is that it will remove your restricted modules package, which is not a good idea if you are using a wireless card.

Edit: The instructions on that site are kind of jarbled. Here is what you'll need to do:
[B]
Warning: Read entire instruction set before you begin![/B]
```

wget http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_8762_32
sudo sh envy_8762_32
```
That second command will drop you out of X and into a terminal. Run the second command again, and follow the instructions.
```

sudo sh envy_8762_32
```
Reboot the system with
```
sudo reboot
```

---

### Post by jkatana on 2006-07-16
Thanks Alot Dickweed Now I Cant Get Into My Gui Motherfucker! I Need To Know How Do I Rescue My Drake Due To A Dumbass Giving Me The Wrong ******* Driver!!!

---

### Post by Cure777 on 2006-07-16
> **jkatana said:**
> Thanks Alot Dickweed Now I Cant Get Into My Gui Motherfucker! I Need To Know How Do I Rescue My Drake Due To A Dumbass Giving Me The Wrong ******* Driver!!!
Lmao. You need to calm down, and approach this from a better perspective...

---

### Post by eqisow on 2006-07-16
jkatana, it would seem (and this is simply a guess) that you had a slight issue installing the drivers using the method I showed you. I assure you, however, that I did not give you the wrong driver. If I did, then you gave me the wrong information.

If you'd like to calm down and approach this issue in a respectful manner, I may help you. However, I probably won't. But, who knows, maybe somebody here is nicer than me and doesn't mind helping people who are so blatantly crude and disrespectful.

P.S. - I don't appreciate the IM's you sent while I was at work either.

Edit: It seems I did, in fact, link you to the wrong drivers. Try using proper punctuation and sentence structure next time, and perhaps somebody will be able to decipher your post. Also, if you had bothered to read the link I posted before you started running scripts from random strangers, you would have seen that the script was for the latest Nvidia drivers and was not what you needed.

---

