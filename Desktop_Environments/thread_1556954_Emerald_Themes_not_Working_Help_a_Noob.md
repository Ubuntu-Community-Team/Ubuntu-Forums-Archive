---
title: "Emerald Themes not Working/ Help a Noob"
date: 2010-08-20
forum: Desktop Environments
---

### Post by cro_409 on 2010-08-20
Hey Everyone

I know there are some other threads with issues regarding Emerald, but some of those had open questions but no replies for over four weeks.

I have installed Emerald Theme Manager 0.7.2.
I have imported two different themes from the internet, I believe they are both "Gnome" themes, I was told they would work on Emerald.
I also have CompizConfiguration System Manager installed.

Clicking on the imported themes does nothing, nor does Alt-F2 "emerald --replace" or Terminal "emerald --replace"

I have double checked to make sure Windows Decorator is enabled/checked, but still nothing happens. I have tried unchecking the Window Decorator, but nothing happens. 

When I say nothing, I mean NOTHING, lol. I hit enter on Alt-F2, it closes, and nothing happens. I hit enter on Terminal, and no code or script except the prefix that means its ready for the next command. No crashes, screen blinks, or applications opening. 

What am I missing? If I could have a step-by-step walkthrough I would be immensely appreciative. Write carefully especially with any code, I am still used to never typing commands in Windows, but already love Ubuntu way more than Windows despite my many beginner problems.

---

### Post by stinkeye on 2010-08-20
Emerald themes only change the title bar and border, and don't work 
with Metacity as your window manager.
Download Emerald themes from here...[http://gnome-look.org/index.php?xcontentmode=103&PHPSESSID=1ad4bda77aae1804757ea5b8d23c092b]("http://gnome-look.org/index.php?xcontentmode=103&PHPSESSID=1ad4bda77aae1804757ea5b8d23c092b")


Import them into emerald theme manager.
Select the one you want and Alt+F2
```
emerald --replace
```


To change your window decorator back
```
gtk-window-decorator --replace
```


Use fusion-icon to easily change your window manager and window decorator.
To install from the terminal
```
sudo apt-get install fusion-icon
```
Find in menu > system tools > compiz fusion icon
Loads into the notification area.


If you have the required theme engine as shown in Emerald theme manager it should work.

---

### Post by snip3r8 on 2010-08-20
I added ```
emerald --replace
``` to my start up applications,is there a better way to get emerald on boot?

---

### Post by nick_goodfate on 2010-08-20
> **snip3r8 said:**
> I added ```
emerald --replace
``` to my start up applications,is there a better way to get emerald on boot?

if you have compiz configuration manager go to window decoration and replace the default command with "emerald --replace".

---

### Post by realzippy on 2010-08-20
..you run compiz?Then you can place the command in *CCSM*,in
"Window Decorations"...


nick_goodfate was faster...

---

### Post by snip3r8 on 2010-08-20
> **nick_goodfate said:**
> if you have compiz configuration manager go to window decoration and replace the default command with "emerald --replace".

will all the other stuff in there effect my emerald settings?

---

### Post by nick_goodfate on 2010-08-20
i think not. But you can try, at the right of every setting there is a reset to default button... You can change the settings of your emerald theme through emerald , in case you don't know ...

---

### Post by snip3r8 on 2010-08-20
> **nick_goodfate said:**
> i think not. But you can try, at the right of every setting there is a reset to default button... You can change the settings of your emerald theme through emerald , in case you don't know ...
 
 I didnt want it to affect my emerald settings,i spent hours on those,by the way just played with it and it doesn't affect emerald settings ,I'm not seeing any bright pink shadows,but if something happens and it goes back to default window decorator,someone's going to think I've lost it.

---

### Post by stinkeye on 2010-08-20
If you use fusion-icon to switch window decorators it automatically changes 
the command in the CCSM > window decoration plugin to either
**gtk-window-decorator --replace**
or
**emerald --replace**
according to which window decorator you choose,
so there is no need to to put anything in startup applications.
Compiz will load the last window decorator you used.


I add fusion-icon to startup applications for easy access to CCSM and the other right click settings.
If you add it to startup applications use the command
```
fusion-icon -n
```
The -n tells it to not start a window manager, otherwise the window manager is loaded twice and can cause some startup programs to crash.(eg gnome-do)

---

