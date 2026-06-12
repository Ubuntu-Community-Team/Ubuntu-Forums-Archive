---
title: "How do I move gnome panels in jaunty?"
date: 2009-04-27
forum: Desktop Environments
---

### Post by baking666 on 2009-04-27
I used to drag and drop a gnome panel to the side of the screen I wanted but now it seems the powers that be have removed that ability :-(

Yes I could open the options menu and pick top, bottom, side etc but this only supports single monitors...

So now I have no way of putting a gnome panel on my second monitor :-(

I assume the gnome dev's don't use dual monitors?

or have I missed something?

---

### Post by chris062689 on 2009-04-27
I want to say there locked down by default now.
Try Right Click > Preferences > Unlock

---

### Post by baking666 on 2009-04-27
> **chris062689 said:**
> I want to say there locked down by default now.
Try Right Click > Preferences > Unlock

I have no unlock option on my jaunty?

---

### Post by ninjapirate89 on 2009-04-27
There may be a way to get the results you want by playing with the Configuration Editor. Unfortunately I have never used dual-monitors and don't know how this would be done.

---

### Post by XeroXer on 2009-04-27
> **baking666 said:**
> I used to drag and drop a gnome panel to the side of the screen I wanted but now it seems the powers that be have removed that ability :-(

Yes I could open the options menu and pick top, bottom, side etc but this only supports single monitors...

So now I have no way of putting a gnome panel on my second monitor :-(

I assume the gnome dev's don't use dual monitors?

or have I missed something?

I upgraded to Ubuntu 9.04 (Jaunty Jackalope) a few days ago and have the same problem.

I use a laptop, most of the time at the office with a second monitor plugged in, but also a lot on it's own at home.
Since the upgrade I can never get the panels where I want them, they just position themself wherever they want.

If I right click an existing panel and select "New Panel" I never know with display it might end up on.
If I then select the panel properties and change position to something else, the panel sometimes jump over to the other display. (And sometimes even drag 1-2 other panels with it.)

---

### Post by blierp on 2009-04-27
i found the 'answer' in this thread:
[http://ubuntuforums.org/showthread.php?t=1133221&highlight=move+gnome+panel](http://ubuntuforums.org/showthread.php?t=1133221&highlight=move+gnome+panel)

basically, you have to rightclick the panel, go in the properties and uncheck 'Expand'. This allows you to move the panel. When it's in the right position check 'Expand' again and you're set.

i don't think this is how it's supposed to work but it'll do for now.

---

### Post by baking666 on 2009-04-27
> **blierp said:**
> i found the 'answer' in this thread:
[http://ubuntuforums.org/showthread.php?t=1133221&highlight=move+gnome+panel](http://ubuntuforums.org/showthread.php?t=1133221&highlight=move+gnome+panel)

basically, you have to rightclick the panel, go in the properties and uncheck 'Expand'. This allows you to move the panel. When it's in the right position check 'Expand' again and you're set.

i don't think this is how it's supposed to work but it'll do for now.

Well not for what i want....for starters it only moves from top to bottom and any location in between. So you can't move to sides or to another monitor :-(

But thanks for the help :-)

---

### Post by cybrsrce on 2009-04-27
> **baking666 said:**
> Well not for what i want....for starters it only moves from top to bottom and any location in between. So you can't move to sides or to another monitor :-(

But thanks for the help :-)

I was able to move it to the other monitor using this trick.  I have separate X screens with Xinerama enabled (Nvidia NVS 140).  Once placed on the second monitor I can go to properties -> expand -> and position it on any of the 4 edges.

What video card do you have?

---

### Post by skotos on 2009-04-28
> **baking666 said:**
> Well not for what i want....for starters it only moves from top to bottom and any location in between. So you can't move to sides or to another monitor :-(

But thanks for the help :-)
If you cannot otherwise grab the panel (this was my case),  you have to disable the hide buttons, too: this will give you the space/handles to grab the panel wherever you want and this definitely solves the problem! :) HTH

---

### Post by wychwood on 2009-04-28
I had the same problem - you can move them more easily than this by holding down "alt" and dragging the panel where you want it.

---

### Post by jazzgossen on 2009-04-29
OK, that works. But after moving a panel to the next monitor and re-expanding it, I also need to re-place my applets where I want them... Sigh!

(Sorry for an unconstructive post, but this is just annoying)

---

### Post by FootySr on 2009-04-29
Thanks everyone! This is my first ubuntu install and I kept thinking I was missing something in the Display control panel. :)

---

### Post by Eneerge on 2009-04-30
Ahhh, you have to use the ALT key now to move the panels.  Why didn't I think of that?  Lol, thanks for that tip.  

If any of you are also having the problem where your panel positions are not being remembered, you can try modifying the %gconf.xml file.  Here's my reply over on another post that explains the procedure: [http://ubuntuforums.org/showpost.php?p=7182438&postcount=18](http://ubuntuforums.org/showpost.php?p=7182438&postcount=18) and here it is in context: [http://ubuntuforums.org/showthread.php?t=799626&page=2](http://ubuntuforums.org/showthread.php?t=799626&page=2)

---

### Post by skotos on 2009-04-30
> **wychwood said:**
> you can move them more easily than this by holding down "alt" and dragging the panel where you want it.
Thanks!

---

### Post by mrtorrent on 2009-05-04
The "alt" trick worked, thanks! What an irritating little thing.

---

### Post by Mongo5000 on 2009-05-11
> **blierp said:**
> i found the 'answer' in this thread:
[http://ubuntuforums.org/showthread.php?t=1133221&highlight=move+gnome+panel](http://ubuntuforums.org/showthread.php?t=1133221&highlight=move+gnome+panel)

basically, you have to rightclick the panel, go in the properties and uncheck 'Expand'. This allows you to move the panel. When it's in the right position check 'Expand' again and you're set.

i don't think this is how it's supposed to work but it'll do for now.

Worked fine for me, thanks :guitar:

---

### Post by kstephens on 2009-06-11
ALT+drag does not work for me.  

What was the point of disabling dragging of the panel in 9.04?  Was there any point at all?  Why remove a convenience?

I regularly attach and detach a second monitor to laptop.  Having to move the panels to different displays when I dock or undock was annoying enough, but now I have to:

1) right click
2) disable expand,
3) click OK, 
4) move the panel right click, 
5) enable expand, 
6) click OK"

