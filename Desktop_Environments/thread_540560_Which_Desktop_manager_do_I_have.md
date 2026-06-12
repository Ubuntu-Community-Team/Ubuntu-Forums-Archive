---
title: "Which Desktop manager do I have"
date: 2007-09-01
forum: Desktop Environments
---

### Post by DGentry on 2007-09-01
I hate to sound like a blithering twit but now I've got my desktop so mixed up and things are just looking weird.

Is there a way to reset it back to what it looked like at the default setup?

I've messed with the beryl manager and I have some thing in preferences that say Emerald Theme Manager.

At one time a week or so ago I actually had the cube effect working but after multiple Umm errr.. clicking on crap it doesn't work now and I can't figure out how to just ...LOL.. Start over.

I hate to say it but at this point I don't even know what or if I'm even using as a theme manager.

Thanks for the help, I really do appreciate it
Doug:lolflag:

---

### Post by 7031 on 2007-09-01
Not sure. I know this probably isn't the best response, but it might be wise to reinstall.

If you want to preserve data, see if you can repartition or something, but it might be better just to wait for someone with more tech knowledge to come by.

---

### Post by DGentry on 2007-09-01
I don't think I need to re-install. that's a tad bit drastic at this point. I'm sure there's a way to see what I'm using.

Just got to do a little searching for something like system info or like the same thing for Linux.

---

### Post by viergeame on 2007-09-01
Anytime you don't have Beryl and Emerald running you should be using whatever theme manager you had before you ever installed Beryl.  I don't remember if you have to be using Emerald to use Beryl, or just have to have it installed.  I forget because I loved Emerald and never tried to use Beryl without it. 
    If you just want to reset Beryl to original settings I'm pretty sure there is a button to do that.  I believe I clicked it once on accident after I spent an hour configuring everything to be just how I wanted it.
    Are you still planning on using Beryl?  Or are you getting rid of it and trying to get everything back to how it was before?  (Sorry if I am completely misunderstanding you, I have a tendency to do that and end up sounding like an idiot.)

---

### Post by DGentry on 2007-09-02
I'd be happy to continue using Beryl for sure. I think I just want to set it back to default. As it is now when I look at my browser, I have no maximise, Minimise or little X to close it. I have a round looking flowerey thing up in the right top corner. just stuff like that.

As far as Emerald goes.. that may explain why I do see emerald in the system prefs.

---

### Post by vambo on 2007-09-02
Not sure exactly what state your desktop is in. If you want to try and get back to a "vanilla" set up
i.e. no fizz confusion etc you could try
```
metacity --replace
```

---

### Post by DGentry on 2007-09-02
Groovy, that metacity --replace worked wonders.

LOL, get this. I just HAD to go screw around and clicked on Enlightenment.

I can't get a term window to come up.
Alt F2 doesn't work.

When I click on the screen I see gnome and GTK and then the flyout box comes out. I see term.

I can't get the mouse over there to click it.

any ideas?

---

### Post by avik on 2007-09-03
After clicking the mouse, can you use the keyboard to select term?  Just a thought.

---

### Post by DGentry on 2007-09-03
Nope. If I click on the desktop I get the following
User Application List >
Gnome>
KDE>
Other>
Enlightenment Epplets>
Restart Enlightenment>
I can mouse to gnome and then to GTK that opens a very rapid flyout window that dissapears in a just a second and then my user menu windows all of a sudden appears in the top of the screen. I can't click anything in that flyout window with all the icons.

I was able to launch a term window but when I did the command of metacity --replace. I recieved the following 

Doug@doug-Linux:~$Metacity --replace
Window manager warning: "" found in configuration database is not a valid value for keybinding "Toggle_shaded"
bash: Window: command not found

---

