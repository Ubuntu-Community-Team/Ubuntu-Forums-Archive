---
title: "help with resizing partition"
date: 2005-12-23
forum: General Help
---

### Post by ubuntu27 on 2005-12-23
Hi guys&Girls! :) I've been trying to Resize my partition using Gparted and QTparted in Ubuntu LIVE CD but, it keep telling me that my Windows XP partition (NTFS) is busy or active. 

If I check if it is mounted or not, it tellme that it is NOT mounted. 
I don't know what to do, any ideas?

Oh! ANd many plp recommended me KNoppix Live CD [because it is more compatible with NTFS??] and use it's partition app, I found that in Knoppix use QTparted.. well, I tryed it and it tells me the same thing, that My NTFS partition is "Active"

What I want to do is to **Give more** space to my Ubuntu Partition.
My current HD space:
30 GB of free space in WIndows.
1 GB of Free space in Ubuntu.

Any ideas?

Thank you, thank you guys :)

---

### Post by ubuntu27 on 2005-12-23
Need your help guys. Anybody has some idea, tips, something ?

---

### Post by weltall on 2005-12-23
Are you running partition programs on windows xp?  If so, try to partition using a windows partitioning program like partition magic instead.

---

### Post by ubuntu27 on 2005-12-23
[QUOTE=weltall]Are you running partition programs on windows xp?  If so, try to partition using a windows partitioning program like partition magic instead.[/QUOTE]

Yeah, I have Partition magick 8 in my WIndows partition. But i've read that it is better to modify the partition running from the Live CD...

Well, I think I will wait for mroe response...

Should I use Partition Magick ?

---

### Post by az on 2005-12-23
If you already have a linux installation, the live cd may be use a swap space you have.  That would make your drive "busy"

swapoff -a

The Ubuntu installer does not have any trouble resizing NTFS and it does not mount swap partitions automatically.  I think you should use that.

---

### Post by rcerreto on 2005-12-23
Far from being sure.
If I remember right, windows set its boot partition as 'active'.
It seems that (g)parted is not able to resize an active partition (just guessing).

You could try:
1) boot from a live CD
2) using fdisk clear the windows partition boot flag
3) run gparted to resize partitions, hopefully it could work now
4) remember to set the windows partition boot flag, otherwise I suppose that windows won't boot

---

### Post by ubuntu27 on 2005-12-23
guys! What a idiot I am... I killed WIndows !!

I was so desesperate that I used partition magick 8... and resized...
It told me to restart, so I did...
then, Windows or PMagick started to scan the disk... and resize the partition...

and, well, it told me to hit any keys to reboot.. 
so Ihit Enter... and noticed that in the screen reported some error, which couldnt see...

Now... whatever option I choose... Windows cannot run anymore, not even in the safe mode...

[IMG]http://img255.imageshack.us/img255/7461/gparted2qy.png[/IMG]

Look at Gparted (See screenshot) it seems that when I resized the NTFS partition... it deleted many files... 
Gparted shows that I have 89,629 of FREE space ?? 

NOw what should I do? I never been so deep in trouble before... :(

---

### Post by rcerreto on 2005-12-23
Ouch!!

There are several restore utilities available but I'm afraid they are not free.
On [www.r-tt.com](www.r-tt.com) you could find some useful products.
You can download an evaluation copy to see whether it can help you.
Then you'll decide whether it's worth to shell out some money for it.

---

### Post by az on 2005-12-23
[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

I used this to recover deleted photos from a digital camera.  I do not know if it does NTFS.  It is free and runs in linux.


Edit:  I forgot,  Good luck and don't panic.

Also, in situations like this, I like to assume that I am totaly screwed so that I am not dissapointed with the final outcome.

---

### Post by rcerreto on 2005-12-23
[QUOTE=azz][http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

I used this to recover deleted photos from a digital camera.  I do not know if it does NTFS.  It is free and runs in linux.[/QUOTE]

Good to know!! :)

---

### Post by briancurtin on 2005-12-23
[QUOTE=ubuntu27]Windows cannot run anymore, not even in the safe mode...

I never been so deep in trouble before... :([/QUOTE]
maybe its just me, but i consider what you did a victory

---

### Post by ubuntu27 on 2005-12-23
[QUOTE=briancurtin]maybe its just me, but i consider what you did a victory[/QUOTE]

Ha ha ha. :D

************************888

Gues what happend now?

I "Recovered" Windows... but this ^*&(^*( WIndows ignored the partitions, and formatted the whole disk... deleting ALL OF MY FILES!!! Byebye my personal files... byebye my work's file... byebye Ubuntu....  

I cannot beleive, I've just reinstalled Windows, and in 5 minutes I already have more than 20 malwares !! 

And to let it make worse...

I've receive a phone from my job...
and told to make many copies (Print) some docments...
well.. I told them that it was "deleted" thanks to WIndows...
they are mad at me now... 

BTY, I get this weird thing:

[[IMG]http://img387.imageshack.us/img387/2268/errorservice9vx.jpg[/IMG]](http://imageshack.us)

I suppose that it is some Virus? 
Surely... Windows is a nightmare
I feel like my worls is upside down now... 

well...
haha...

I got to start over again...

---

### Post by newuser111 on 2005-12-23
that is not a legitimate windows system message, notice it says "messenger service" in the title, it is messenger spam (not MSN messenger, but the messenger service designed for popup network messages), which allows spammers on the internet to send messages due to a vulnerability, either patch it with the patch released by microsoft a few years back or disable with the tool from grc.com, its not needed at all anyway

---

### Post by ubuntu27 on 2005-12-23
newuser111, thank you for the reply.
Ok, I've desable the messenger service and the error reporting service using the Service tool that comes with Win Xp :)

---

### Post by briancurtin on 2005-12-23
[QUOTE=ubuntu27]I cannot beleive, I've just reinstalled Windows, and in 5 minutes I already have more than 20 malwares !![/QUOTE]
there was a story on slashdot that on average, it takes something like 12 minutes of being unprotected (firewall/antvirus) after installation of MS windows for someone else to own your windows box.

---

### Post by ubuntu27 on 2005-12-23
[QUOTE=briancurtin]there was a story on slashdot that on average, it takes something like 12 minutes of being unprotected (firewall/antvirus) after installation of MS windows for someone else to own your windows box.[/QUOTE]
Yeah, I've read it before...
...Wonder how do they do that ><

---

### Post by az on 2005-12-23
[QUOTE=ubuntu27]

I got to start over again...[/QUOTE]



WAIT!!!!!!!!!!!!!!!



Use parted to recover the NTFS partition if it was repartitioned.  The, use foremost to recover the files that are still recoverable.

DO not boot into windows as that will eat away at files that are potentialy salavageable.

---

### Post by ubuntu27 on 2005-12-23
[QUOTE=azz]WAIT!!!!!!!!!!!!!!!



Use parted to recover the NTFS partition if it was repartitioned.  The, use foremost to recover the files that are still recoverable.

DO not boot into windows as that will eat away at files that are potentialy salavageable.[/QUOTE]
Thank you. But it's too late now. The Compaq System Restore Re-Formatted the Whole HD.
I am typing this in Windows ><

I think...
I will look for info on how to set a different partition for my Home directory.
And see it it is convenient or not.

---

### Post by az on 2005-12-23
[QUOTE=ubuntu27]Thank you. But it's too late now. The Compaq System Restore Re-Formatted the Whole HD.
I am typing this in Windows ><

I think...
I will look for info on how to set a different partition for my Home directory.
And see it it is convenient or not.[/QUOTE]
Even if it reformatted, there may be data that is recoverable...

---

