---
title: "How do you force applications to minimize"
date: 2009-06-14
forum: General Help
---

### Post by azzid on 2009-06-14
I have a habit, stuck in me from all those years with m$ windows, to hit win+d to force applications to minimize.

I have been able to set up the same shortcut in Ubuntu, but it does not work all the time since some applications keep stealing the keyboard input from gnome.

Is there some signal that is always able to get down to the underlying system?

Sometimes applications fail and you just need to get down to the operating system, but as stated above, I have been unable to figure out how to.

Anyone got any tips?

---

### Post by sigixv on 2009-06-14
> **azzid said:**
> Sometimes applications fail and you just need to get down to the operating system
Are you looking for a way to close down (kill) an application as it freezes? Or simply minimize the window?

---

### Post by dnairb on 2009-06-14
<WIN> + D is the "show desktop" keyboard shortcut.
In Ubuntu, the default shortcut is <ctrl><alt><d>

You can change this in System --> Preferences --> Keyboard Shortcuts (on the gnome desktop)
The entry is near the bottom, listed as "Hide all normal windows and set focus to the desktop background".

---

### Post by dnairb on 2009-06-14
Having read the OP properly now, (d'oh!), what you may need is the "Force Quit" panel-thingy. This is a graphical way of forcing a misbehaving app to close.
Right-click a panel, select "Add to panel", highlight "Force Quit" about half-way down the list, and click Add

---

### Post by nothingspecial on 2009-06-14
Alt F4

It may give a message about not responding

Just hit Tab then Return/Enter

---

### Post by azzid on 2009-06-15
Thanks for the answers guys, but I am still not really satisfied.

What I want is something like the task manager from windows, something you can always get a hold of without first killing off the troubling apps.

alt+f4 would just kill the application...

---

### Post by RobOrr on 2009-06-15
System > Administration > System Monitor is the most similar program to Task Manager I guess.

---

### Post by nothingspecial on 2009-06-15
```
ps aux | less
```

Shows all running processes

 ```
ps -u azzid
```

Shows all your processes (assuming your username is azzid)

Then you can kill by pid or killall by name

Or if you just mean minimize Alt F9

---

### Post by azzid on 2009-06-15
Still not quite what I am looking for.

The reason I started thinking about this was that I was unable to "get behind" xbmc when I wanted a browser while waiting for my gf to come back to the tv.

I realized then that I could not get a hold of the underlying OS, in windows (i keep naging about it, I know) a tap on the win-key would have forced xbmc to minimize, in gnome I cannot figure a similar move out.

The actual problem with xbmc I have circumvented by learning the keyboard shortcut for that application to switch to windowed mode, but I know I will find myself in similar situations in the future with other fullscreen apps, that's why I am looking for a universal way to get back to the desktop.

---

### Post by nothingspecial on 2009-06-15
I`m thinking (never having used windows) that I don`t actually understand what you want but for a final throw of the dice if you want all windows minimized so that all you can see is your Desktop then either

Ctrl Alt D

or

Ctrl Alt (left or right arrow) to switch to another workspace/desktop.

If I am missunderstanding sorry for wasting your time - haven`t a clue what task manager does

---

### Post by azzid on 2009-06-15
nothingspecial: I really appreciate you taking your time here. ;)

ctrl+alt+d, or in my case, since I've done some remapping, win+d will only force applications to minimize if they are in windowed mode.

If you try the same with an application like [xbmc]("http://xbmc.org/download/") nothing will happen. The application will absorb the keyboard signals, and gnome will do nothing.

Some signals however are always snatched by the operating system, like ctrl+alt+f1, which will give you a prompt.

With that you can always rock your command line skills and make the system behave when things are going really wrong.

Sometimes things are not so bad though, and all you want is a web browser even though the fullscreen application you are using is missing a minimize button.

You see, I want the crowbar to use instead of the rocket launcher when the door is missing the door knob. ;)

---

### Post by nothingspecial on 2009-06-15
I think I understand you now.

xbmc looks like a really cool app.

As a final throw of the dice, look at [[COLOR="Red"]this[/COLOR]]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/346009106631")

I think it`s what you are looking for.

Weather or not it works .......it`s very old and probably the first workings of the show desktop applet.

However the script itself might point you in the right direction.

---

### Post by MuseIC on 2011-05-13
I know this is an old thread, but it popped-up when I was trying to find the answer to the same question.

"how to minimise xbmc in unbuntu"

the answer, hit "\" to switch xbmc to windowed mode then minimise or resize to your heart's content.

---

