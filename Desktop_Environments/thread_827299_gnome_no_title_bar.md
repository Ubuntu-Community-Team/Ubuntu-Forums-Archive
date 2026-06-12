---
title: "gnome no title bar"
date: 2008-06-12
forum: Desktop Environments
---

### Post by metalmaniac248 on 2008-06-12
hi there

before i start i am very new to Ubuntu, 

my problem is that when i active the gl desktop and desktop effects and all that fancy looking stuff, my title bar disappears (im not sure if title is the right name i am talking about the thing with the close maximize minimize)

also, as far as i can tell the problem arose when i tried to set up dual screen, i was following this tutorial on how to do it 

[http://www.ubuntugeek.com/dual-monitors-with-nvidia.html]("http://www.ubuntugeek.com/dual-monitors-with-nvidia.html") 

i think i must have put something in the wrong place or something, and after i rebooted, the x window thing wouldn't run. So i was stuck with the white letters black background code screen (like what you see when you first turn your machine on) i managed to fix this by doing the restore thing on the tutorial 

but since then gnome has been removing my title bar

any help would be greatly appreciated, i am very determined to stick with Linux

thanks in advance

---

### Post by wootah on 2008-06-12
> **metalmaniac248 said:**
> hi there

before i start i am very new to Ubuntu, 

my problem is that when i active the gl desktop and desktop effects and all that fancy looking stuff, my title bar disappears (im not sure if title is the right name i am talking about the thing with the close maximize minimize)

also, as far as i can tell the problem arose when i tried to set up dual screen, i was following this tutorial on how to do it 

[http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html) 

i think i must have put something in the wrong place or something, and after i rebooted, the x window thing wouldn't run. So i was stuck with the white letters black background code screen (like what you see when you first turn your machine on) i managed to fix this by doing the restore thing on the tutorial 

but since then gnome has been removing my title bar

any help would be greatly appreciated, i am very determined to stick with Linux

thanks in advance

You lost your Window Manager [metacity] (the program that draws the title bar, buttons for closing (minimizing and maximizing), sizing handles, etc).

Applications -> Accessories -> Terminal
metacity --replace &
ALT-F2
(close the terminal now, but leave the run menu open. You should loose the title bars and what not)
metacity --replace

Things should be ok now. At this point, save your session ([http://www.howtogeek.com/howto/ubuntu/make-ubuntu-automatically-save-changes-to-your-session/](http://www.howtogeek.com/howto/ubuntu/make-ubuntu-automatically-save-changes-to-your-session/))

Good Luck! :)

---

### Post by metalmaniac248 on 2008-06-13
hi

thanks for your quick response i did what you said, my title bar is back but now my beryl effects dont work

---

### Post by wootah on 2008-06-13
> **metalmaniac248 said:**
> hi

thanks for your quick response i did what you said, my title bar is back but now my beryl effects dont work

I assume by beryl you mean compiz? What version of Ubuntu are you using?

Were the effects successfully enabled? If so, instead of doing the above steps with metacity, use **emerald**.

So:
```

emerald --replace

```:popcorn:

---

### Post by soccerboy on 2008-06-13
did you get the dual monitor setup working or are you still in limbo?  If so, did you undo all the changes you made when trying to setup dual monitor?

---

### Post by metalmaniac248 on 2008-06-14
> **wootah said:**
> I assume by beryl you mean compiz? 
[/code]:popcorn:

actually it is beryl, i have compiz but the effects from that don't apply

i'm using feisty fawn 7.04 

i tried the emerald thing but my beryl effects still don't work

> Were the effects successfully enabled?

they were before i did the metacity thing, but of course i had no title bar
then once i did the metacity thing my effects didn't work 
and the emerald thing hasn't done anything except from add something called emerald themes manager to my preferences menu

---

### Post by metalmaniac248 on 2008-06-14
> did you get the dual monitor setup working or are you still in limbo?

i never got it set up no, because after i initialy tried it x window manager broke and when i finaly fixed it i decided not to bother with the dual screen set up for fear of breaking it again
> 
If so, did you undo all the changes you made when trying to setup dual monitor?

no i didnt because i didnt know how, as im sure you've probably gathered im not very confident with ubuntu......yet

---

### Post by metalmaniac248 on 2008-06-14
im now running compiz,
still no title bar
emerald theme manager dosn't apply themes
i found what could be a solution to my problem by googling it said to enter this code 
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
into terminal, but when i open terminal when compiz is aplied, i cannot see any text in terminal and i have tried just typing everything in any way but no luck

---

### Post by metalmaniac248 on 2008-06-22
sorry actually that script did work just had to reboot

---

### Post by Wulvor on 2008-06-25
I actually have this exact issue, but am using an ATI Card. I didn't know if I should start a new thread in the Noob forum or not. 

Installed the restricted drivers, everything worked fine. Rebooted,  ran displayconfig-gtk to set up my second monitor, put the settings in, reboot, and got the second monitor at the proper resolution. My problem now is I have 2 Monitors, but no Window manager I guess.  If I unhook the second monitor and restart X, everything is fine. I installed Emerald, again on a single monitor it works fine, as soon as I hook the second monitor up and restart, I can't move any windows etc.  
Tried the emerald --replace command in a terminal when in dual monitor mode, but it just comes up with an error. 
Everything works great  until I hook up the second screen. I would try the command listed above but I am running an ATI card, not nvidia.

Sorry, I have been using Suse and Fedora for a while, so new to Ubuntu etc.

Edit** Forgot to add I am using the newest patched version of Ubuntu

---

### Post by pure0z on 2008-06-27
> **metalmaniac248 said:**
> im now running compiz,
still no title bar
emerald theme manager dosn't apply themes
i found what could be a solution to my problem by googling it said to enter this code 
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
into terminal, but when i open terminal when compiz is aplied, i cannot see any text in terminal and i have tried just typing everything in any way but no luck

Mate I had the exact same issues as you right down to not being able to type in the terminal window....what a bugger this was.
But just the same as you after a restart I had the issue licked.
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
worked a treat, THANKS VERY MUCH

---

### Post by Wulvor on 2008-06-30
I wish I could find something I could pop into a terminal for the same problem with ATI  :(

---

### Post by metalmaniac248 on 2008-07-01
erm im not exactly a ubuntu expert yet but have tried the comand i posted and replacing nVidia with ati 

just a thort please anyone tell me iff this is wrong

---

### Post by metalmaniac248 on 2008-07-01
oh ****, sorry folks didnt see the second page 

:lolflag:

---

