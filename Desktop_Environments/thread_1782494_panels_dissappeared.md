---
title: "panels dissappeared"
date: 2011-06-14
forum: Desktop Environments
---

### Post by Shriner on 2011-06-14
Did a log out today. When I logged back in I had no panels. I cannot access them from the xfce settings manager either. When I click on "panel" nothing happens.

---

### Post by ivanovnegro on 2011-06-14
Type in a terminal:

```
xfce4-panel
```

Should restore it.

---

### Post by Shriner on 2011-06-14
Thank did it thanks....

---

### Post by Shriner on 2011-06-14
Opps...did it until I closed the terminal window

The command reports "~/Desktop$ xfce4-panel
(xfce4-mixer-plugin:2897): xfce4-mixer-plugin-DEBUG: mixer_plugin->track_label = 'Master'
"

It does not return to the prompt.

---

### Post by ivanovnegro on 2011-06-14
Ok, another thing, maybe better.
Press ALT+F2 and run the same command.

---

### Post by jerrrys on 2011-06-14
try 

sudo apt-get remove xfce4-panel

sudo apt-get install xfce4-panel

---

### Post by Shriner on 2011-06-14
> **ivanovnegro said:**
> Ok, another thing, maybe better.
Press ALT+F2 and run the same command.
It worked, but it didn't hold thru a restart. That was my fault. I didin't make sure that the "keep settings" was checked. So I proceeded to Jerry's suggestion.......

---

### Post by Shriner on 2011-06-14
> **jerrrys said:**
> try 

sudo apt-get remove xfce4-panel

sudo apt-get install xfce4-panel
This was a bit drastic for me. Upon completing this I restarted to see if it would hold thru a restart. It was then I noticed that I hadn't checked the "keep settings". 

My problem now is that I cannot access anything but FireFox and Thunderbird. My "system" and "Places" are gone. My desktop has been reset and the icons are larger and the background has changed. All of that I can repair if I can gain access to the "system" again. Right clicking on the desktop gives me no access.

I would bet now that when I was removing I should have said "no" when it asked if I wanted to remove the packages. But since that was the purpose of "remove" I said yes.....

---

### Post by ivanovnegro on 2011-06-14
> **Shriner said:**
> This was a bit drastic for me. Upon completing this I restarted to see if it would hold thru a restart. It was then I noticed that I hadn't checked the "keep settings". 

My problem now is that I cannot access anything but FireFox and Thunderbird. My "system" and "Places" are gone. My desktop has been reset and the icons are larger and the background has changed. All of that I can repair if I can gain access to the "system" again. Right clicking on the desktop gives me no access.

I would bet now that when I was removing I should have said "no" when it asked if I wanted to remove the packages. But since that was the purpose of "remove" I said yes.....

IMO it was a bad idea to remove the panel. If you had enabled the "keep settings" it should work from running "xfce4-panel" from the run command but not in a terminal, that was my fault.

Now you have to customize your desktop again, for the panel, right click on it, for the desktop icons, right click on desktop and settings.

---

### Post by jerrrys on 2011-06-14
thats why the remove and not --purge.

---

### Post by Shriner on 2011-06-14
> **ivanovnegro said:**
> IMO it was a bad idea to remove the panel. If you had enabled the "keep settings" it should work from running "xfce4-panel" from the run command but not in a terminal, that was my fault.

Now you have to customize your desktop again, for the panel, right click on it, for the desktop icons, right click on desktop and settings.

I agree with you, now I know better. If I right click on the panel I only get: properties, move, remove, add new items, customize. None of these let access anything that will let me recover.

---

### Post by Shriner on 2011-06-14
> **jerrrys said:**
> thats why the remove and not --purge.
Lesson learned. Any suggestions on how to regain access?

---

### Post by jerrrys on 2011-06-14
one minute

---

### Post by ivanovnegro on 2011-06-14
Did you also try adjust panel?

Edit: If you want to have the Firefox icon back, you have to add a new element, in this case a starter. If you want to move the new created starter icon, right click on it and choose "move", you can place it where you want.

---

### Post by jerrrys on 2011-06-14
try this in terminal or Alt F2

xfce4

and navigate to your applications folder

should be filesystem>user>share>applications

may have to use gksudo xfce4

---

### Post by Shriner on 2011-06-14
> **ivanovnegro said:**
> Did you also try adjust panel?

Edit: If you want to have the Firefox icon back, you have to add a new element, in this case a starter. If you want to move the new created starter icon, right click on it and choose "move", you can place it where you want.
I have FF and Thunderbird, but that it is all. The "System" and Places" are gone. With out "System" ( I believe that is what it was) and since right clicking on the desktop gives me now access to programs, I no access to even start a terminal window or anything else.

There is no adjust panel.

---

### Post by ivanovnegro on 2011-06-14
> **Shriner said:**
> I have FF and Thunderbird, but that it is all. The "System" and Places" are gone. With out "System" ( I believe that is what it was) and since right clicking on the desktop gives me now access to programs, I no access to even start a terminal window or anything else.

There is no adjust panel.

Do you mean the menu is not there anymore at the left?
If that is the case, right click on panel, add new item, select Xfce menu.
I hope I understand you well. :)

---

### Post by nzjethro on 2011-06-14
I had a similar issue which came about because Nautilus was running in the background. I shut down Nautilus and my XFCE panel came back. But it sounds like even if this was the case you've cooked it further!

If you have access to programmes, can you access ccsm, and bind some kind of keyboard shortcut to create a terminal? Then open the terminal and run the commands to restore your panels?

---

