---
title: "How much HDD space does Ubuntu need for installation"
date: 2005-12-20
forum: Desktop Environments
---

### Post by LoclynGrey on 2005-12-20
I just happened to have a old IBM laptop lying around that I thought I'd install Unbuntu 5.10 on.
During installation of ubuntu it told me I had run out of room to install packages. It seems that there was enough room to install the base system.

I'm sure (and didint bother to check beforehand) that this old ugly IBM laptop have 2.5 or 3GB hard drive. Which I assumed would be ample room.

Does any one know how much room a standard installation with I guess the standard packages takes?

Edit: yes i instructed the ubuntu installer to erase the whole disk first. (which brutally and with extreme prejudice  killed the existing MS windows 2000 installation - applause all round please!)

---

### Post by linbetwin on 2005-12-20
I think Ubuntu needs approximately 3 GB of hdd space, but you can install it as server and then install only the applications you need (from the internet or even from the CD).

---

### Post by UseTheForce on 2005-12-20
On the case that I have here, it states 1.8 GB are needed.

---

### Post by az on 2005-12-20
[QUOTE=UseTheForce]On the case that I have here, it states 1.8 GB are needed.[/QUOTE]


You need more than that.  1.8 gigs is what you end up with.  About 300 megs of packages are cached onto your hard drive for installation, of which about 150 megs are cleaned just before you get to the graphical login.

Add to that the filesystem data and reserved blocks.

Heap on top of that the swap.

You need something line 2.2 gigs (maybe more, depending on your ram and so forth)

You can always install with the bootprompt

linux archive-copier/copy=false
and it wil not cache the 300-or-so megs of packages onto your disk.  It will go slower and ask you for your cd during the second satge of the install...

---

### Post by LoclynGrey on 2005-12-20
> linux archive-copier/copy=false
You know, when i have as many posts as you (4525) I would know to do linux archive-copier/copy=false off the top of my head. :)
lol
Cheers mate, it's going through the install process now.

---

### Post by towsonu2003 on 2005-12-20
Here is my ubuntu partition:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              20G  2.7G   17G  14% /

```
+ 
2GB swap + 1GB RAM which is pretty stupid of me... I usually have 150 - 350MB RAM used (firefox+gaim+liferea).

PS. Xubuntu would run beter on an old laptop.

---

### Post by LoclynGrey on 2005-12-21
**Update:**

The hard disk drive size is 3.3GB and thats not enough even with not caching packages over.
Hmmmm wot to do wot to do lol.
Could be back to win2K on this puppy, besides its only a spare unused laptop. (one that I was going to just leave lyinga round in the lounge)
Must of been a grunter in its day, p133 something I'm guessing a 200Mhz hell not really sure but man is it a uguly bulky begger. Has 80mb of ram lol. IBM 380D beast of burdan.
The best thing about it is the dlink AirPlusG wireless network card i put in it. (actually the card is worth more than the laptop)

---

### Post by Luffield on 2005-12-25
[QUOTE=LoclynGrey]The hard disk drive size is 3.3GB and thats not enough even with not caching packages over.[/QUOTE]
That's strange - I installed Ubuntu 5.10 on a 3gb drive (normal installation, I didn't know that trick before) and it works. It's a bit slow, but seems to work fine otherwise.
I have half a giga of RAM, maybe that's the difference.

---

### Post by kaamos on 2005-12-25
I installed ubuntu on this:
> /dev/hdb1             1,9G
/dev/hda1             625M
Swap:          549M

So hda is about 1,1 G and hdb 1.9G. Works fine with a server install + xubuntu desktop.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-25
> The hard disk drive size is 3.3GB and thats not enough even with not caching packages over.

You got other problems there. Are you sure it's not doing something stupid like making a 1GB swap or something? I have installed ubuntu on a thinkpad 600 with a 2GB hard drive so I know it'll fit.

I bet it's your ram. 80MB? You probably couldn't boot even gnome 2.10 - even if it installed. Install a server then apt-get xfce or blackbox. I've run blackbox on a 200mhz pentium with 64MB ram and it worked.

---

### Post by LoclynGrey on 2006-01-07
Hi all, thanks for your replies/questions.
Yes I think it was the ram, 80MB just doesnt cut it.
Even damn small linux said "NO way" although I think with DSL it was more a video issue. 
Shame, only windows installs on it, I've put it back on the shelf for now but later on if get bored again and decide that I want a super nova Virus gateway I might install windows again on it. lol
(ok I know how to put a firewall and virus checker on windows..don't we all)

---

### Post by LoclynGrey on 2006-04-17
Final update.
I put the laptop aside for a month or so, moved house then brought it out so my 20 month old daughter could be like me when I was using my main laptop in the lounge. (Which she did do and it was quite cute)

Anyhow, I decided to put Edubuntu on it. It didnt go so well but in the end after (not caching and just installing off the cd) it went on.
Now she can really be like dad and learn at the same time. :)
(ps: its slow)

---

