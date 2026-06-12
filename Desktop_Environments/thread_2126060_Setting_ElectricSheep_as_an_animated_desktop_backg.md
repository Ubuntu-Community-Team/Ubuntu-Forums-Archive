---
title: "Setting ElectricSheep as an animated desktop background"
date: 2013-03-15
forum: Desktop Environments
---

### Post by Koro76 on 2013-03-15
On Ubuntu 12.04 LTS, I have already imported electricsheep into xscreensaver, but am having a difficult time finding a way to set it up as my desktop background. Should I use xwinwrap? If so, how?

---

### Post by madinc on 2013-03-15
i dont have xwinwrap installed but you can try something like this:
```
xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /your/screensaver/directory/here -root -window-id WID
```

---

### Post by Koro76 on 2013-03-15
I don't currently have xwinwrap. I was wondering if it would be easier to do what I want with it.

---

### Post by madinc on 2013-03-15
> **Koro76 said:**
> I don't currently have xwinwrap. I was wondering if it would be easier to do what I want with it.

i think its easier but thats just my opinion if you do take the xwinwrap route you can also have videos  looping as background not only screensavers.

---

### Post by Koro76 on 2013-03-15
I'm in the middle of looking for the screensaver directory, having already installed xwinwrap. I'll get back to you if it works or not. ere 

Maybe you can shorten my search? I used terminal to install it. Where does it normally stash the app data in the file structure?

---

### Post by Koro76 on 2013-03-15
Found it. I'm using Shantz's updated xwinwrap for improved functionality. I put in what you said and here's what it fed me:

```
xwinwrap v0.3- Modified by Shantanu Goel. Visit http://tech.shantanugoel.com for updates, queries and feature requests

Usage: xwinwrap [-g {w}x{h}+{x}+{y}] [-ni] [-argb] [-fs] [-s] [-st] [-sp] [-a] [-b] [-nf] [-o OPACITY] [-sh SHAPE] [-ov]-- COMMAND ARG1...
Options:
             -g      - Specify Geometry (w=width, h=height, x=x-coord, y=y-coord. ex: -g 640x480+100+100)
             -ni     - Ignore Input
             -d      - Desktop Window Hack. Provide name of the "Desktop" window as parameter             -argb   - RGB
             -fs     - Full Screen
             -s      - Sticky
             -st     - Skip Taskbar
             -sp     - Skip Pager
             -a      - Above
             -b      - Below
             -nf     - No Focus
             -o      - Opacity value between 0 to 1 (ex: -o 0.20)
             -sh     - Shape of window (choose between rectangle, circle or triangle. Default is rectangle)
             -ov     - Set override_redirect flag (For seamless desktop background integration in non-fullscreenmode)
             -debug  - Enable debug messages



```

---

### Post by madinc on 2013-03-15
> **Koro76 said:**
> Where does it normally stash the app data in the file structure?

sorry but i don't know:confused:

did you put the screensaver directory?

---

### Post by Koro76 on 2013-03-15
Yes, in my case it was simply /usr/bin/electricsheep

---

### Post by madinc on 2013-03-15
> **Koro76 said:**
> Yes, in my case it was simply /usr/bin/electricsheep

than that should have worked give me the link  you used i will give it a try.

---

