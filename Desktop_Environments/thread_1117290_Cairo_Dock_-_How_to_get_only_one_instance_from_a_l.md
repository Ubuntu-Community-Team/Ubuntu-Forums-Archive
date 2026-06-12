---
title: "Cairo Dock - How to get only one instance from a launcher?"
date: 2009-04-05
forum: Desktop Environments
---

### Post by Adamantus on 2009-04-05
I installed Cairo Dock two days ago and have played around with it to get it to do what I like. But now I've come to something I just don't know. The attached picture should help my explanation.

The left side of my dock is my launchers, and in the middle is where the applications open up. When I click on the firefox, pidgin, or text editor launchers, no application icon opens up. Instead, I minimize and maximize with the launcher.

But for Amarok and Thunderbird, when I click on them, it creates an application icon in the center, and clicking on the launcher will try to create a new instance of that application in the center of the bar.

I want the Amarok and Thunderbird launches to do what the firefox launcher does: minimize/maximize with the launcher icon, and don't create an application icon in the center. On the flip side, I want the Firefox icon to create a new instance whenever I click on it.

The problem is, I can't find anything in the Cairo Config menu to do this. Even if there was, there would be no reason why firefox and thunderbird should act differently. And their individual configurations (the "modify launcher" option) are exactly the same. How do I fix it so that firefox opens up new application instances and thunderbird/amarok don't?

---

### Post by fabounet on 2009-04-06
probably a class mismatch for these 2 applications.
try to re-create their launcher by drag and drop from the App Menu

---

### Post by Adamantus on 2009-04-06
Thanks a lot. Thunderbird was as easy as dragging it onto the dock from the applications menu and it correctly created the class (Thunderbird-bin). I kind of guessed awhile until I found that Amarok needed to be amarokapp. 

Anyway, it's working perfectly. Thanks again.

---

### Post by radox1912 on 2010-01-07
well, i followed the solution above and it didn't help. what help was to rename the class to: thunderbird :KS , maybe it's because i used ubuntuzilla to get the newest versions of ff and tb. on my karmic system.

---

### Post by nanotube on 2010-01-07
what is this 'class' thing exactly, what does it do, and what /should/ it be for thunderbird/firefox? 

i see that the default repos shortcuts have:

StartupWMClass=Firefox

StartupWMClass=Thunderbird-bin

is that what they should be? i have ignored those bits for ubuntuzilla's launchers, because i had no idea what they were and whether they were of any use (didn't seem that way to me)... but i can put them in if it actually makes a difference...

---

### Post by fabounet on 2010-01-08
just drag and drop the launcher from the menu, it contains the StartupWMClass field, which will be used by the dock, so you have nothing to do.
if you ever need to know the class of a window, type that in a terminal
xprop | grep CLASS
then click on the window

---

### Post by nanotube on 2010-01-08
> **fabounet said:**
> just drag and drop the launcher from the menu, it contains the StartupWMClass field, which will be used by the dock, so you have nothing to do.
if you ever need to know the class of a window, type that in a terminal
xprop | grep CLASS
then click on the window

yes, my question is - if i'm making my own launcher, what should i put in the startupwmclass field? will /anything/ do, or is there some convention to follow, etc.?

---

### Post by llawwehttam on 2010-01-08
> **nanotube said:**
> yes, my question is - if i'm making my own launcher, what should i put in the startupwmclass field? will /anything/ do, or is there some convention to follow, etc.?

I always left the class box blank. Worked for me on older versions.

---

### Post by nanotube on 2010-01-08
> **llawwehttam said:**
> I always left the class box blank. Worked for me on older versions.

yes, that's what i did - but apparently it causes problems with cairo dock... that's why i was asking for clarification... i think i'll just go and try to hunt up some docs.

---

### Post by nanotube on 2010-01-08
ok, so i found the right wm classes for firefox thunderbird and seamonkey using 'xprop WM_CLASS'. i'll include them in StartupWMClass option in the .desktop files in ubuntuzilla .deb packs. Should solve the problems with the docks.

---