### Post by Shriner on 2011-06-14
> **ivanovnegro said:**
> Do you mean the menu is not there anymore at the left?
If that is the case, right click on panel, add new item, select Xfce menu.
I hope I understand you well. :)
Wish I could, but Xfce Menu does not appear under add new item.

---

### Post by Shriner on 2011-06-14
> **jerrrys said:**
> try this in terminal or Alt F2

xfce4

and navigate to your applications folder

should be filesystem>user>share>applications

may have to use gksudo xfce4

this appears to do nothing. The closest is alt-f2, run in terminal, gksudo xfce4
That opens a terminal window (without a prompt) but it dissappears before I can do anything.

---

### Post by Shriner on 2011-06-14
> **nzjethro said:**
> I had a similar issue which came about because Nautilus was running in the background. I shut down Nautilus and my XFCE panel came back. But it sounds like even if this was the case you've cooked it further!

If you have access to programmes, can you access ccsm, and bind some kind of keyboard shortcut to create a terminal? Then open the terminal and run the commands to restore your panels?
I have no access to programs. only the firefox and thunderbird on the panel.

---

### Post by Shriner on 2011-06-14
How do I determine if xfce is even running now?
Not just the panel?

---

### Post by jerrrys on 2011-06-14
sudo debconf xfce4-panel

this should restore it

---

### Post by Shriner on 2011-06-14
> **jerrrys said:**
> sudo debconf xfce4-panel

this should restore it
Nothing.

Used alt-f2 and nothing happened. using alt-f2 and run in terminal - a term window opens and closes. Doesn't even ask for root pwd.

---

### Post by jerrrys on 2011-06-14
alt f2  xfce4-terminal

try that

---

### Post by Shriner on 2011-06-14
> **jerrrys said:**
> alt f2  xfce4-terminal

try that
that gets me a terminal window

---

### Post by jerrrys on 2011-06-14
now that your in terminal enter

sudo debconf xfce4-panel

EDIT: i must shut down for a couple of hours, hope for a good report when i get back.  i leave you with this

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=restore+panel&as_qdr=m6&sa=Google+Search&lang=en#971](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=restore+panel&as_qdr=m6&sa=Google+Search&lang=en#971)

---

### Post by Shriner on 2011-06-14
> **jerrrys said:**
> now that your in terminal enter

sudo debconf xfce4-panel

EDIT: i must shut down for a couple of hours, hope for a good report when i get back.  i leave you with this

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=restore+panel&as_qdr=m6&sa=Google+Search&lang=en#971](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=restore+panel&as_qdr=m6&sa=Google+Search&lang=en#971)
Only get:
"xfce4-panel-Message: Xfce4-panel already running"

---

### Post by Shriner on 2011-06-14
From further reading it appears that the only way to recover from this is create a new user and copy all the files except those hidden files associated with xfce from the current user to the new user.

Since I only have access to CLI can somebody give me detailed instructions on how to do this (that info wasn't included in the other thread).

Nevermind...figured out how to add the user...it didn't owrk.

---

### Post by jerrrys on 2011-06-14
in terminal

killall xfce4-panel

then follow up with sudo debconf xfce4-panel

and you have done a restart havent you?

---

### Post by Shriner on 2011-06-15
> **jerrrys said:**
> in terminal

killall xfce4-panel

then follow up with sudo debconf xfce4-panel

and you have done a restart havent you?
Results:
(xfce4-panel:2220): xfce4-panel-WARNING **: No X-XFCE-{Module,Exec} entry found in "/usr/share/xfce4/panel-plugins/xfce4-menu.desktop".

(xfce4-panel:2220): xfce4-panel-WARNING **: Failed to create plugin "xfce4-menu"

I have restarted many times.

Followup:
When starting xfce4-panel from the term window rather than alt-f2, the exact same error appears.

---

### Post by jerrrys on 2011-06-15
good morning shriner...time to dive in...

[https://help.ubuntu.com/community/XubuntuPanels](https://help.ubuntu.com/community/XubuntuPanels)

---

### Post by Shriner on 2011-06-15
> **jerrrys said:**
> good morning shriner...time to dive in...

[https://help.ubuntu.com/community/XubuntuPanels](https://help.ubuntu.com/community/XubuntuPanels)
Well that got me a bit closer.......I now have easy access to term and a file browser.
But I'm still missing "/usr/share/xfce4/panel-plugins/xfce4-menu.desktop" that apparently would allow me to recover more fully.

I'll be off and on today as I deal with other things,,,,,

---

### Post by jerrrys on 2011-06-15
navigate to this folder (in your home folder) and delete it, then restart

~/.config/xfce4/panel

and likewise; i have running around to do.  so will be checking in and out

---

### Post by Shriner on 2011-06-15
> **jerrrys said:**
> navigate to this folder (in your home folder) and delete it, then restart

~/.config/xfce4/panel

and likewise; i have running around to do.  so will be checking in and out
Did nothing for my problem.

---

### Post by jerrrys on 2011-06-15
how bout this...

create a new user; that should reset everything can you navigate to there

if not; in terminal

sudo **adduser newuser**

---

### Post by Shriner on 2011-06-15
> **jerrrys said:**
> how bout this...

create a new user; that should reset everything can you navigate to there

if not; in terminal

sudo **adduser newuser**
I had posted previusly that I'd tried that, it didn't work.

---

### Post by jerrrys on 2011-06-15
sorry, doing too many things at once.

sudo debconf xfce4-panel  i tried this and it reset my panel back to some resemblance of default.  not impressed...

i wonder if there is a cache file being overlooked.  im going exploring, will post back

---

### Post by jerrrys on 2011-06-15
ok, finally found it!

navigate to home>.config and delete the **xfce**4 folder

that simple

---

