---
title: "Screensaver appears when using gamepad"
date: 2010-12-27
forum: Gaming &amp; Leisure
---

### Post by Howy on 2010-12-27
So, I have set up WINE pretty nicely, and I enjoy playing NFS MW in it. Only thing that would make it better? If the screensaver didn't turn on. I'm running WINE in windowed mode.
At the given time, the screensaver turns on because I use a gamepad. I know that this is caused by that X doesn't count its activity for deciding when to turn on the screensaver. So, is there any way to avoid the screensaver while using the gamepad?

---

### Post by thatguruguy on 2010-12-27
This is a Wine question, not a gaming question. There is a forum specifically for questions regarding Wine. That being said, you'll need to set up some scripts for your games.

The first thing you'll need to do is identify your desktop.  To do so,  open a terminal on an otherwise blank desktop and enter the following  code:
 ```
xwininfo
```You will receive the following message:
```
Please select the window about which you would like information by clicking the mouse in that window. 

```Simply click on an empty space on your desktop.  A bunch of text  should appear in your terminal.  You want the first line, which will say  something like this:
```
xwininfo: Window id: 0x2200003 "Desktop"
```Then, you'll need to create some scripts to launch your games.  For example, I have a script for halo:
```
 #!/bin/sh
xdg-screensaver suspend 0x2200003
sh -c "cd /home/john/.wine/drive_c/Program\ Files/Microsoft\ Games/Halo && ./halo.exe"
xdg-screensaver resume 0x2200003
```

Use the script to launch the game, and it will suspend the screensaver while playing the game, and then turn it back on when you exit the game.

---

### Post by MichaelBurns on 2010-12-28
> **thatguruguy said:**
> This is a Wine question, not a gaming question. There is a forum specifically for questions regarding Wine.I have this same problem as described by the OP, except replace wine with either zsnes or fceu, two presumably completely independent programs, and also presumably completely independent of wine.  (I don't even have wine installed on my system.)  I was expecting this to be a xwindow question.  Are you saying that the solution that you describe won't work for me, and I should start a new thread for the zsnes gamepad screensaver problem and another new thread for the fceu gamepad screensaver problem?

---

### Post by thatguruguy on 2010-12-28
> **MichaelBurns said:**
> I have this same problem as described by the OP, except replace wine with either zsnes or fceu, two presumably completely independent programs, and also presumably completely independent of wine.  (I don't even have wine installed on my system.)  I was expecting this to be a xwindow question.  Are you saying that the solution that you describe won't work for me, and I should start a new thread for the zsnes gamepad screensaver problem and another new thread for the fceu gamepad screensaver problem?

Well, see, here's the thing. In a sticky entitled "**Guidelines in Gaming & Leisure forum**" which is available right [here]("http://ubuntuforums.org/showthread.php?t=359869"), it says (in big red letters), "[B][COLOR=Red]Wine and Windows related games on linux or related to wine in any kind, please post them [in our wine forum]("http://ubuntuforums.org/forumdisplay.php?f=313").
If not they will be deleted or closed.[/COLOR][/B][COLOR=Red][COLOR=Black]"

I was, however, nice enough to answer the question, despite the fact that the OP apparently didn't read the guidelines. Moreover, you apparently didn't read the guidelines, either, or you presumably wouldn't have felt the need to be snarky.

Is there a separate forum for emulators?

And to answer your question, yes, the solution will work for you. I'll let you figure out how.
[/COLOR][/COLOR]

---

### Post by Perfect Storm on 2010-12-28
Thread closed.

---

