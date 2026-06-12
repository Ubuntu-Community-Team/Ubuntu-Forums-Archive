---
title: "linux mint-cannot delete files because can't change permissions options"
date: 2009-04-11
forum: General Help
---

### Post by irish66 on 2009-04-11
Hi, I'm trying to delete some files, but cannot because in properties/permissions, I can't change the group acess, or others acess. They both stay at "none"
The owner is listed as martin (martin) with read and write acess.
M

---

### Post by SuperSonic4 on 2009-04-11
You can always use sudo rm /path/to/file to delete the files but you should be very careful as it can break your system

---

### Post by irish66 on 2009-04-12
Hi,Thanks for the tip. I think I'll leave that option alone.
Anyway I better start at the beginning, because as the song says
"let's start at the very beginning, a very good place to start"
I'm running multi boot linux mint/windows xp, with Mint being the one I use more or less all the time.
I decided to install the file sharing program filetopia. It's a windows program, but can run through wine. But it wouldn't connect. When i tried closing it, it froze the computer. I waited, still no response. I hit the reset button. The computer rebooted, but stopped at the black screen. I waited, nothing, turned off the computer, turned on the computer, same result. I stuck kubuntu disc into dvd drive, rebooted computer, chose option to boot from hard drive. Everything went fine, and I could go into linux mint.
All was right for a while, and then lock icon appeared beside one of my external hard drives. Ooops, i should say, that I have a number of external HDS. I switched off computer
I posted to Ubuntu forum. I went to bed.
I got up early thinking that maybe the problem was with the external hard drive. Now as I didn't know which hard drive was which, I pulled all their connections, and decided to reconnect them one by one. The second one connected was the one giving the problem.
So far anyhow, the problem does not seem to have reappeared.
m

---

### Post by hatalar205 on 2009-04-12
First press "ALT+F2" and then write "gksu nautilus". Then you can delete whatever you want. But be carefull the thing you delete.
I think this will solve your problem.

---

### Post by irish66 on 2009-04-12
Well the problem did come back.
Thank you hatalar205 for your suggestion. Unfortunately it didn't work.
Now I'm using Thunar instead of Nautilus, because Nautilus kept crashing and reappearing on me. But I'll try anything. So next I'm gonna try a different file manager. It probably won't make a blind bit of difference, but heck, ye gotta try.
M

---

### Post by irish66 on 2009-04-12
Well, well. That seems to have done the trick. Now something else occurred to me. I may have deleted some system file from that external hard drive. I guess I was just wondering what a system file would be doing on an external hard drive.
M

---

### Post by irish66 on 2009-04-12
So I decided to shut down and reboot without using kubuntu as startup disc Everything went fine. So I guess the question is did I do something I shouldn't have, or did Thunar decide to be naughty of it's own accord. Anyway I'll stick to Nautilus at least until it starts acting up again, and I get tired of it. 
M

---

### Post by irish66 on 2009-04-12
Okay. so i went out leaving computer on,came back and computer was knocked off. I rebooted, and after a short while. I got the same problem. I dunno. I'm a a loss.

---

### Post by hatalar205 on 2009-04-12
Then please **ALT+F2** and write "**gksu thunar**". This will solve. I also used these with thunar. When you this you will get superuser priviliges in file manager and you can do whatever you want. It is very simple.

---

### Post by irish66 on 2009-04-12
Thanks again, and once I'll repeat what I said before. Alt f2 does nothing on my keyboard. I presume it's supposed to open up the terminal?
Okay going on that assumption, i opened up terminal, and typed "gksu nautilus" since I have gone back to nautilus.
here is terminal output
 gksu nautilus
Initializing nautilus-share extension
Initializing nautilus-open-terminal extension

** (nautilus:15562): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSInit evolution plugin
Init thunderbird plugin
Init pidgin plugin
Init sylpheed-claws plugin

Anyway it didn't work. I still can't delete files from that hard drive. I'm gonna remove the drive, and put another one in it's place, and see what happens.

---

