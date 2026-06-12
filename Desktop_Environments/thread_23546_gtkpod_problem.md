---
title: "gtkpod problem"
date: 2005-04-02
forum: Desktop Environments
---

### Post by Muchacho_Gasolino on 2005-04-02
well, i just finally got sound juicer to rip mp3's, but now for some reason gtkpod won't write to my ipod.

i get this message
Could not open file "/media/MAX'S IPOD/iPod_Control/Music/F01/gtkpod00817.mp3" for writing.
Could not open file "/media/MAX'S IPOD/iPod_Control/Music/F02/gtkpod00818.mp3" for writing.
Could not open file "/media/MAX'S IPOD/iPod_Control/Music/F03/gtkpod00819.mp3" for writing.
Could not open file "/media/MAX'S IPOD/iPod_Control/Music/F04/gtkpod00820.mp3" for writing.
Could not open file "/media/MAX'S IPOD/iPod_Control/Music/F05/gtkpod00821.mp3" for writing.
Could not open file "/media/MAX'S IPOD/iPod_Control/Music/F06/gtkpod00822.mp3" for writing.

with the 6 songs i am trying to put on it

what i think might be the problem is that it is mounted read-only, because when i go to change the permissions on the ipod(they are set correctly, I was just experimenting), it says i cant, because it is a read-only drive
i looked in my fstab and there is nothing listed there besides my HDD partitions, my CD drive and my floppy
does anyone know how to make it writeable?

---

### Post by Muchacho_Gasolino on 2005-04-04
well i successfully changed the permissions for /dev/sdc, sdc1, and sdc2, which i noticed were created when the ipod was plugged in, but i still cant change the permissions on the actual ipod folder. It doesn't give me the message about it being a readonly drive anymore, it just changes it right back whenever i try to change the permissions
this may have nothing to do with the read-only status but im just messing around with it because it was what gave me that error message

---

### Post by aussieskin on 2005-07-17
[QUOTE=Muchacho_Gasolino]well i successfully changed the permissions for /dev/sdc, sdc1, and sdc2, which i noticed were created when the ipod was plugged in, but i still cant change the permissions on the actual ipod folder. It doesn't give me the message about it being a readonly drive anymore, it just changes it right back whenever i try to change the permissions
this may have nothing to do with the read-only status but im just messing around with it because it was what gave me that error message[/QUOTE]
 I am having the same problem. Ipod was working fine all day, have added about 600 songs, but now all of a suddne I am getting the same error as you were...gtkpod is reading fine, it just wont let me write. I tried changin the persmissions on the iPod, but ti says it is read only and I cant do nothing!

Help would be awesome...I just got a new ipod....20gig from 4gig, but I cant seem to add more music!

---

### Post by angkor on 2005-07-17
I got my ipod to work perfectly using this howto:

