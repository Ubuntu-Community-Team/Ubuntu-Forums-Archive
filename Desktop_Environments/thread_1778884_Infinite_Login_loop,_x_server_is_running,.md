---
title: "Infinite Login loop, x server is running,"
date: 2011-06-09
forum: Desktop Environments
---

### Post by Mappenz on 2011-06-09
Hi,

this is my first post here. After i failed at fixing the problem for the past few hours i run out of ideas. So i had to admit i needed to ask for help. I dont remember everything i did but lets start with an overview of the Situation.

I am a total Linux noob. I use xubuntu with xface on a brand new acer TravelMate 5735Z. I got it up and running and used it yesterday and today without much trouble.

When I get to the login screen i klick my username and enter my password. The screen blinks and u can see the shell at f7 for a second before the login dialog apears again. If i enter the password wrong i see a text informing me of that. At the shell at f7 u see some lines they go like 
```
*starting ...
*starting ...
...
checking batery state... 

```I don't think they are important, if anyone thinks those lines have significance i am happy to write them out for you. I tried taking out the accu, no difference.

Also my laptop doesnt shut off when i shut it down.

When started this?
I had a black screen problem which is comon for this laptop. See [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/744187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/744187) . I fixed it for the boot up, and thought i had fixed it for waking up too, but i didn't. So when it ent to sleep the screen went dark, i pressed some keys to wake it up, maybe suspending my self, but theres no telling. Then i pressed the powerswitch so i could boot again. Thats when the infinite login loop began.

What did i do?

After searching the internet and trying solutions to similiar sounding problems i found out that i could type 'startxfce4'. So i found [http://www.x.org/wiki/FAQErrorMessages#Ikeepgettingthemessage.3A.22Serverisalreadyactivefordisplay0.22](http://www.x.org/wiki/FAQErrorMessages#Ikeepgettingthemessage.3A.22Serverisalreadyactivefordisplay0.22)
and
[http://www.x.org/wiki/FAQErrorMessages#Ikeepgettingthemessage.3A.22Cannotestablishanylisteningsockets....22](http://www.x.org/wiki/FAQErrorMessages#Ikeepgettingthemessage.3A.22Cannotestablishanylisteningsockets....22)
both fit to the what i read when i type 'startxfce4' depending on wether i deleted .X0-lock or not. Tryiing to lock in to a xfce sesion by the login dialog restores the lockfile.

If you need more specific information i will happily deliver, though i might need some help on that too.

regards
Michi

---

### Post by Toz on 2011-06-09
Have a look at your ~/.xsession-errors file for an error message. This might be tricky given that you can't log into the GUI to view the file. You'll have to do this command line. Ctrl-Alt-F1 will get you to a terminal prompt. Login using your id and password. Once logged in (text-only), type:```
less ~/.xsession-errors
```
You can then use the arrow keys on your keyboard to move around in the file.

Have a look for any kind of error message and post it back. I've seen some recent posts about an error message related to .ICEauthority. Keep an eye out for that.

Ctrl-Alt-F7 will get you back to the graphical login screen.

---

### Post by Mappenz on 2011-06-10
Thanks,

that led me to the solution. In the logfile i found an entry telling me that i was unable to access ICEauthority. I deleted this file and can login again. I can't reproduce the log for details, but i think thats not a big loss.

michi

---

