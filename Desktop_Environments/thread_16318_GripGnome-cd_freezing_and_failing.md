---
title: "Grip/Gnome-cd freezing and failing"
date: 2005-02-20
forum: Desktop Environments
---

### Post by ions on 2005-02-20
When I try and open either of these 2 apps I get one of the following:

- The apps take forever to appear.  This happens everytime I try and open either of them.

- Sometimes they appear as a white window with a title bar and that's it.  Closing them requires a force-quit.

- Sometimes they'll flash on the screen quickly and just disappear.  

- When I run them from the commandline sometimes I'll get GTK errors.  Sometimes nothing.

- Sometimes they open but as soon as I try and use either one they quit responding and a force-quit is required.

- I don't know if this is related but Totem is extremely slow to open.  xine, works well and quickly.

This is a 3 day old Warty install on a Barton 3200.

---

### Post by kassetra on 2005-02-20
It could be just those two apps, or it could be a problem with your cd-rom drive.  Have you tried sound-juicer as an alternative cd-player?  This is the easier of the two possible problems to test.  :)

---

### Post by ions on 2005-02-20
Oops, forgot to mention Soundjuicer is doing the same sorta thing.  It opens immediately but is just a white window with a title bar.  

It could be a CD-rom issue although I never heard a peep from my cd rom in Gentoo my dmesg is full of hdc: lost interrupt.

---

### Post by ions on 2005-02-20
As a test I tried to start grip w/o a CD in the drive and the behaviour remains unchanged.

---

### Post by kassetra on 2005-02-20
yeah, I know pretty much what the problem is, but I'm trying to find a way of giving you a solution...
  
  give me a bit to poke around on my machine here...
 
 Ok... not sure if this will work or not, try booting linux with:
 ```
linux noapic nolapic
```

---

### Post by ions on 2005-02-20
You mean add that to Grub?

---

### Post by kassetra on 2005-02-20
[QUOTE=ions]You mean add that to Grub?[/QUOTE]
 
 yes, you can also just boot with that option.

---

### Post by ions on 2005-02-20
[QUOTE=kassetra]yes, you can also just boot with that option.[/QUOTE]
 Hmmm how do I boot with it?  I tried to find a place to do but only ended up at grub> which didn't like the command at all.

---

### Post by ions on 2005-02-21
[QUOTE=ions]Hmmm how do I boot with it?  I tried to find a place to do but only ended up at grub> which didn't like the command at all.[/QUOTE]
 Never figured out how to boot with those options added so I just edited grub.  I only had time for a quick test but it appears to have worked.   Thanks kassetra! :)

---

### Post by kassetra on 2005-02-21
[QUOTE=ions]Never figured out how to boot with those options added so I just edited grub. I only had time for a quick test but it appears to have worked. Thanks kassetra! :)[/QUOTE]
 
 Oh gosh, I'm sorry I dropped the ball on you!  I'm glad its working so far for you though!!

---

### Post by ions on 2005-02-22
[QUOTE=kassetra]Oh gosh, I'm sorry I dropped the ball on you!  I'm glad its working so far for you though!![/QUOTE]

Oh not at all, you gave me what I needed to know and I got where I needed to go. :)

---

### Post by kassetra on 2005-02-22
[QUOTE=ions]Oh not at all, you gave me what I needed to know and I got where I needed to go. :)[/QUOTE]

Yay!  (I still feel bad I didn't answer you though!)

---

### Post by jamaas on 2005-02-23
Bless you ... I bow in complete respect ...
I have a brand new system, loaded Hoary and could not make the CD player work consistantly .... no idea why!!  This seems to have fixed it!

Now the question.  I have two systems and both now exhibit this behaviour.  When booting I get the Ubuntu square in the middle of the screen and then the first two little squares appear, the second one and the title underneath is "metacity windoes manager" and then the system just sits for about 2 minutes and waits!  Only happened when added these boot arguments!  Any idea what causes it.. or how to fix it so it boots quickly like it used to?  Thanks  Newbie here!

Best Regards

Jim


[QUOTE=kassetra]yeah, I know pretty much what the problem is, but I'm trying to find a way of giving you a solution...
  
  give me a bit to poke around on my machine here...
 
 Ok... not sure if this will work or not, try booting linux with:
 ```
linux noapic nolapic
```[/QUOTE]

---

