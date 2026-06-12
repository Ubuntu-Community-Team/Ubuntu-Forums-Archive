---
title: "Emerald theme manager won't apply"
date: 2007-05-26
forum: Desktop Effects &amp; Customization
---

### Post by azizzle on 2007-05-26
Now I have searched and found posts that dealt with problems similar to mine, but none of those solutions worked for me. I have beryl running smoothly, but when i go into emerald there is no Apply button. I try to select the theme, then right-click on beryl manager and reload window decorator, but still nothing happens. I swear this is my last "help me" post for the day then i'm going to stop procrastinating and wash my dog! :p

---

### Post by JordanII on 2007-05-26
Try double clicking on the theme. :D

~Jordan

---

### Post by azizzle on 2007-05-26
haha yes i did that... i think in my frustration i may have quad-clicked on a theme... still no dice

---

### Post by strumluff on 2007-05-26
Usually it auto-applies when you click the theme. An alternative method is to select the theme and then right click on the beryl ruby, and select Reload Window Decorator.

---

### Post by Kuoi on 2007-05-27
But first "Select Window Decorator" ... ans select 'Standard Beryl Decorator (emerald)

Kuoi

---

### Post by Albi on 2007-05-27
Happens with me too, you have to right click the emerald icon in the corner and select "Reload Window Decorator"

---

### Post by NumberOne on 2007-05-27
You can press alt-f2 then type

 ```
emerald --replace
```

then all you have to do is click on themes in emerald and they will automatically change.

---

### Post by valejandria on 2007-09-24
Hi, thanks, work like charm. :lolflag:

---

### Post by univremonster on 2007-09-27
this same issue happened for me, but when I try the solution you suggested I get this:

remonster@remonster-desktop:~$ sudo emerald --replace
Reloading...

(emerald:8158): Gdk-CRITICAL **: gdk_drawable_unref: assertion `GDK_IS_DRAWABLE (drawable)' failed


No matter which theme I pick, even those which are preinstalled

---

### Post by Rupertronco on 2007-09-27
That's because you're using sudo to start emerald. I tried it just for fun and my borders are going nuts, they change every time I re-focus a window, it's kind of fun but you don't need super user to start emerald. If you start the program as a super user, you would have to use the same privileges to change the program.

---

### Post by univremonster on 2007-09-28
Yea I tried it without sudo first, but it didn't even give me an error message, nothing happened.  No theme, no error, nothin'.  Maybe I should try reinstalling emerald...

---

### Post by lionkingfly on 2007-10-02
I'm a chinese ubuntu user.
 I had the same problem with you ,but now i have solved it.
I'd like to share my solution to you.

i think you had installed an old  beryl and emerald,right?
I did so.

so maybe some old setting files  conflict with the new version of beryl and emerald.
I had tried reinstall them,but emerald-theme-manager didn't work,i couldn't use emerald themes.


So it is need to clear the old setting files after remove beryl and emerald(sudo apt-get remove emerald* beryl*).
you should   run   " rm -r ~/.beryl " and " rm -r ~/.emerald" in terminal.

then you can reinstall beryl and emerald.

hope you can solve it as i can.

good luck!

---

### Post by LBAWinOwns on 2008-04-24
> **NumberOne said:**
> You can press alt-f2 then type

 ```
emerald --replace
```

then all you have to do is click on themes in emerald and they will automatically change.
Works perfectly, instantly and flawlessly!

Great post man :)!

---

### Post by LBAWinOwns on 2008-04-25
Oh, the solution works, but is there a way to skip doing it every session restart?

Can be tidious typing in that every time after you login :)

---

### Post by SaddaGocaraRupa on 2008-04-25
go to system > preferences > Sessions
click 'add'
type 
name: emerald
command: emerald --replace

click 'ok' and you should be good to go :)

---

