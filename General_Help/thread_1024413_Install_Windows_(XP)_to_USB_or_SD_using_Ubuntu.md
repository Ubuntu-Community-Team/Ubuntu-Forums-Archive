---
title: "Install Windows (XP) to USB or SD using Ubuntu"
date: 2008-12-29
forum: General Help
---

### Post by Hobbes on 2008-12-29
I am running Ubuntu on an eeepc and I was wondering if there is a way to get from a windows .iso file to a bootable usb or sd card, using only Ubuntu.

I have seen this question asked a few different ways before, but after searching the forums, google, and eeeuser.com for a good while, I have yet to see a solution that does not involve using another computer that has windows installed.

Is this just not possible because nobody wants to encourage the switch to Windows :) ?

---

### Post by methid122 on 2008-12-29
i have 0 experience with linux, but what i did...just today. is i bought a external hd. and installed ubuntu on it. and my internal hd has vista. so i have 1 hd for games and 1 hd for linux. this way works very well because to change the hd all you need to do is enter the bios and pick wich one to load. very simple.

---

### Post by logos34 on 2008-12-29
here try this

[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

let us know how it goes

---

### Post by Hobbes on 2008-12-29
Yeah, maybe I wasn't clear enough on my first post.

1.) I don't have a cd-rom drive
2.) I am running Ubuntu, and have no Windows available
3.) I just want to make a bootable usb or sd card to install Windows ***from*** not actually install it there and use it from there.

(the first reply has to do with installing it to an external harddrive, which isn't really what I want (and which I also couldn't do), the second requires an existing Windows install, which is exactly what I don't have :) )

Thanks for trying to help! but unfortunately the question remains open :(

Cheers

---

### Post by Hobbes on 2009-01-02
*bump*

Is this really not possible?

---

### Post by krepperk on 2010-03-12
*bump*
Have the same question, been searching for hours without getting a solution...

---

### Post by Mark Phelps on 2010-03-13
> **krepperk said:**
> *bump*
Have the same question, been searching for hours without getting a solution...

Maybe that's because ... it's simply not possible using the Ubuntu USB creation app.

---

### Post by jastonas on 2010-05-04
Still nothing new on this?

---

### Post by jetsam on 2010-05-04
Here's an inefficient but interesting workaround that I think might work:
Make a bootable Ubuntu usb stick, then put a virtual machine on it, and in the vm put Windows whatever...  Then script the startup to autostart Windows and use script magic to give it an entertaining intro...

Watch Ubuntu fly by as you inevitably suffer the fate of working in Windows ME... that sorta thing.

Just an idea...

---

### Post by spydeyrch on 2010-05-04
> **jetsam said:**
> Here's an inefficient but interesting workaround that I think might work:
Make a bootable Ubuntu usb stick, then put a virtual machine on it, and in the vm put Windows whatever...  Then script the startup to autostart Windows and use script magic to give it an entertaining intro...

Watch Ubuntu fly by as you inevitably suffer the fate of working in Windows ME... that sorta thing.

Just an idea...

I don't think that this is what the OP is looking to do.

If I understand the OP correctly, you want to have a usb flash drive carry all the files necessary to install windows to a HDD from that usb flash drive.

Much in the same way that one can make a live usb installer for ubuntu but instead of ubuntu, you want to have windows there. This would allow you to carry the USB flash drive with you where ever you went and be able to install windows with it.

Is that right?

I know that there is a usb installer for windows 7 on the windows 7 website. It allows you to take an already existing .iso of windows 7 and "burn"/convert it to the usb flash drive to use to install windows 7 to, for example, a netbook, which don't have cd/dvd drives.

I don't know if this is what you are looking for but it might help. I also don't know if it will work for Vista or XP in place of Win7.

-Spydey:lolflag:

---

### Post by alh on 2010-05-04
Excuse me but I don't understand why you would want windows on a usb key. I have karmic on a usb key...... but hey it's usfull. I have saved friends windows boxes and their data. If you need to run windows like I unfortunately do as e-tax is not ported to linux, install windows in a virtual machine within linux. I have xp running in virtualbox and it runs very well.
Hope this helps.
 
> **jastonas said:**
> Still nothing new on this?

---

### Post by jastonas on 2010-05-04
well... i dont want a live xp usb. I want to have a usb to use on friends laptops so i can install both xp and ubuntu without the need of a cd. It took more than half an hour to install xp to a new laptop from cd whereas ubuntu would take 10-12 minutes from usb...

---

### Post by jetsam on 2010-05-04
Oh... I don't know the details, but there are ways to do stuff like that I know.  You need Windows savvy admin help...  

There's other forums that would get you the answer quicker.  Next step for me would be a google search using:
```
 "site:slashdot.org windows rollup service patch"
```
...but if you know of a good Windows forum, you might get a better response by asking there.

---

