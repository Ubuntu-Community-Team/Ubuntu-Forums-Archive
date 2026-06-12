---
title: "Many problems... Shift+Backspace, modifying path variable, ctrl doesnt work"
date: 2006-07-07
forum: Desktop Environments
---

### Post by seventoes on 2006-07-07
Im having a couple problems with ubuntu. First and most annoying, i cant seem to get Shift+BackSpace to not restart my X server... Ive heard that its a shortcut for compiz or something, but i cant get it to perminantly stay off. I have to type
```
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
```
every time i log in.

Second is that my control button doesnt work right! I use ctrl+c, ctrl+v and a bunch of other shortcuts all the time, but for some reason every time i press control now, it seems like the current window loses focus untill i let go of control.

Last is that i need to modify my PATH environment variable, but i cant get that change to stick either. I need to add /usr/lib/j2re1.5-sun/bin to my PATH, but just like my shift backspace problem, i have to type
```
PATH=$PATH:/usr/lib/j2re1.5-sun/bin
```
every time i log in.

Can anyone help?

---

### Post by amunimanghi on 2006-07-07
Um I dont know about the 1 and 3 problem. Sorry. For the ctrl problem, which programs does it not work with or is it for the entire pc.

---

### Post by Astro96 on 2006-07-07
This is kind of a band-aid solution but you could set those two things to run on startup automatically.

Go to System > Preferences > Sessions
Select the "Startup Programs" tab and then add the two lines.

Andy

---

### Post by seventoes on 2006-07-07
Well one of the many things i tried for the PATH problem worked. I have the xmodmap line in my sessions>startup programs, but it still reboots when i hit the shortcut. As for the ctrl problem, it happens on the computer

---

### Post by PriceChild on 2006-07-07
The shift backspace "feature" really annoyed me.

If you simply enter
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
into a new file and make it executable, then place it in your usr/local/bin folder. Next, adding the name of the file to your sessions>startup It should be run every startup and no--longer have the problem.

---

### Post by seventoes on 2006-07-07
Ahh.. thats better. Thanks PriceChild, that worded beutifully.

---

### Post by scantan on 2006-10-31
I've been having problems with my CTRL keys too.

I posted some clues which I haven't been able to test yet on the following thread:

[http://www.ubuntuforums.org/showthre...highlight=ctrl](http://www.ubuntuforums.org/showthre...highlight=ctrl)

---