### Post by fabounet on 2010-01-08
yes some applications don't follow the common rules about the class, and set up some useless information in their class.

I don't think you need to make your own launchers for firefox, thunderbird, etc, just drag and drop them from the Applications menu into the dock.

99% of the time you don't need to care the class, because the dock can find it.
if it can't, rather than writing inside the .desktop, you can add it in the config panel of the launcher (both will work though)

---

### Post by nanotube on 2010-01-09
i am creating launchers for the packages in the ubuntuzilla repository, so... i do need to create my own launchers :)
but anyway, i have updated my .desktop files with the proper wmclass, so it's all good now. ;)

---

### Post by darthpenguin on 2010-05-08
Hi all. I'm having a problem with cairo-dock too. I can minimize an application window to it's launcher (just like Mac OS 10.6). But, the launcher only accepts 1 window at a time (specifically, the first window opened). So the first Firefox window I open can minimize to the ff launcher. All new windows opened after will minimize to the far right of the dock. With multiple firefox and gimp windows open the dock gets cluttered. How can I minimize all firefox windows to one launcher?

---

### Post by fabounet on 2010-05-08
in the Taskbar module, there is an option that does that.

---

### Post by darthpenguin on 2010-05-08
Hey Thanks. It's under the advanced view lol. It does this funny thing where it layers the icons over each other. I'd rather it didn't do that but it's working. cool

---

### Post by fabounet on 2010-05-09
yep, this has become an option in the 2.1.4 and later.

---

### Post by darthpenguin on 2010-05-09
I actually found a dock app that works better for me called AWN (avant-windows-manager). It does exactly what I need it to do.

---

### Post by amadis2009 on 2010-06-21
The class thing worked for me I had the issues before with Firefox and Thunderbird, but then a few weeks later realized that Limewire was having the same problem. Using the terminal to find Limewire's class as described in one of the posts above got it for me. Turns out it's sort of complicated  "org-limewire-ui-swing-Main", not like the other apps. That fixed it. Thanks.

---

### Post by marbertone on 2010-06-27
Still not solved w/ Thunderbird 3.1 . I drag and drop from application menu to Cairo dock and there're two instances for thunderbird,

---

### Post by marbertone on 2010-06-27
Whoops! Just solved! :) the right class is "Mozilla Thunderbird" and not "thunderbird-bin".
Cheers!:popcorn:

---

### Post by fabounet on 2010-06-29
maybe there is a bug in the .desktop of Thunderbird (wrong class written inside it) ?

---

### Post by thongstele on 2010-12-01
Up to now, what's the result? 
I have the same problem with u, and I need a solution...
I have spent a lot of time to make an experience but cannot solve the problem. Just some programs with the laucher have the same effect...


> **Adamantus said:**
> I installed Cairo Dock two days ago and have played around with it to get it to do what I like. But now I've come to something I just don't know. The attached picture should help my explanation.

The left side of my dock is my launchers, and in the middle is where the applications open up. When I click on the firefox, pidgin, or text editor launchers, no application icon opens up. Instead, I minimize and maximize with the launcher.

But for Amarok and Thunderbird, when I click on them, it creates an application icon in the center, and clicking on the launcher will try to create a new instance of that application in the center of the bar.

I want the Amarok and Thunderbird launches to do what the firefox launcher does: minimize/maximize with the launcher icon, and don't create an application icon in the center. On the flip side, I want the Firefox icon to create a new instance whenever I click on it.

The problem is, I can't find anything in the Cairo Config menu to do this. Even if there was, there would be no reason why firefox and thunderbird should act differently. And their individual configurations (the "modify launcher" option) are exactly the same. How do I fix it so that firefox opens up new application instances and thunderbird/amarok don't?

---

### Post by smuthavarapu on 2010-12-21
Here is what I have found.
Cairo Dock version 2.2.0.4
First Open your Application 
Right click on your Custom Launcher --> Modify this Launcher.
In the Extra Parameters, Class of the Program, Click on the Grab button and click on your application once Plus signs appear.

The Class name should automatically populated.

This worked for Jdeveloper / Sql Developer for me. 

All the best if any one still looking for.

---

