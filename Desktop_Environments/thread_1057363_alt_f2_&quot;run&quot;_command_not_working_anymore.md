---
title: "alt f2 &quot;run&quot; command not working anymore"
date: 2009-02-01
forum: Desktop Environments
---

### Post by deadtom on 2009-02-01
Since upgrading to kde 4.2 alt-f2 no longer brings up the run dialogue.
Help?

---

### Post by binbash on 2009-02-02
I had same problem.It was working at a clean install of kubuntu but after an upgrade it was broken.I had to change the shortcut to ctrl+alt+space,try changing it to another shortcut

---

### Post by gjoellee on 2009-02-02
You can simply use terminal, just add an "&" in the end of the command so you don't need to have the terminal open. Ie:
```
firefox &
``` that will launch firefox and make it stay open when terminal is closed.

---

### Post by deadtom on 2009-02-02
> **gjoellee said:**
> You can simply use terminal, just add an "&" in the end of the command ...

Yes, I'm aware of how to background a process but I like prefer the run command. Changing it from the default did the trick. I wonder why the default alt-F2 isn't working. It's gonna take me a while to get used to something else.

Thanks binbash!

---

### Post by dabl on 2009-02-02
If you have "desktop effects" enabled, you might try an experiment of disabling them and (after restarting X) check Alt-F2.  Also, try changing the window decorator and then restart X and check it.

I proved to my satisfaction, on KDE 4.1.x, that the Emerald window decorator was effectively an "Alt-F2 killer".  Not Compiz, just Emerald.  Compiz with Kwin was OK.

Now, with KDE 4.2 installed, Alt-F2 is working again on my rig, even with Compiz and Emerald enabled.

---

### Post by kiprit on 2009-02-10
I had the same problem, I don't know if it is caused by compiz (even though i had compiz beforehand, alt f2 used to work until I upgraded to kde 4.2) but i solved it with compiz...

Start Compiz Config Settings Manager
Go to General Options, under Commands tab
under the commands fold, command line 0, type: krunner
go to "key bindings" fold, Run command 0, assign <Alt+F2>

When i did this, I first had a conflict with the "run dialog," so for the "run dialog" (under key bindings tab) I had to assign a different combination... if you need to do this, don't try ctrl-alt-f2 :)

---

### Post by bobdobbs on 2009-05-06
> **kiprit said:**
> I had the same problem, I don't know if it is caused by compiz (even though i had compiz beforehand, alt f2 used to work until I upgraded to kde 4.2) but i solved it with compiz...

Start Compiz Config Settings Manager
Go to General Options, under Commands tab
under the commands fold, command line 0, type: krunner
go to "key bindings" fold, Run command 0, assign <Alt+F2>

When i did this, I first had a conflict with the "run dialog," so for the "run dialog" (under key bindings tab) I had to assign a different combination... if you need to do this, don't try ctrl-alt-f2 :)


when I enter Alt+F2, I get an error:
Alt+F2 is not a valid shortcut.

What is happening here ?

---

### Post by Zorael on 2009-05-06
It's a hassle, but if it's really bothering you, try renaming your ~/.kde directory to get KDE to recreate its settings. If it was something really annoying like alt+f2 not working, I would, but that's me. You'd lose all your KDE-y settings (though not settings of "non-KDE" apps, like Firefox).

You may need to do this when logged out or when logged in as another user; not sure.

---

### Post by bobdobbs on 2009-05-06
> **Zorael said:**
> It's a hassle, but if it's really bothering you, try renaming your ~/.kde directory to get KDE to recreate its settings. If it was something really annoying like alt+f2 not working, I would, but that's me. You'd lose all your KDE-y settings (though not settings of "non-KDE" apps, like Firefox).

You may need to do this when logged out or when logged in as another user; not sure.

Were you addressing the error that I was getting?
I should maybe added that I'm not using kde.

---

### Post by Zorael on 2009-05-06
> **bobdobbs said:**
> Were you addressing the error that I was getting?
I should maybe added that I'm not using kde.
No, of the original poster's krunner not popping up. Alt+F2 is sort of the default for running stuff, so were it me, I'd rather rework all my settings and get Alt+F2 back than learn to use something else (that I eventually have to unlearn again once I'm at a system where Alt+F2 works).

---