### Post by Koro76 on 2013-03-15
[http://tech.shantanugoel.com/2008/09/03/shantz-xwinwrap.html](http://tech.shantanugoel.com/2008/09/03/shantz-xwinwrap.html)

Should I tr[FONT=monospace][COLOR=#555555]*y *[/COLOR][/FONT]> [COLOR=#555555][FONT=monospace]*xwinwrap -ov -fs -- /usr/bin/electricsheep -root -window-id WID*[/FONT][/COLOR]* ?*

Would you care to try it with electricsheep?

---

### Post by madinc on 2013-03-15
> **Koro76 said:**
> Should I tr[FONT=monospace][COLOR=#555555]*y *[/COLOR][/FONT]* ?*

the code i gave works for me with glmatrix

> **Koro76 said:**
> Would you care to try it with electricsheep?

is it in the repos? if not give me the link.

---

### Post by Koro76 on 2013-03-15
These are the instructions I followed. 

[http://wiki.freegeekvancouver.org/article/Installing_Electric_Sheep](http://wiki.freegeekvancouver.org/article/Installing_Electric_Sheep)

Also, I tried it with glmatrix as well, and it seems to work with that, but not elecrticsheep.

Also, you might need to edit your command, as when I use it, if I click on the desktop window, all of my taskbars and the launcher vanish. They are recoverable with a little fanangling, but they shouldn't get covered in the first place.

---

### Post by madinc on 2013-03-15
> **Koro76 said:**
> These are the instructions I followed. 

[http://wiki.freegeekvancouver.org/article/Installing_Electric_Sheep](http://wiki.freegeekvancouver.org/article/Installing_Electric_Sheep)

i didn't follow those instructions it is in the repos just did a apt-get install and was done it works with the code i gave but you must remove the -root option.
```
xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/bin/electricsheep -window-id WID
```

---

### Post by Koro76 on 2013-03-15
I entered your new code and terminal acts as though it opened electricsheep, providing me with the normal

```
[avi @ 0x839e9a0] max_analyze_duration reached
```

But, no new window opens.

---

### Post by madinc on 2013-03-15
> **Koro76 said:**
> Also, you might need to edit your command, as when I use it, if I click on the desktop window, all of my taskbars and the launcher vanish. They are recoverable with a little fanangling, but they shouldn't get covered in the first place.

working perfectly here see images:

glmatrixblue: [https://dl.dropbox.com/u/2078155/Screenshot%20from%202013-03-16%2003%3A40%3A51.png](https://dl.dropbox.com/u/2078155/Screenshot%20from%202013-03-16%2003%3A40%3A51.png)

electricsheep: [https://dl.dropbox.com/u/2078155/Screenshot%20from%202013-03-16%2003%3A55%3A54.png](https://dl.dropbox.com/u/2078155/Screenshot%20from%202013-03-16%2003%3A55%3A54.png)

---

### Post by Koro76 on 2013-03-15
Not sure what I'm doing wrong then. I'm literally copy and pasting your command.

Removed xscreensaver and restored gnome-screensaver. Same thing is happening. Any ideas?

I wouldn't be opposed to remote desktop.

---

### Post by madinc on 2013-03-15
> **Koro76 said:**
> Not sure what I'm doing wrong then. I'm literally copy and pasting your command.

like i wrote before i did not follow those instructions you did so i suggest you revert them because you don't need them and maybe they are getting in the way.

these are the steps i took:

1-install xwinwrap from the link you gave me.
2-```
sudo apt-get install electricsheep
```
3-open terminal and type ```
xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/bin/electricsheep -root -window-id WID
``` gave error.
4-open terminal and type ```
xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/bin/electricsheep -window-id WID
``` works perfectly.

> **Koro76 said:**
> I'll redo all these steps right now. Fingers crossed.

good luck:P

---

### Post by Koro76 on 2013-03-15
I'll redo all these steps right now. Fingers crossed.

Same thing again. It acts like electricsheep is running, but there is no background. Up for remote desktop?

Apps like teamviewer. 

[http://www.teamviewer.com/en/download/linux.aspx](http://www.teamviewer.com/en/download/linux.aspx)

It would basically let you do stuff on my computer from yours.

---

### Post by madinc on 2013-03-15
what do you mean with remote desktop??:confused:

i wouldn't know what to do and you should not let anybody access your pc its not safe.

---

### Post by Koro76 on 2013-03-15
Theres override security built in. Besides I don't keep any personal info on here, and if all else fails I can power off.

Is there some kind of command you've done in the past to disable the desktop background window so you can apply another window over it?

Maybe you can double check? Make sure i did it right?

```
sudo apt-get remove xscreensaver
```

followed by

```
sudo apt-get install gnome-screensaver
```

---

### Post by madinc on 2013-03-15
> **Koro76 said:**
> Theres override security built in. Besides I don't keep any personal info on here, and if all else fails I can power off.

i really would like to help you but even if i had access to your pc i wouldn't know what to do. that is if you have undone the steps you followed.

> **Koro76 said:**
> Maybe you can double check? Make sure i did it right?

tell me which steps you did to undo.

> **Koro76 said:**
> ```
sudo apt-get remove xscreensaver
```

followed by

```
sudo apt-get install gnome-screensaver
```

try this:

```
sudo apt-get remove --purge xscreensaver xscreensaver-gl-extra xscreensaver-data-extra 
```

---

### Post by Koro76 on 2013-03-15
I just discovered that my normal desktop is exhibiting the same traits as the glmatrix window did, hiding my task bars and launcher as long as the electricsheep terminal is running that doesn't seem like it does anything.

Did it, still no improvement when I try to use that command.

Just checked. There was one there. Should I delete that too?

---

### Post by madinc on 2013-03-15
> **Koro76 said:**
> Did it, still no improvement when I try to use that command.

do you have a .xscreensaver file in home directory hidden?

> **Koro76 said:**
> Just checked. There was one there. Should I delete that too?

yes

---

### Post by Koro76 on 2013-03-16
Deleted it (and a second one I found.), and it still does the same thing.

---

### Post by madinc on 2013-03-16
> **Koro76 said:**
> Deleted it (and a second one I found.), and it still does the same thing.

can you try after logout or reboot?

---

### Post by Koro76 on 2013-03-16
I opened a second instance of electricsheep and it auto-detected the first instance. (the one that runs without actually appearing as a background) Not sure if that helps.

---

### Post by madinc on 2013-03-16
> **Koro76 said:**
> I opened a second instance of electricsheep and it auto-detected the first instance. (the one that runs without actually appearing as a background) Not sure if that helps.

i really don't know it should be working with this code:
```
xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/bin/electricsheep -window-id WID
```

---

### Post by Koro76 on 2013-03-16
Logged out and rebooted. Same problem.

---

### Post by madinc on 2013-03-16
i'm using ubuntu 12.10 amd64 maybe there is something different:confused:

---

### Post by Koro76 on 2013-03-16
I'm on 12.04 LTS on 32 bit.

What I don't understand is, that if glmatrix worked, why doesn't electricsheep?
Should I try moving electricsheep to usr/lib?

I didn't think so. I'm open to anything you want me to try, though.

---

### Post by madinc on 2013-03-16
> **Koro76 said:**
> I'm on 12.04 LTS on 32 bit.

i have a 32bit notebook but it has puppy linux there.

> **Koro76 said:**
> What I don't understand is, that if glmatrix worked, why doesn't electricsheep?
Should I try moving electricsheep to usr/lib?

that would make no difference

> **Koro76 said:**
> I didn't think so. I'm open to anything you want me to try, though.

what version of electricsheep do you have since we both have the same version of xwinwrap?

> **Koro76 said:**
> I used 

```
sudo apt-get install electricsheep
```

So we should have the same version.

i'm using a newer version of ubuntu so they can be different.

---

### Post by Koro76 on 2013-03-16
I used 

```
sudo apt-get install electricsheep
```

So we should have the same version.

---

### Post by madinc on 2013-03-16
mine is 2.7~b12+svn20091224-1ubuntu3

---

### Post by Koro76 on 2013-03-16
I ran a search through my file structure, and i found electricsheep in /usr/bin AND ElectricSheep in /usr/share/applications/screensavers Do you have the second one?

Mine is v2.7b12 also.

---

### Post by madinc on 2013-03-16
> **Koro76 said:**
> I ran a search through my file structure, and i found electricsheep in /usr/bin AND ElectricSheep in /usr/share/applications/screensavers Do you have the second one?

yes i have both plus /usr/bin/electricsheep-preferences

---

### Post by Koro76 on 2013-03-16
Everything appears to be the same, then.

Nothing even opens If I try opening it alone. I doubt it would do anything with your command, either.

What would you suggest?

Still nothing.

Nothing at all outside of terminal.

---

### Post by madinc on 2013-03-16
try using the one in /usr/share/applications/screensavers

> **Koro76 said:**
> Nothing even opens If I try opening it alone. I doubt it would do anything with your command, either.

try with different code.

try in a small window:

```
xwinwrap -ov -g 400x400+400+200 -- /usr/bin/electricsheep -window-id WID
```

nothing show up??

whats the terminal output?

mine  is:
```
madinc@Madinc-1:~$ xwinwrap -ov -g 400x400+400+200 -- /usr/bin/electricsheep -window-id WID
[avi @ 0x6be080] max_analyze_duration reached
[avi @ 0x6be080] max_analyze_duration reached
[avi @ 0x6be080] max_analyze_duration reached
[avi @ 0x6be080] max_analyze_duration reached
[avi @ 0x6be080] max_analyze_duration reached
[avi @ 0x6be080] max_analyze_duration reached
```

---

### Post by Koro76 on 2013-03-16
Mine is the same.

```
jeff@jeff:~$ xwinwrap -ov -g 400x400+400+200 -- /usr/bin/electricsheep -window-id WID
[avi @ 0x99dd9a0] max_analyze_duration reached
[avi @ 0x99dd9a0] max_analyze_duration reached
[avi @ 0x99dd9a0] max_analyze_duration reached

```

Yes, it worked with glmatrix.

---

### Post by madinc on 2013-03-16
> **Koro76 said:**
> Mine is the same.

so why does my work and yours don't did you try with other screensavers it did work with glmatrix right?

your output is different mine is 0x6be080 and yours is 0x99dd9a0 this can be the problem but if it is i don't know how to fix it.

> **Koro76 said:**
> Know anyone who does?

you can try contact the dev that made the app but i don't know if he will reply or you can leave this thread open and wait for somebody that can help you better than i can because i'm not a linux pro:)

---

### Post by Koro76 on 2013-03-16
Seems that the last update to electricsheep was in 2009? so contacting the dev is unlikely.

---

### Post by madinc on 2013-03-16
then i think you better wait for somebody here or look for similar threads and if you are like me just keep trying till it works.

one of my friends has 12.04 32bit i will ask him to try it out to see if he has the same problem i will ask him tomorrow or the day after so remember to check back.

do you have the compiz wallpaper plugin?

---

### Post by Koro76 on 2013-03-16
I'll keep this thread open in a tab.

No, I don't.

---

### Post by Koro76 on 2013-03-17
Bumping the thread in an attempt to get further assistance.

---

### Post by zombifier25 on 2013-03-18
If you're using Compiz, open ccsm (install compizconfig-setting-manager), open the Windows rule plugin, and add "name=xv" to all of the categories except for Above and Non-ARGB visuals.

It worked for me, so try it.

---

### Post by Koro76 on 2013-03-19
You sure that's the solution? Upon enabling the plugin (after entering name=xv into the fields), compiz promptly crashed, so I disabled it again.

Perhaps the quotation marks are nessicary?

---

### Post by Koro76 on 2013-03-20
Bumping for continued help

---

### Post by zombifier25 on 2013-03-21
> **Koro76 said:**
> You sure that's the solution? Upon enabling the plugin (after entering name=xv into the fields), compiz promptly crashed, so I disabled it again.

Perhaps the quotation marks are nessicary?

The crashing is to be expected everytime you enable a Compiz plugin. If it doesn't start again, simply restart the machine.

Once done, start electricsheep from the terminal and see if it works.

---

### Post by JOHNNYG713 on 2013-03-21
IMHO The new Compiz is waaay to unstable to use for drawing an an animated back ground ! I use xwinrap, just pull out a sheep you like from .electricsheep in your home folder, put it some place like Videos, start xwinrap and boom shakalka, animated back ground, no compiz crash ! they REALLY should have concentrated more on getting compiz right, before they went and totally screwed the pooch ! IMHO

---

### Post by Koro76 on 2013-03-21
Here's the breakdown of where I am currently. I want the changing version of electricsheep as my desktop background.

```
[COLOR=#000000][FONT=Ubuntu Mono]xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/bin/electricsheep -window-id WID[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]
only gives me the operation of electricsheep within terminal, but no visible window.

Changing the  settings in the window rule plugin in comiz to "name=xv" makes electricsheep run fullscreen out of terminal, but does not make it act as a desktop background.

Trying both methods together yields the same results as the command by itself.

The same command running glmatrix works just fine, but it won't run electricsheep.

---

### Post by zombifier25 on 2013-03-22
So it ran fullscreen, but is the window below other windows? It should be, because the window is added to the "Always Below" rule.

If not, then you're out of luck, since it seems that everyone's electricsheep works, but yours don't. As a last resort, try purging electricsheep and install it again.

---

### Post by Koro76 on 2013-03-24
Perhaps my electricsheep window is running below my desktop background? Is there any way to remove my desktop background layer to check?

---

### Post by Koro76 on 2013-03-28
bumping for more assistance.

---

### Post by Diemex on 2013-04-05
this one worked for me:
    ```
xwinwrap -ov -fs -b -- /usr/bin/electricsheep -window-id WID
```
only problem is that I have conky and that seems to draw to the real wallpaper, so the area which conky draws to shows the wallpaper as background and the area around is from electricsheep.
I'm not bothering any further with it though because it uses 40% of my cpu...

---

### Post by jeremiahjal on 2013-06-21
Here is what I'm using.. works very well so far

Code:
```

xwinwrap -ni -o 0.5 -s -st -sp -b -nf -g 1440x900 -- /usr/bin/electricsheep -window-id WID

```

---

