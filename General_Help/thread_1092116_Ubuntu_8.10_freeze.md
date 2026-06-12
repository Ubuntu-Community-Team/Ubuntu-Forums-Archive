---
title: "Ubuntu 8.10 freeze"
date: 2009-03-10
forum: General Help
---

### Post by prokopis on 2009-03-10
i have install ubuntu 8.10 on my pc. my problem is that in any time my OS freeze and i can't use anything and the only that is working is the mouse but i can't select anything. the only that i can do is to leave is for 10 hours and maybe more in order to start working or to turn-it off manually from the button and start it again.
am using a satellite a100-192 model.
is there anything that i can use in order to check what is the problem???
i have it and previous this problem and i install again the ubuntu but it's still doing it

---

### Post by kryptikos on 2009-03-10
What's interesting is that you said you could come back after time and the system would be available for use again. The first thing to determine is whether it is Linux in and of itself or just the X server. Shooting from the hip I'd lay money on X at the moment. 

The quickest way to determine that is to try to bump and hang up the X server by issuing:

**[INDENT]ctrl + alt + backspace[/INDENT]**

That should cause your screen to blink as X hangs up and resets itself. If it is successful you should be presented with a graphical log in prompt and your keyboard should be working again. If that works I would reconfigure X. If it didn't work we can manually try to bump it. To do that you need to log into tty terminal console by pressing:

**[INDENT]ctrl + alt + f1[/INDENT]**   (if that doesn't pull anything up try f2, f3 and f4)

That should change the display to just one solid tty console. Then run:

**[INDENT]/etc/init.d/<gkx>dm stop[/INDENT]**where g, k or x is the display manager that you are using. Most likely you are using "gdm". Then run:

**[INDENT]dpkg-reconfigure xserver-xorg[/INDENT]**

And walk through the steps to reconfigure. See if that helps. If not we may need more diagnosing (which would involve the tty console anyways).

---

### Post by prokopis on 2009-03-10
thx. i will try it the next time that it will freeze,which mean in a few hours

---

### Post by prokopis on 2009-03-10
i have try what you have told me but when it freeze i can't do anything.
i can't use the keyboard. the only that i can use is the mouse.
nothing else

---

### Post by prokopis on 2009-03-11
it freeze again.2 times today and is still 10 in the morning. the only key that is working is the FN keys,some of them of course. is there any tool that i can check if is any hardware problem or software???

---

### Post by prokopis on 2009-03-13
i try removing the RAM but it still freeze.does anyone know what i can do???

---

### Post by sideaway on 2009-03-16
~bump~

Does anyone have a solution to this? I'm in the exact same boat here. Happens mostly when I put a lot of stress on the HDD or network. Or rather, using amarok, because that's what I've been doing mainly, shuffling gigs of music around on the network, recently.

---

### Post by prokopis on 2009-03-16
i try evrything and at the end there was the drivers with the ATI i think:)
but now and 3 day after i install the drivers is working without freezing the screen.
i will find the page that i update the drivers and i will send it to you later today because i have exam in a few hours.

give me some time and i will send you the page

---

### Post by sideaway on 2009-03-16
Aaah, cheers bud.

My laptop's been frozen for 12 hours right now, I'm unwilling to admit I've lost my work. I may just have to let go and restart... :(

If you could send that page, that'd be great :)

---

### Post by prokopis on 2009-03-16
i found it :)
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Configure_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Configure_the_Driver)
i use the method 1.
it's working for the moment. i don't know if it's working the next week

sorry for the delay:)

---

### Post by sideaway on 2009-03-16
All good, thanks heaps.

+1 for you my friend.

---