[http://www.linux-sxs.org/non_pc/iPod.html](http://www.linux-sxs.org/non_pc/iPod.html)

Maybe this works for you guys as well.

I mount the ipod as root and start gtkpod as root as well to be able to write to my ipod.

---

### Post by aussieskin on 2005-07-18
[QUOTE=angkor]I got my ipod to work perfectly using this howto:

[http://www.linux-sxs.org/non_pc/iPod.html](http://www.linux-sxs.org/non_pc/iPod.html)

Maybe this works for you guys as well.

I mount the ipod as root and start gtkpod as root as well to be able to write to my ipod.[/QUOTE]


Thanks for the link there.
 I had a look at the page but it didn't help much sorry.

See I can get it to mount and unmount and read the ipod no worries...
It has just decided to become 'read-only' all of a sudden... 

Can't seem to get around it..treid mounting the iPod as 'root' but its not working either. As in I cant get it to mount through the command line. I tried 'mount /media/iPod' which is where it usually mounts to when I plug it in, but it tells me that  'mount: special device /dev/sda2 does not exist'
So I don;t know, but I dont see how doing that as 'root' is going to make any difference, as it comes up when I mount the iPod normally that i actualy own it, not root....

any more ideas? I'am going nuts here....thanks

---

### Post by aussieskin on 2005-07-18
[QUOTE=aussieskin]Thanks for the link there.
 I had a look at the page but it didn't help much sorry.

See I can get it to mount and unmount and read the ipod no worries...
It has just decided to become 'read-only' all of a sudden... 

Can't seem to get around it..treid mounting the iPod as 'root' but its not working either. As in I cant get it to mount through the command line. I tried 'mount /media/iPod' which is where it usually mounts to when I plug it in, but it tells me that  'mount: special device /dev/sda2 does not exist'
So I don;t know, but I dont see how doing that as 'root' is going to make any difference, as it comes up when I mount the iPod normally that i actualy own it, not root....

any more ideas? I'am going nuts here....thanks[/QUOTE]
 Cancel that last message. It was giving me the shits so I just got onto the windows machine and restored factort settings to the ipod...luckily I still have all the mp3's on  harddrive, so it is working now anwyay...but for how long I dont know!..haha

Do you think maybe I unplugged it before it had been unmounted? Maybe thats what cause the problem...

One more question though, with unmounting. I just right click on the ipod icon on my desktop and choose 'unmount' then the little icon disappears but the ipod still says 'do not disconnect' Is that still unmounting it properly? It automatically mounts when I plug it in too, even without gtkpod open...is that okay aswell?

Sorry for the stupid questions which are probably pretty obvious, I am still reltaivly new to linux, although I am getting there!

---

### Post by angkor on 2005-07-18
To get rid of the 'do not disconnect' message type:

eject /dev/sda2

Allthough just unmounting the iPod and then disconnecting it with the blinking message shouldn't hurt it.

---

### Post by aussieskin on 2005-07-19
[QUOTE=angkor]To get rid of the 'do not disconnect' message type:

eject /dev/sda2

Allthough just unmounting the iPod and then disconnecting it with the blinking message shouldn't hurt it.[/QUOTE]
 cool...thought it would be okay to unmount then disconnect, but through I should check as I havent had much luck so far..haha

cant get the eject /dev/sda2 to work though, it says it cant find or open it..oh well doesnt matter. not that important...

thanks for your speedy reply too angkor! Its folks like you that have made sure I have stuck with linux as opposed to going back to windows! You rock

---

### Post by Jet2k5 on 2005-07-19
Sorry I'm in sort of a rush.  Seems that you are having trouble getting your iPod working Under Linux.  I don't know if anyone has recommended this link,

[https://wiki.ubuntu.com/IPodHowto?highlight=%28ipod%29](https://wiki.ubuntu.com/IPodHowto?highlight=%28ipod%29)  

It's the Wiki straight from Ubuntu.  This shows you how to get your iPod working under Linux.  Specially in Ubuntu.

---

### Post by aussieskin on 2005-07-19
[QUOTE=Jet2k5]Sorry I'm in sort of a rush.  Seems that you are having trouble getting your iPod working Under Linux.  I don't know if anyone has recommended this link,

[https://wiki.ubuntu.com/IPodHowto?highlight=%28ipod%29](https://wiki.ubuntu.com/IPodHowto?highlight=%28ipod%29)  

It's the Wiki straight from Ubuntu.  This shows you how to get your iPod working under Linux.  Specially in Ubuntu.[/QUOTE]
 yeah, thanks

I got the iPod working okay, it just desided to become read only all of a sudden. i just wiped it and restored it to factory defaults is all.

Thanks though

---

### Post by angkor on 2005-07-20
btw 'dosfsck /dev/sda2' helped me out once when my iPod got borked. It couldn't write my iTunes.Db all of a sudden but after I ran a dos check of the filesystem it worked again :)...

maybe this is useful to some googlers out there :)

---

### Post by e.c.dahls on 2005-08-13
Im new fish with ubuntu, so please help. Im having languageproblems with my gtkpod. It seems that the program is installed with swedish as the default language and I dont like that. :roll:   I want it in english.
What can I do to easily solve this problem?

---

