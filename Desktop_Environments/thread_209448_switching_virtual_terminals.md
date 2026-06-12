---
title: "switching virtual terminals"
date: 2006-07-05
forum: Desktop Environments
---

### Post by Matthew Bartram on 2006-07-05
ctrl+alt+(function key) no longer switches my virtual terminal! Can anyone tell me how to make it work again?

Thanks

---

### Post by 23meg on 2006-07-05
What happens when you hit Ctrl + Alt + F(x)? Do you get a blank screen? Can you return to the X environment when you hit Ctrl + Alt + F7?

---

### Post by Matthew Bartram on 2006-07-05
What do you mean by F(x)? if you mean F1-F6/F8-F12, that's what's not working.

---

### Post by Ramses de Norre on 2006-07-05
What do you see then when you do ctrl+alt+F1?

---

### Post by Matthew Bartram on 2006-07-05
Nothin happens - I'm still in terminal 7 (I presume it's terminal 7 as it ought to be)
But nothing happens to my screen

I can log in multiple users, and switch between them using gnome's panel applet for user switching. So multiple terminals seems to work, just the shortcuts for changing them don't.

---

### Post by martux on 2006-07-07
same for me after upgrading to dapper... any suggestions?

---

### Post by Matthew Bartram on 2006-07-16
I wonder if it's a gnome thing? Seems odd though. Once I'm in a different terminal, without any gui, it works.

---

### Post by Matthew Bartram on 2006-07-16
Ok, it's not. I just logged in with KDE, and the same problem is still there.

---

### Post by ctaggart on 2006-07-16
ctrl+alt+f<x>, where x is 1 to 6 do not work for me either.  ctrl+alt+backspace works just fine.  I'm running the latest Dapper.  Lucky for my, it is freezing several times a day too.

---

### Post by Matthew Bartram on 2006-07-17
My brother has Kubuntu dapper, and it works for him. So it's not a universal dapper problem. But on the other hand it's not just a gnome problem.

---

### Post by Matthew Bartram on 2006-07-17
I had a problem with my '£' key, and now I've followed [these instructions](http://www.ubuntuforums.org/showthread.php?t=207603&highlight=XKB) to fix that, my ctrl+alt+f<x> work. :-)

---

### Post by tymanthius on 2006-08-10
I've also started being unable to swap VT's.  I was able to up until a few weeks back (not sure of the exact time, as I've been too busy).  But I dont' think I did any updates before it broke.  

I tried the linked fix, changing gb to us, but no dice.  :(

Thanks for any help!

Ty

---

### Post by mrashley on 2006-08-15
I'm having a similar problem to Matt, though with a US keyboard. I tried to synthesize a new command (specifically)

```
setxkbmap -model pc105 -layout us
```

or

```
setxkbmap -model pc105 -layout us -variant basic
```

but neither worked out for me. 

I noticed that when I go into system > preferences > keyboard and look at the  layouts tab that my keyboard model says "unknown" and when I click on the [...] button to look at known keyboard models it doesn't have any.

Furthermore the 'us' selected layout was unchecked. I have checked this, but don't notice any difference. Again, the [+Add] (new layout) button is greyed out so presumably there are none to choose from.

I'm using Dapper Drake 6.06.

---

### Post by Arisna on 2006-08-15
There is a parameter that can be set in xorg.conf to prevent switching VT's in any graphical session on the system.  That may not be the cause here, but you can easily check to see if you have it set by typing the following in a terminal:

```
grep -i novtswitch /etc/X11/xorg.conf
```

If there is output, this is the problem.  Removing or commenting out the corresponding option line using a text editor will solve it.

---

### Post by mrashley on 2006-08-24
Nope. That's not it. :-/ 

Thanks though.

---

