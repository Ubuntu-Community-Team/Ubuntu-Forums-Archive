---
title: "gnomebaker problems"
date: 2006-01-11
forum: General Help
---

### Post by lungdart on 2006-01-11
I have some iso's that need burning, So I turned to gnomebaker, as I'm using gnome for my enviroment. It works, my lord its slow! I have a 16x dual layer dvd+- burner, and the isos are burning between .7x and 1.2x (shows the percentage each step in the verbose area) the speed choice ranges from 1-100, as this is in development, i originally thought that it cant auto detect my speed so i went speed 6x as its good imbetween speed. Got about 1x. So i thought maybe it was a percentage, so i put it at 100% for good measure but alas, same problem. Is there maybe a driver issue?

I really do not want to use k3b as I dislike the KDE look to things, and If i can get this working right, it would be better. Any help? :confused:

---

### Post by StefanoCole on 2006-01-11
Well, in your post you did not mention if you have enabled the DMA on your burner, so, just in case I ask for ....
Second maybe trivial question: is your burner internal or an external USB burner? In the second case be sure you have connected it to a USB 2.0
Third, if you give your general PC specifications (cpu, memory, etc.) could be useful.

Stefano

---

### Post by lungdart on 2006-01-11
I do not have DMA enabled on my burner, but I am backing up xbox games and using xiso files I have created myself from extract-xiso for linux. I do not believe the DMA would be a problem there. The burner is internal, and alas I do not have a usb 2.0 port, so no externals for me anytime soon.

I have a 256mg chip and a 512 chip of DDR ram CPU I have no idea, but im pretty sure it's intel around the 1.2ghz range. This is a second hand computer and I never bothered with the specs since it was given to me for free.

MY burner is LG but I can't see a serial number on it at all. I know theres some command that shows me all my hardware from the command line, but I forget it. If someone wants to refresh my memory i'd be happy to give the output.

EDIT: Gnomebaker gives this as my dvd burner choice:

```

 HL-DT-ST DVDRAM GSA-4167B

```

---

### Post by lungdart on 2006-01-11
bump

---

### Post by bb002 on 2006-01-11
Not having DMA enabled on you burner is most likely the problem. Burning DVD without DMA will result in slow burns (if it works at all). PIO mode is sloooow (it is the method that existed before DMA).


All of my devices have been DMA enabled from the start so I don't know how to enable it.

---

### Post by StefanoCole on 2006-01-12
I agree with bb002, you should try burning with DMA enabled. Check the following link: [https://wiki.ubuntu.com/DMA]("https://wiki.ubuntu.com/DMA") 

Stefano

---

