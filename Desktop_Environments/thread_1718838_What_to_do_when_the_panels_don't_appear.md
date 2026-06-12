---
title: "What to do when the panels don't appear?"
date: 2011-03-31
forum: Desktop Environments
---

### Post by L a r r y on 2011-03-31
Having no panels appear is a fairly frequent occurrence for me when I restart my Ubuntu computer.  As I leave the computer on for days at a time, I don't encounter it all that often.

I have no menus to with which to launch applications, navigate or to adjust the system.

My only saving grace is that I did a mod once to add "Open in Terminal" to my context menu, so I could open a terminal using the current directory as the starting point.  I know the command "reboot."

Had I not had that available, what could I have done, short of killing power and restarting the computer?

I know the command "firefox."  So from that terminal I can launch Firefox to ask this question.

I have space allotted for both the top and bottom panels, and Firefox does not extend beyond the screen boundaries set aside for these panels.

If I right-click in the panel space, I get the Desktop context menu.  If I left-click where a menu or quick-launch icon should be, nothing happens.  If I maximize Firefox, it fills the screen, allowing for the missing panels.  I just changed my Desktop wallpaper and it displays in the panel area.  Before, I had a wallpaper that was all black in the panel area, and I selected one that has a flower, and some various colors in different parts of the panel area; left-clicking did not display anything as I clicked on the locations of the Gnome menus.

So, besides using the Terminal to reboot, what is there for me to do?

---

### Post by cbowman57 on 2011-04-01
A lot of times "killall gnome-panel" is all that is needed to respawn the panel.  Try that & see if it does the trick, if not there might be a more serious problem.

---

### Post by Krytarik on 2011-04-01
To restart "gnome-panel" you can run this command, it actually kills it, but it auto-respawns right after that:```
killall gnome-panel
```You could also create a launcher for it, located at your desktop.

Greetings.

---

### Post by patryk77 on 2011-04-01
In case you ever get stuck without the "Open in Terminal" mod:

Press Alt+f2. This should open the "Run Application" window, from where you can use commands like "gnome-terminal" or "killall gnome-panel" as suggested.

Alt+f1 might also open the menu, though it may not work if gnome-panel isn't running properly.

---

### Post by Krytarik on 2011-04-01
> **patryk77 said:**
> 
Press Alt+f2. This should open the "Run Application" window, from where you can use commands like "gnome-terminal" or "killall gnome-panel" as suggested.

Actually, the "Run Application" feature is provided by gnome-panel, and just like you said, if it's not running properly, that may not work. ;-)

---

### Post by karmila on 2011-04-01
You might want to check value for your default panel from gconf-editor. Run it from terminal and navigate to desktop > gnome  > session > required_components.
Make sure value for panel is gnome-panel.

---

### Post by Copper Bezel on 2011-04-01
Is gconf-editor installed by default? Why do I have weird memories of having to install it from the repos?

> Had I not had that available, what could I have done, short of killing power and restarting the computer?

Actually, Compiz and Metacity have a keystroke to launch a terminal by default - I think it's Ctrl+Alt+T (I've long since changed the keystroke on my machine.)

---

### Post by L a r r y on 2011-04-01
> **Copper Bezel said:**
> Is gconf-editor installed by default? Why do I have weird memories of having to install it from the repos?



Actually, Compiz and Metacity have a keystroke to launch a terminal by default - I think it's Ctrl+Alt+T (I've long since changed the keystroke on my machine.)

You are correct, I can bring up Terminal using Ctrl+Alt+T. 

I shall respond to each of these great posts with whether the suggestion works for me, or not.  This will be a very useful thread for future Ubuntu'ers.  Thanks everyone!

---

### Post by L a r r y on 2011-04-01
> **karmila said:**
> You might want to check value for your default panel from gconf-editor. Run it from terminal and navigate to desktop > gnome  > session > required_components.
Make sure value for panel is gnome-panel.

No such file or directory:
~/Desktop/gnome
~/Desktop/.gnome
~/gnome
~/.gnome/session
~/Files/Desktop/gnome
~/Files/Desktop/.gnome
(~/Files/Desktop is my Desktop location)
I will have to report back when I have the panels up.

In my case, I have created a Files directory in my Home folder and moved my Desktop and Documents there, just so I don't have to deal with all the hidden folders in ~ when I want to see a .htaccess file or something.  Not every application follows me to my new location, by the way, so I have a Desktop folder at the old location as well.  It is Desktop in name only, however.

For my next setup I might leave the Desktop alone and move all the rest into my Files directory, just to avoid future confusion over two "Desktop"s.

---

### Post by L a r r y on 2011-04-01
> **Krytarik said:**
> Actually, the "Run Application" feature is provided by gnome-panel, and just like you said, if it's not running properly, that may not work. ;-)

You are correct.  There is no Alt+F2 Run dialog without panels.

---

### Post by L a r r y on 2011-04-01
> **patryk77 said:**
> In case you ever get stuck without the "Open in Terminal" mod:

Press Alt+f2. This should open the "Run Application" window, from where you can use commands like "gnome-terminal" or "killall gnome-panel" as suggested.

Alt+f1 might also open the menu, though it may not work if gnome-panel isn't running properly.

There is no Alt+F1 or Alt+F2 available without panels.  Thanks for the keyboard tips though -- they would be handy under normal conditions.

---

### Post by safarin on 2011-04-01
> **L a r r y said:**
> You are correct.  There is no Alt+F2 Run dialog without panels.

Maybe you could refer this

[[SOLVED] Disappearing panel icons ]("http://ubuntuforums.org/showthread.php?t=1716534")

---

### Post by L a r r y on 2011-04-01
Cbowman57 said:  A lot of times "killall gnome-panel" is all that is needed to respawn the panel. Try that & see if it does the trick, if not there might be a more serious problem.
__________________
Chuck 
> **Krytarik said:**
> To restart "gnome-panel" you can run this command, it actually kills it, but it auto-respawns right after that:```
killall gnome-panel
```You could also create a launcher for it, located at your desktop.

Greetings.

This turned the panels back on, so I will create a shortcut for killall gnome-panel on my Desktop.  Thanks to one and all for a very thought-out discussion.

May I add, back when I indicated there was no such file or directory, evidently the editor in question is not in by default, therefore my results.

Thank you!

---

### Post by Copper Bezel on 2011-04-01
Yeah, you might have to install gconf-editor like 

```
sudo apt-get install gconf-editor
```

But more importantly, the path to that setting isn't to a file or directory on your hard drive, but to a setting within gconf-editor. If it's not installed, install it, then run it, and you'll see what he meant. Then we can check that Gnome Panel is actually set up to launch at startup like it ought to be.

---

### Post by Krytarik on 2011-04-01
> **Copper Bezel said:**
> Is gconf-editor installed by default? Why do I have weird memories of having to install it from the repos?
Actually, gconf-editor is installed by default, but its menu item is also disabled by default. ;-)

---

### Post by Copper Bezel on 2011-04-01
Ah! I see. = )

---

### Post by Krytarik on 2011-04-01
> **Copper Bezel said:**
> But more importantly, the path to that setting isn't to a file or directory on your hard drive, but to a setting within gconf-editor.
Actually, it is, almost. ;-) But all those gconf-paths start at "~/.gconf" and end up in "%gconf.xml" at the lowest level.

---

### Post by Copper Bezel on 2011-04-01
Yeah, I'd kind of wondered if it all corresponded to a directory tree structure hidden somewhere. Cool. = )

---