for two panels (!!!).

PLEASE: bring back the "MOVABLE" option in the right click menu from 8.x.

If someone will point me to the code, I'd put it back myself. :)

---

### Post by fizban9 on 2009-06-13
> **blierp said:**
> i found the 'answer' in this thread:
[http://ubuntuforums.org/showthread.php?t=1133221&highlight=move+gnome+panel](http://ubuntuforums.org/showthread.php?t=1133221&highlight=move+gnome+panel)

basically, you have to rightclick the panel, go in the properties and uncheck 'Expand'. This allows you to move the panel. When it's in the right position check 'Expand' again and you're set.

i don't think this is how it's supposed to work but it'll do for now.

TY!  That did it for me as well.  I was already contemplating downgrading back to Jaunty if there was no fix for this.

---

### Post by eternalnewbee on 2009-06-13
Right-click on the Panel, click on properties, and at Orientation you can choose left, right, or bottom . . .

---

### Post by asmoore82 on 2009-06-14
The rationale from the Gnome project is that Alt+Button1 moves windows, now the panel is the same.

I know from experience with my girlfriend and her friends that
it was too easy to accidentally move a panel before.

My suggestion for the future would be that Alt Drag should also be used
to remove ambiguity; it should always move whole panels and never
individual panel applets. Currently, you still have to make sure that
you Alt+Click "empty" space on the panel to grab it.

BTW, you could also "right-click the panel -> properties" and change "orientation,"
That is the ultimate equalizer against ambiguity I guess.

---

### Post by smokey_58au on 2009-06-14
> **kstephens said:**
> ALT+drag does not work for me.  

What was the point of disabling dragging of the panel in 9.04?  Was there any point at all?  Why remove a convenience?

I regularly attach and detach a second monitor to laptop.  Having to move the panels to different displays when I dock or undock was annoying enough, but now I have to:

1) right click
2) disable expand,
3) click OK, 
4) move the panel right click, 
5) enable expand, 
6) click OK"

for two panels (!!!).

PLEASE: bring back the "MOVABLE" option in the right click menu from 8.x.

If someone will point me to the code, I'd put it back myself. :)

Exactly my scenario.  Why oh why did they ever change something that worked efficiently and perfectly.  This is a real pain to me because I change from laptop to laptop/monitor multiple times in any given day.  And in addition to the steps above, I now also have to change the settings for the hide buttons with each move.  This is a backward step that I can't see any justifiable reason for.  And as for (on the rare occasion it happened) moving a panel in error - it was sooooooo easy to put it back before.  Try putting it back now!!  :(

