---
title: "HOWTO: terminal embedded in background"
date: 2009-04-11
forum: Desktop Environments
---

### Post by r4z0rw0lf on 2009-04-11
Okay, this is my first howto so it may stink a little...
This (should) give you a terminal embedded in you're desktop and also allow you to see your icons.
Step 1. you will need devilspie and xcompmgr (optional: transset,konsole)
```

sudo apt-get install devilspie xcompmgr

```
cd to ~/.devilspie
and create "DesktopConsole.ds"
```

gedit DesktopConsole.ds&

```
and put the following code: 
```

(if
        (is (window_name) "DesktopConsole")
        (begin
                (set_workspace 1)
                (maximize)
                (stick)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "desktop")
                (geometry "1024x768+140+122")
        )
)

```
you might have to mess with the geometry setting(format: "WIDTHxHEIGHT+X+Y")
Step 2. open gnome-terminal
create a new profile
```

File->New Profile

```
name it DesktopConsole
go to the "Titles and Commands" and set the Initial Title to DesktopConsole
and set it so when command change the title to keeps its own title
now go to the Background tab and set its to have a transparent background and then set the transparency to maximum(or however transparent you want it.
(you can change to other preferences)
Step 3.
execute these commands:
```

xcompmgr
gnome-terminal --window-with-profile=DesktopConsole

```
you should now have a terminal with the underlying window beneath
now execute: 
```

devilspie

```
check you're workspace #1
you should have a console with the desktop showing through
Step 5.
if all that works
go to System->Preferences->Sessions
click add and for the name put "DevilsPie"
for the command put "devilspie"
click add
now add another named "gnome-terminal"
set command to "gnome-terminal --window-with-profile=DesktopConsole"
add it
now add a last one named "xcompmgr"
with the command "xcompmgr"
Step 6. log out and log back in
you should have terminal with your desktop showing through in the background

You can also try this with konsole(or any other terminal(xterm,Eterm,aterm), and mess with other window transparency with transset
you can also get transset-df (build it yourself :( )
let me know if i did any thing wrong :)

---

### Post by PacSci on 2009-04-11
I believe there is already a tutorial for this, which I have already followed. When I tried using your method to see if it could fix a bug my tutorial had ("Show Desktop" made it disappear), it messed up my gedit window. It might work for other people, though.

---

### Post by cubeist on 2009-04-11
not bad, but can be done with compiz much easier..

create terminal profile with no scrollbars, transparent background, and a unique title

In compiz, under window decoration, select your uniquely title terminal window to NOT draw window decorations.

Also in the window rules plugin, add your uniquely titled terminal to the categories of skip pager, taskbar, below, sticky, non-moveable, non- resizable, etc as you choose.

Last, optionally use the place plugin to specify coordinates for the terminal...

---

### Post by r4z0rw0lf on 2009-04-11
i would have but i cannot get compiz to work.

---

### Post by crownedzero on 2009-10-14
Bumping this so I can find it again! Compiz didn't seem to want to work for me >.<

---

### Post by Shadyboy on 2011-02-07
This way worked for me, but I am not a big-fan of compiz.
Is there a way to NOT be using compis and getting terminal embedded into the background?

-----
never mind I found it out, but now I have a new problem.
Everytime I click outside of the "terminal" it goes away. And I have to start it back up to get it on my background again
Help?

---

### Post by Copper Bezel on 2011-02-07
I think that's a fundamental decision you have to make - if you want pretty things, you'll really have to use Compiz. = )

And as has been said, it's not that Compiz is a slower WM than Metacity, it just comes with (fairly addictive) plugins that can, if you choose to use them, slow things down.

---

