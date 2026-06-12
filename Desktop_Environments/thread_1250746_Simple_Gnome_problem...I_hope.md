---
title: "Simple Gnome problem...I hope"
date: 2009-08-26
forum: Desktop Environments
---

### Post by Spooky_Kilt on 2009-08-26
So last night i installed ubuntu 9.4 for netbooks on my eeepc 1005ah.  I first had problems with getting wifi and ethernet to work but i solved that by fallowing the instructions from this page

[http://www.jfwhome.com/](http://www.jfwhome.com/)

it worked well and after i did that i switched from the netbook desktop mode to the classic one.  i then did some messing around with the panels to get them how i liked.  so far that has been all i have done on my netbook but when i went to turn it on today all my panels were gone.  the only thing i could get open was ubuntu help by pressing f2 which did not help.  I am also able to get into firefox because i right clicked on the desktop and made a new html file which i can click to get firefox open. 

that is all i am able to do.  i also noticed that i have no window borders.


I have no idea what to do so hopefully somebody can help me out here.

---

### Post by yabbadabbadont on 2009-08-26
Try hitting Alt-F2 to open a run dialog.  Then enter "gnome-panel" (without the quotes) and hit enter.  That should get you back one of them.  Then you can right-click on the new panel and use the options there to add another one.

---

### Post by Spooky_Kilt on 2009-08-26
i tried that.  nothing happens when i press alt f2  i think its more of a problem than just a lack of panels.  i also have no window borders so i can not move them around resize them or minimizethem or anything

---

### Post by yabbadabbadont on 2009-08-26
Try using the failsafe session.  If that works, then try removing the hidden (the names start with a period) directories .gnome* .gconf* and .metacity*.  Then login normally and see if it helps.

---

### Post by Spooky_Kilt on 2009-08-26
i dont have a login screen.  i set it to just login automatically

---

### Post by yabbadabbadont on 2009-08-26
Now you know why that can be a bad idea...  ;)

Hit Control-Alt-F1.  That should drop you to a text console.  You can then login there and use the "rm" command to remove those directories.  You will need to use the "--recursive" option to remove them and all their contents.  Normally I wouldn't suggest this as it will remove all your custom gnome settings.  However, since you just installed it last night, I doubt that you'll lose much.

Edit: Once you have done that, just run "sudo reboot" to restart the machine to see if it worked.

---

### Post by Spooky_Kilt on 2009-08-26
so i logged in and after that i should type in
rm .gnome
rm .gconf
rm .metacity

right?  sorry i am not good at these things  i am new to this

---

### Post by Spooky_Kilt on 2009-08-26
oh and i found a way to get into the file system.  i looked to see if the hidde gnome files were there and they were.  any way i could set them to default or something?

---

### Post by yabbadabbadont on 2009-08-26
What I meant was:
```
rm --recursive .gnome*
rm --recursive .gconf*
rm --recursive .metacity*
```
Then run the "sudo reboot" command to restart.

---

### Post by Spooky_Kilt on 2009-08-26
it said i dont have a .metacity file

---

### Post by yabbadabbadont on 2009-08-26
Then don't worry about that one.

---

### Post by Spooky_Kilt on 2009-08-26
awesome!  its back  thanks for the help!!

---

