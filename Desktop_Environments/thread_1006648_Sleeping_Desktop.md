---
title: "Sleeping Desktop"
date: 2008-12-09
forum: Desktop Environments
---

### Post by acmeinc on 2008-12-09
I am having problems keeping my desktop from sleeping.  I try to watch streaming videos and such from the internet (through my browser) and about 10 minutes in my desktop goes to sleep.  Howeverif I watch from Totem Movie Player my screen does not sleep(go black).  My desktop seems to go to sleep on all applications after 10 minutes, except for Totem.  

My Power Management Preferences are set to Never on both Actions and Display.  Is there more setup info I should look for?  Please let me know how I can fix this, because it is quite annoying to get up and move my mouse every 10 minutes :(

---

### Post by mali2297 on 2008-12-09
This advice might be outdated, but you could try editing xorg.conf...

Open the file from a terminal with the command
```

gksudo mousepad /etc/X11/xorg.conf

``` 
Then append the lines
```

Section "ServerFlags"
        Option          "blank time" "0"
        Option          "standby time" "0"
        Option          "suspend time" "0"
        Option          "off time" "0"
EndSection

```
last in the file. Save, quit and restart.

---

### Post by acmeinc on 2008-12-10
Breaks my config file :(  OS won't load.

---

### Post by kerry_s on 2008-12-10
> **mali2297 said:**
> This advice might be outdated, but you could try editing xorg.conf...

Open the file from a terminal with the command
```

gksudo mousepad /etc/X11/xorg.conf

``` 
Then append the lines
```

Section "ServerFlags"
        Option          "blank time" "0"
        Option          "standby time" "0"
        Option          "suspend time" "0"
        Option          "off time" "0"
EndSection

```
last in the file. Save, quit and restart.

close but it's:

```
Section "ServerFlags"
        Option	"BlankTime"	"0"
        Option	"StandbyTime"	"0"
        Option	"SuspendTime"	"0"
        Option	"OffTime"	"0"
EndSection

```

---

### Post by kerry_s on 2008-12-10
> **acmeinc said:**
> Breaks my config file :(  OS won't load.

any error?
did you put it on the bottom of xorg.conf and leave 1 empty line on the end of the file?

mine look like this:

---

### Post by mali2297 on 2008-12-10
> **acmeinc said:**
> Breaks my config file :(  OS won't load.

You should still be able to reach a text interface. From there, open the file with **nano**:
```

sudo nano /etc/X11/xorg.conf

```
See if you can correct the changes. Otherwise just remove the appended lines. Save (ctrl+o) and quit (ctrl+x).

---

### Post by mali2297 on 2008-12-10
> **kerry_s said:**
> close but it's:

```
Section "ServerFlags"
        Option	"BlankTime"	"0"
        Option	"StandbyTime"	"0"
        Option	"SuspendTime"	"0"
        Option	"OffTime"	"0"
EndSection

```

Both should work, but your text is in better accordance to the man page.

---

### Post by acmeinc on 2008-12-17
thanks for the help, I'll implement this when I get home from work and let you konw if this fixes the problem.  

On a lighter note, here is my problem in comic form!  And look they suggest a mouse moving script :)

[http://xkcd.com/196/](http://xkcd.com/196/)

---

### Post by kerry_s on 2008-12-17
> **acmeinc said:**
> thanks for the help, I'll implement this when I get home from work and let you konw if this fixes the problem.  

On a lighter note, here is my problem in comic form!  And look they suggest a mouse moving script :)

[http://xkcd.com/196/](http://xkcd.com/196/)

:lolflag:
always a option.

---

### Post by acmeinc on 2009-03-16
Sorry for the delay, however, this did not work.

```

Section "ServerFlags"
        Option	"BlankTime"	"0"
        Option	"StandbyTime"	"0"
        Option	"SuspendTime"	"0"
        Option	"OffTime"	"0"
EndSection

```

Also, in case you think im crazy, I attached the below screenshot to prove I have the power manager set up correctly :P

[IMG]http://pwnspeak.com/ss.png[/IMG]

Any other suggestions?

---

### Post by acmeinc on 2009-03-16
And I'm an idiot and overlooked my xfce settings manager and assumed Power Management took all precendence.  Apparently 'Blank Screen' was selected, under the Screensave tab, to go active after, whadya know, 10 minutes.  :)  I'm not very window savvy, I use mostly the terminal to get around.  Thanks for the good info though!

---

