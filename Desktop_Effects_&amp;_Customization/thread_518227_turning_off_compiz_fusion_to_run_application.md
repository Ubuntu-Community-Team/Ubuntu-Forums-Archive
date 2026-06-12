---
title: "turning off compiz fusion to run application"
date: 2007-08-05
forum: Desktop Effects &amp; Customization
---

### Post by Luksion Knight on 2007-08-05
hey is there a way i can edit several of my quick launch commands (mostly concerning games) so that it will revert to metacity before the game runs, and then switch back to compiz fusion when the game exits?

---

### Post by dougfractal on 2007-08-05
[HTML]
metacity --replace &      # for metacity


compiz --replace &      #  for compiz[/HTML]

---

### Post by Luksion Knight on 2007-08-05
can you be more specific? i know the commands for switching window managers but how do i specificly add the switch window command to a run game command, i try tossing it in there, but it only switches the window manager, doesnt launch the game. and then do i put the compiz command on the end of the quick launch command to make it revert to compiz after the fame exits?

---

### Post by AndrewGene on 2007-08-05
I'm no expert at linux but this won't hurt anything to try...I think it will work.

If you don't have a folder in your home directory called "bin" you can create one.  In it make a file called "gamestart" (or whatever you want to call it).
Then paste this into the file...

#/bin/bash
sleep 10
compiz --replace -c emerald &
sleep 10
avant-window-navigator

Save the file and then make it executable by opening a terminal and cd'ing to whatever the directory is (in this case "username/bin") where the file is found and type...
chmod +x gamestart  (it might be chmod +x gamestart.sh)

Now set the quicklaunch button to start with that script.

Hope this works.

---

### Post by Luksion Knight on 2007-08-06
how do i set the quicklaunch button to start with any script???

---

### Post by dougfractal on 2007-08-06
basic format:

```
metacity --replace ; gimp ; compiz --replace &
```


original format
metacity --replace && sleep 3 ; gimp && compiz --replace &
&& = do next thing on successful complete.
but this would fail to launch gimp if already in metacity



make a script /usr/bin/gamestart
```
#!/bin/bash
# gamestart.sh
# Usage:    gamestart application
# turn compiz off for application
if  [ `ps -A | grep "compiz" | wc -l` -gt '0' ]; then
metacity --replace ; $1 ; compiz --replace &
else
$1
fi
```


```
sudo chmod 755 /usr/bin/gamestart
```

[B]
quicklauncher[/B]
>Create launcher
>Name: Inkscape
>Command:  gamestart inkscape
>Comment:  plain old inkscape

[B]
Or [/B]
Drag icon from menu to Desktop.
Right click> properties > Launcher> command:
add gamestart to the previous command. If there are options use quotes.

example:   /usr/games/tremulous --quiet  >>   gamestart  "/usr/games/tremulous --quiet"

---

### Post by jpereira on 2007-08-06
If you're running Xgl, you might want to take a look at this thread on how to easily run a separate X just for a specific application, thus overcoming the inability to run some 3D games in Xgl.

---

### Post by dougfractal on 2007-08-07
> **jpereira said:**
> If you're running Xgl, you might want to take a look at this thread on how to easily run a separate X just for a specific application, thus overcoming the inability to run some 3D games in Xgl.


It costs about 180MB per gnome X session, So if you have Xgl it might be less memory intensive to logout and use the non-xgl Session.

---

### Post by koshari on 2007-08-07
i posted a thread to pretty much do the same and had limited success.

heres a copy of my opening post, 

seems it would be good to merge the posts as were ultimately trying to acheive the same thing..


ok so stellarium doesnt play well with compiz.

so i are attempting to write a little script that switches the desktop manager back to metacity and then executed stellaruin when compiz is running, 

i started with this basic script that is touch and go, works sometimes and not others,

```
#! /bin/bash
metacity --replace
stellarium
fi
```

i think i need something like 

```
if desktop=compiz
metacity --replace
stellarium
else
stellarium
fi
```

sometimes the batch will change compiz to metacity but doesnt open stellaruium and site in the process running list as sleeping, and then if you select compiz back it leunches stellarium causing havoc.

does anyone know how i can use the if condition to see if compiz is running so satisfy the following conditions?

---

### Post by jpereira on 2007-08-07
> **dougfractal said:**
> It costs about 180MB per gnome X session, So if you have Xgl it might be less memory intensive to logout and use the non-xgl Session.

Well, in that script, it's not running Gnome any window manager or any other application (other than a xterm), it's just running plain old X server, so it barely spends any extra memory at all.

---

### Post by dougfractal on 2007-08-07
> **koshari said:**
> 

ok so stellarium doesnt play well with compiz.

so i are attempting to write a little script that switches the desktop manager back to metacity and then executed stellarium when compiz is running, 

does anyone know how i can use the if condition to see if compiz is running so satisfy the following conditions?


from > **dougfractal said:**
> this thread, post #6

```
if  [ `ps -A | grep "compiz" | wc -l` -gt '0' ] ; then metacity --replace ; stellarium ; compiz --replace & ; else stellarium; fi
```


how it works
```
ps -A  #   list all processes
ps -A | grep "compiz"       # list all processes with compiz
ps -A | grep "compiz" | wc -l    # count the lines with all processes with compiz
if  [ `ps -A | grep "compiz" | wc -l` -gt '0' ] ;    # if line count greater than 0 then
```


I recommend the gamestart script in the above post.
then it would be 
> gamestart stellarium


jpereira,  I should have checked your script.
[http://ubuntuforums.org/showthread.php?t=518426](http://ubuntuforums.org/showthread.php?t=518426)
 good script.  :guitar:

---

