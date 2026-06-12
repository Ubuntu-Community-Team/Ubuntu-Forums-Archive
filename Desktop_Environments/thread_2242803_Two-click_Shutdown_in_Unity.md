---
title: "Two-click Shutdown in Unity?"
date: 2014-09-04
forum: Desktop Environments
---

### Post by 2CV67 on 2014-09-04
After a week's work, I am reasonably satisfied with my new PC with 14.04.1, even with Unity...

One little irritation is the shut-down procedure.

After clicking the Shutdown icon at top right of the panel, I need to find & click the Shut Down item in the drop-down list which includes lots of other items, before getting to the Restart / Shutdown window which actually does what I wanted in the first place.

I would like to simplify the frequently-used Restart / Shutdown procedure to a 2-click sequence, which I think is ideal for this action.

It was easy in Xfce (added big red Stop button to panel which brought up Restart / Shutdown window immediately).

Is it possible in Unity?

Thanks!

---

### Post by hai3 on 2014-09-04
> **2CV67 said:**
> After a week's work, I am reasonably satisfied with my new PC with 14.04.1, even with Unity...

One little irritation is the shut-down procedure.

After clicking the Shutdown icon at top right of the panel, I need to find & click the Shut Down item in the drop-down list which includes lots of other items, before getting to the Restart / Shutdown window which actually does what I wanted in the first place.

I would like to simplify the frequently-used Restart / Shutdown procedure to a 2-click sequence, which I think is ideal for this action.

It was easy in Xfce (added big red Stop button to panel which brought up Restart / Shutdown window immediately).

Is it possible in Unity?

Thanks!

Yes yes yes! You can put a launcher on Cairodock, tell it to use shutdown command.
But it will be executed when you single-click...

---

### Post by mcvries on 2014-09-04
This is what i used:
[http://itsfoss.com/shutdown-dialogue-box-ubuntu-1404/](http://itsfoss.com/shutdown-dialogue-box-ubuntu-1404/)

Now, when i click in the top right corner, i can choose between pause, shutdown, reboot and it gets executed immediatly.

---

### Post by westie457 on 2014-09-04
In 14.04 with Unity, tapping the power button of the computer should bring up a panel with 4 icons in it. They should be labelled 'suspend', 'restart', 'cancel' and 'shutdown'.
Am using 12.04 at the moment which has similar behaviour.

---

### Post by CantankRus on 2014-09-04
You can suppress confirmation dialogues by running this command
```
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown true
```

---

### Post by 2CV67 on 2014-09-04
Thanks, guys, for those suggestion!

CairoDock looks amusing, but is a bigger step than I want to take today - I will maybe look at it in my spare 14.04.1 drive soon.

I had been using the Power-Button-Tap on my Netbook, without realizing it would also work on a Desktop.
I tried it & it did work.
But it means groping under the desk (it's a DeskBottom really) which is less than slick.

The suggestion:
```
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown true
```
(from both Mcvries & CantankRus) looked interesting, although it still involves finding a line of small text in a drop-down list (I would rather hit a big coloured button!).

I remembered "com.canonical.indicator..." from recent dealings with dconf Editor (setting panel clock format) so looked in dconf Editor to see if I could do the job by GUI, but apparently not?

So I did it by terminal.
And it works immediately. :)

This is a decent solution for me, though I am still interested in any other ideas.

Note that after suppressing dialogs this way, the Power-Button-Tap method produces instant shutdown - a one-click method!
Although I will not be using that normally, I would be interested to know if that is a legitimate & peaceful shutdown method, as opposed to the Power-Button-Hold-Down which is for emergencies only.
I suppose it is OK as it did not induce automatic restart on power-on.

---

### Post by CantankRus on 2014-09-04
You could create a shut down button on the launcher.

In the terminal run
```
gedit ~/.local/share/applications/exit.desktop
```
Copy a paste in the following and save.
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=gnome-session-quit --power-off
Name=Exit
Icon=system-shutdown
```

In the file browser go to **~/.local/share/applications** and drag and drop **exit.desktop** to the launcher. 

When **not** suppressing confirmation
```
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown **false**
```
you will see as in pic.


When suppressing confirmation
```
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown **true**
```
it will be instant.

---

### Post by 2CV67 on 2014-09-05
YES!!!

That is PRECISELY what I have been looking for (without suppression of confirmation).

I now have a big red button at top left.
Clicking that brings up big simple option buttons for Lock, Suspend, Restart & Shutdown (I will never use Lock or Suspend on this Desktop).

So - 2 clicks to exit, with no squinting at small text lists.

Thank you VERY much, CantankRus! :D

---

### Post by CantankRus on 2014-09-05
> **2CV67 said:**
> YES!!!

That is PRECISELY what I have been looking for (without suppression of confirmation).

I now have a big red button at top left.
Clicking that brings up big simple option buttons for Lock, Suspend, Restart & Shutdown (I will never use Lock or Suspend on this Desktop).

So - 2 clicks to exit, with no squinting at small text lists.

Thank you VERY much, CantankRus! :D

No problem.
Look at the man page for gnome-session-quit,
```
man gnome-session-quit
```

eg
```
gnome-session-quit --reboot
```
gives you a restart shutdown option.

You can also add a quicklist item for logout
eg
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=gnome-session-quit [COLOR="#FF0000"]**--reboot**[/COLOR]
Name=Exit
Icon=system-shutdown

**Actions=[COLOR="#FF8C00"][B]logout**[/COLOR];

[Desktop Action [COLOR="#FF8C00"]**logout**[/COLOR]]
Name=Logout
Exec=gnome-session-quit --logout --no-prompt
OnlyShowIn=Unity;[/B]
```

Adapt for whatever suits you.

---

### Post by 2CV67 on 2014-09-05
Thanks!

I ended up using your first suggestion about button on the launcher, but with the --reboot option.

(I will use the old drop-down list for logout etc which I do rarely).

So finally I have:
- Big red button at top of Launcher.
- Clicking that brings up big simple Restart / Shutdown window.
- Clicking that produces the result with no further confirmation.

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=gnome-session-quit --reboot
Name=Exit
Icon=system-shutdown
```

I think that is near perfect.
Only a bit of colour to differentiate the Restart / Shutdown buttons would improve the ergonomics...

Really appreciated your help! :D

---