---

### Post by asmoore82 on 2009-06-15
> **smokey_58au said:**
> Exactly my scenario.  Why oh why did they ever change something that worked efficiently and perfectly.  This is a real pain to me because I change from laptop to laptop/monitor multiple times in any given day.  And in addition to the steps above, I now also have to change the settings for the hide buttons with each move.  This is a backward step that I can't see any justifiable reason for.  And as for (on the rare occasion it happened) moving a panel in error - it was sooooooo easy to put it back before.  Try putting it back now!!  :(

Alt+Drag - it's just that easy.

if it doesn't work, it will be whatever you have changed it to under
"System -> Preferences -> Windows" and the "Movement Key" section.

---

### Post by gilesp on 2009-06-15
> **asmoore82 said:**
> Alt+Drag - it's just that easy.

if it doesn't work, it will be whatever you have changed it to under
"System -> Preferences -> Windows" and the "Movement Key" section.

Unfortunately, this only works for me if I have my "Movement Key" set to "Alt".  This proved to be an annoyance to me in other applications, so I had it set to the "Super" (windows logo) key, and moving my panels using that didn't work.  Am too busy to file a bug right now :(

---

### Post by mhgsys on 2009-06-15
why don't you just add new panels to the second monitor>>?

and to put the panel back to original , just check the expand option again.

---

### Post by Coder_ak on 2009-07-27
Still no progress with this bug.
Really annoying. 
Is somebody filled a bug on Launchpad or somewhere else?

---

### Post by todb on 2009-09-21
First off, thanks for the uncheck "Expand" tip. That totally works. It's still only half a solution, though -- I use a couple scripts to switch between laptop-only and external monitor configs:

```

todb@mazikeen:~$ cat `which 1screen`
#!/usr/bin/env bash

xrandr --output TMDS-1 --off
xrandr --output VGA --off
xrandr --output LVDS --auto
todb@mazikeen:~$ cat `which 2screen`
#!/usr/bin/env bash

xrandr --output TMDS-1 --auto
xrandr --output LVDS --left-of TMDS-1

todb@mazikeen:~$ 

```

Now, if I go to 1screen, my panel disappears completely, when on 8.10, it dutifully moved over.

Another irritant is that my Window List won't move to the correct "bottom" of my external monitor -- if I move it over to the larger monitor, it still behaves as though it's stuck at the bottom of the smaller laptop screen (which makes it kind of hang out about an inch and a half above the true bottom of the external display.

I haven't figured out how to fix this.

So sad. Perhaps it's time to try another window manager...

---

### Post by nimbis on 2009-10-10
Another solution:

1. Right-click on the gnome-panel and click "New Panel".
2. Do this twice and you should now have 4 panels on your first screen.
3. Repeat (1) again and panels will now be created on the second screen.0
4. When you have the panels you want, delete the ones you don't :).

---

### Post by Rich43 on 2009-10-30
> **skotos said:**
> If you cannot otherwise grab the panel (this was my case),  you have to disable the hide buttons, too: this will give you the space/handles to grab the panel wherever you want and this definitely solves the problem! :) HTH

VERY USEFUL ^^^

Thanks!

---

### Post by mkomo on 2010-04-12
there is also a setting in gconf, which can be changed in a script:

```

gconftool-2 --type int --set /apps/panel/toplevels/top_panel_screen0/monitor 1
gconftool-2 --type int --set /apps/panel/toplevels/bottom_panel_screen0/monitor 1
```this moves the top and bottom panel to the monitor at index '1'. you can move them back to your primary monitor with:

```

gconftool-2 --type int --set /apps/panel/toplevels/top_panel_screen0/monitor 0
gconftool-2 --type int --set /apps/panel/toplevels/bottom_panel_screen0/monitor 0
```I have the following script which takes an argument ('l'=laptop, 'e'=external, 'b'=both):
```

#!/bin/sh

while getopts “leb” OPTION
do
     case $OPTION in
         l)
             xrandr --output VGA1 --off --output LVDS1 --auto
             ;;
         e)
             xrandr --output VGA1 --auto --pos 0x0 --output LVDS1 --off
             ;;
         b)
             xrandr --output VGA1 --auto --pos 0x0 --output LVDS1 --auto --pos 1280x0
             gconftool-2 --type int --set /apps/panel/toplevels/top_panel_screen0/monitor 1
             gconftool-2 --type int --set /apps/panel/toplevels/bottom_panel_screen0/monitor 1
             ;;
     esac
done
```

---

