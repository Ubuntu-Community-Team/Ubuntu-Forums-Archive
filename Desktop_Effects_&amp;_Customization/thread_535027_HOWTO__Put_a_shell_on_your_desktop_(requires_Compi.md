---
title: "HOWTO:  Put a shell on your desktop (requires Compiz*)"
date: 2007-08-25
forum: Desktop Effects &amp; Customization
---

### Post by phaedOne on 2007-08-25
I will show how to create a transparent shell using only gnome-terminal and Compiz-fusion.  Check out the attached screenshots.

[SIZE="3"]**Part 1:**[/SIZE]

Create a new profile in gnome-terminal (Edit->Profiles->New), name it "*trans*".  Set the following characteristics:

Cursor blinks: **off**
Show menubar: **off**
Initial title: **trans**
Dynamically-set title:** Isn't displayed**
Color scheme: **Black on white**
Transparent Background: **on**
Set the transparency down to** "None"**
Scrollbar: **disabled**

The important part here is that now the gnome-terminal is gonna have the title *trans*.  We can now target the gnome-terminal windows that are using trans profile from inside CompizConfig by using *title=^trans$*  

[list]The ^ at the begining means for the title to match it must start with the word *trans*, The $ at the end means the title must end after trans.  This prevents it from matching other phrases that include "trans" for example "The *trans*formers"   (See:[Regular Expressions]("http://www.grymoire.com/Unix/Regular.html")).  You can match windows by other things than their title  (See: [[How To] Use opacity values and Window Rules]("http://forum.compiz-fusion.org/showthread.php?t=1768")).[/list]

[SIZE="3"]**Part 2:**[/SIZE]

Have an instance of gnome-terminal open with the trans profile so you can see whats happening to it as you follow the rest of the howto.  Open CompizConfig (System->Preferences->CompizConfig).  

Make sure you have the **regEx** plugin enabled.  

Go to the **Window Decoration** plugin and add *!title=^trans$* to the* Decoration windows* field.  This will skip adding window borders to our trans terminals.

Go to the **Window Rules** plugin.  Add *title=^trans$* to the following fields (This will turn the terminals into a widget-like windows,  *Sticky* will put them on all sides of the cube):
[list]Skip taskbar, Skip pager, Below, Sticky, Non resizable windows, Non minimizable windows, Non maximizable windows, Non closable windows[/list]
In the * Fixed Size Window*s section click add.  Use *title=^trans$* for the the *Sized Window* field and put the height and width you want for your shells.

Go to the **Place Windows** plugin, go to the *Windows with fixed positions* tab, in *Windows with fixed positions* click add.  Put *title=^trans$* in *Positioned Windows* field and put x and y coordinates of the default position you want for your shell (top-left corner is 0,0).  After they have loaded you can move them by Alt-Dragging them.   

To run the transparent gnome-terminal use:
```

gnome-terminal --window-with-profile=trans

```
Edit:
The guide will put the same shell repeated on all sides of the cube.  You could put a different shell on each side of the cube. To do this create a profile following the fist part of the instructions above but change the title to *trans1*.   Now make three new profiles using this first profile as its base.  Change the titles of these profiles to:  *trans2*, *trans3*, *trans4*.   Now follow the second part of the instructions above using *title=^trans[1-4]$* instead of *title=^trans$* to match the windows.  Now you want to set each one to appear on a  fixed side of the cube.  Go to the **Place Windows** plugin, go to the *Windows with fixed positions* tab, in *Windows with fixed viewports*.  Here add each of your four windows ( *title=^trans1$*, *title=^trans2$*, ...)  along with the viewport you want them to be in.

[SIZE="1"]
dock: avant-window-navigator
widgets: conky /  [theme]("http://ubuntuforums.org/showpost.php?p=3197911&postcount=505")


[/SIZE]

---

### Post by ESPOiG on 2007-08-25
very good ill try that soon :D

1 question what is the dock program?

---

### Post by psyopper on 2007-08-26
Good one!! I had been working on doing this with Devilspie a few month back but got frustrated with the window sizing and placement scheme. This is much easier - size the window, place it then lock it down and clean it up with Window Rules and Window Decoration in Compiz-Fusion.

Mush less overhead to do the same thing considering I'll be running CF anyway.

Thanks a bunch!!

---

### Post by walkerk on 2007-08-26
Very nice. I just removed devilspie.. :)

---

### Post by Dark Star on 2007-08-26
Awesome guide .. Will give it a try soon :) Thanks bro :D

---

### Post by chm0d on 2007-08-26
I just did this and it worked great, but now I have no borders around any of my windows.  Did I do something wrong?  Obviously i did LOL....tell what I did.  Also when we were told to put title=trans in certain spots and plugins do I use the quotes as well? I also seen one with an exclamation mark just want to make sure that is correct as well.  BTW I love your conky theme great job on that.

fsckr

---

### Post by walkerk on 2007-08-26
> **chm0d said:**
> I just did this and it worked great, but now I have no borders around any of my windows.  Did I do something wrong?  Obviously i did LOL....tell what I did.  Also when we were told to put title=trans in certain spots and plugins do I use the quotes as well? I also seen one with an exclamation mark just want to make sure that is correct as well.  BTW I love your conky theme great job on that.

fsckr

dont use quotes.. and the exclamation point means exclude basically.. so !title=trans would decorate all windows **except** those with trans in the title which you would use for window decorations plugin. the rest should be title=trans..

---

### Post by Meyithi on 2007-08-26
chm0d for "Window Decoration", if you have "any" in there, remove it and just add !title=trans

Otherwise if you have more custom rules in there I think the seperator is "|"

---

### Post by chm0d on 2007-08-26
> **Meyithi said:**
> chm0d for "Window Decoration", if you have "any" in there, remove it and just add !title=trans

Otherwise if you have more custom rules in there I think the seperator is "|"

This did not work for me.  I have !tile=trans in that field.  If i put that in there without quotes nothing happens.  If I put that in there with quotes every window is missing a border.  So there is definitely something wrong.  I have compiz-fusion 0.5.2.  I have recieved some help on the compiz-fusion irc channel and the person there had the same problem that I did.  

fsckr

*solved.  instead of !title=trans I had to xprop | grep WM_CLASS in terminal to fine the class which for me was Gnome-terminal so I had to put !class=Gnome-terminal in that field instead of !title=trans.  Hope this helps everyone else having this problem.  Also thanx to amphi on #compiz-fusion on irc!

fsckr

---

### Post by Lord Illidan on 2007-08-26
Nice..but I have a couple of probs.

First, how can I disable show desktop plugin from moving it?

Secondly, try typing trans in a google search in firefox. The title changes to include trans, and ... havoc ensues.

---

### Post by yuri_rage on 2007-08-26
> **Lord Illidan said:**
> First, how can I disable show desktop plugin from moving it?

I have the same issue...plus one.  Mine shows up initially as an 800x600 window (the default).  I need to use the "show desktop" tool to minimize, then restore it to get it to follow the rules I have set in the compiz config manager.

Any ideas?

---

### Post by Lord Illidan on 2007-08-26
Also, you didn't include that you have to disable scrollbar.

---

### Post by chm0d on 2007-08-26
I hardly ever use show desktop.  I myself use many workspaces.  So..by any chance is there a way for each of my workspaces to have their own terminal?

fsckr

---

### Post by Diabolis on 2007-08-26
Cool guide, I only had one problem. Windows decorations disappeared for all my applications. After trying different names and combinations of words I figured it out. The problem was that I typed **"!title=trans"** instead of **!title=trans** . I know this is very silly, but others might run into this too.

---

### Post by cawill on 2007-08-26
> 
Secondly, try typing trans in a google search in firefox. The title changes to include trans, and ... havoc ensues.

Am I right in saying that the name of the profile doesn't actually need to be trans? so if the name trans is a problem couldn't you replace trans in all the settings with something random? (1039402 etc that would never come up)

---

### Post by sekazi on 2007-08-26
I like this idea and I have it working except for the window size.

In the Windows Rules section under Fixed Size Windows I set title=trans to 480x680 which I assumed was pixels. After that did not work I tried what is says when I size the window which is 40x60. Neither worked for me. It seems to load the default terminal size when it launches.

---

### Post by Lord Illidan on 2007-08-26
> **cawill said:**
> Am I right in saying that the name of the profile doesn't actually need to be trans? so if the name trans is a problem couldn't you replace trans in all the settings with something random? (1039402 etc that would never come up)

True..just saying as trans is not a difficult word to type in firefox. Note that even if I type transparent or trans1 or whatever word occurs with trans in it, problems crop up. Is there a way to restrict the title detection to detect just titles which are "trans" only?

---

### Post by cawill on 2007-08-26
> **Lord Illidan said:**
> True..just saying as trans is not a difficult word to type in firefox. Note that even if I type transparent or trans1 or whatever word occurs with trans in it, problems crop up. Is there a way to restrict the title detection to detect just titles which are "trans" only?


Yes, I agree that the trans name needs to be changed to something else as it comes up to often or find a way to change the settings to detect only 'trans' as you have suggested.

---

### Post by Rupertronco on 2007-08-26
One, to disable scrollbars go into your regular terminal, edit the trans profile go to the scrolling tab, and go to disable. Also, if searching trans is the problem, change the profile name to something ridiculous like I did, my profile is called "caddywompus". 

Also if you use tabs in firefox, it only affects the tab in which you typed it, I find it to be quite hillarious actually.

---

### Post by yuri_rage on 2007-08-26
I changed everything from "trans" to "desktop.terminal.window" - that seems improbable enough.

One problem solved:
Disabling the "Hide skip taskbar windows" setting in the General tab of compizconfig keeps the terminal window open when you use the "Show Desktop" function.

One problem remaining:
I'm still stuck with an 800x600 window, even though I specified a larger size in "Fixed Size Windows."

---

### Post by Rupertronco on 2007-08-26
> **chm0d said:**
> I hardly ever use show desktop.  I myself use many workspaces.  So..by any chance is there a way for each of my workspaces to have their own terminal?

fsckr

I'm not sure that's possible with these settings and compiz, I've been playing around with that, but with the way you anchor it, and the way compiz reacts to it, I can't get it to stop cloning the single terminal.

---

### Post by Lord Illidan on 2007-08-26
> **yuri_rage said:**
> I changed everything from "trans" to "trans6969" - that seems improbable enough.

One problem solved:
Disabling the "Hide skip taskbar windows" setting in the General tab of compizconfig keeps the terminal window open when you use the "Show Desktop" function.

One problem remaining:
I'm still stuck with an 800x600 window, even though I specified a larger size in "Fixed Size Windows."

That Hide Skip Taskbar Windows does the trick, found it here

[http://ubuntuforums.org/showthread.php?t=535459&highlight=compiz](http://ubuntuforums.org/showthread.php?t=535459&highlight=compiz)

As for the 800x600 Window, it may be neccessary to restart the plugin or even  compiz-fusion sometimes..

---

### Post by yuri_rage on 2007-08-26
Another problem solved:
You can override the default terminal window size using the "--geometry" flag on the command line.  This works pretty well for me:
gnome-terminal --window-with-profile=desktop.terminal.window --geometry 100x57+200+0

---

### Post by sekazi on 2007-08-26
thanks yuri_rage it worked for me. I had to remove the resize and placement rules in order for it to work for me. I also had to add the command for my window for non movable windows since there was a hidden bar to move it acidently.

Would it be possible to allow icons to stay over the terminal. This would make it so the terminal looks like it is completely embedded into the desktop. If I save something to the desktop right now the terminal gets in the way and I cannot select the icon.

---

### Post by phaedOne on 2007-08-26
> **chm0d said:**
> I hardly ever use show desktop.  I myself use many workspaces.  So..by any chance is there a way for each of my workspaces to have their own terminal?

fsckr

I have edited the post with instructions on how to put a separate terminal in each viewport.

---

### Post by sekazi on 2007-08-27
Thanks for the tutorial.

I would really like to know what I am doing wrong when resizing the windows. I am able to place it in the correct location but resizing does not work for me. The only method which really worked was yuri_rage but I would like to know what I am doing wrong in compiz.

Under Place Windows in the Fixed Window Placement tab I have put title=^trans[1-4]$ in Positioned windows. The X Positions is 15 and the Y Positions is 60. When I use this with yuri_rage command it resizes it perfectly but in compiz it says 800x600.

---

### Post by ittiam on 2007-08-27
it may be slightly off the topic but please can be tell what is the toolbar launcher that is there in the screenshot. I have only gdesklets...is it gdesklet or something else? Also how did u redo ur top panel? Sorry as it is off the topic

---

### Post by phaedOne on 2007-08-27
> **sekazi said:**
> Thanks for the tutorial.
I would really like to know what I am doing wrong when resizing the windows. I am able to place it in the correct location but resizing does not work for me. The only method which really worked was yuri_rage but I would like to know what I am doing wrong in compiz.


Thanks.  As for your problem im not sure what it could be.  You should be able to set the size in the **Window Rules** plugin in the *Fixed windows* section.  If its not working maybe it could be a bug in the plugin.  The people at the OpenCompositing forums may be able to help you.  At least for now you got yuri_rage's [workaround]("http://ubuntuforums.org/showpost.php?p=3257747&postcount=23").

> **ittiam said:**
> it may be slightly off the topic but please can be tell what is the toolbar launcher that is there in the screenshot. I have only gdesklets...is it gdesklet or something else? Also how did u redo ur top panel? Sorry as it is off the topic

The dock is avant-window-navigator (AWN).  

```

echo 'deb http://download.tuxfamily.org/3v1deb feisty eyecandy' >> /etc/apt/sources.list
echo 'deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy' >> /etc/apt/sources.list
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
sudo apt-get update; sudo apt-get install avant-window-navigator

```

To make AWN look glossy like I have it run gconf-editor inside goto apps/avant-window-manager/bar/angle put in 45.  This turns the dock 45 degrees inward and gives it reflection.   apps/avant-window-manager/bar/icon_offset  put in 18.  To make the icons go up a little higher to show their reflection.

The top panel is the regular gnome-panel set to extend=off.  I removed the tasklist plugin that puts all windows on the taskbar cause AWN handles that already.  It looks dark because i have a dark window theme: [Mire v2]('http://www.gnome-look.org/content/show.php?content=51023") used with the murrine engine

```

sudo apt-get install gtk2-engines-murrine

```

---

### Post by ittiam on 2007-08-27
that repo is already in my sources list...but when i do an apt-get install..it says package not found...???

---

### Post by ittiam on 2007-08-27
ok i had it installed manually! But avant-preferences doesnt seem to give that much options. Like make the icons stand vertical and have reflection enabled ..???

---

### Post by phaedOne on 2007-08-27
sorry had mistyped it.  its avant-window-navigator not avant-window-manager

---

### Post by phaedOne on 2007-08-27
> **ittiam said:**
> ok i had it installed manually! But avant-preferences doesnt seem to give that much options. Like make the icons stand vertical and have reflection enabled ..???

For the reflection you have to run "gconf-editor" and edit the settings there.  Yea the AWN dock doesn't do vertical [yet]("https://blueprints.launchpad.net/awn/").  Its part of the [Google]("http://code.google.com/p/awn-plugins/") summer of code campaign so its gonna be seeing improvements real soon.

---

### Post by Lord Illidan on 2007-08-27
Thanks for editing the howto will definitely test it again tonight.

---

### Post by sekazi on 2007-08-27
> **phaedOne said:**
> Thanks.  As for your problem im not sure what it could be.  You should be able to set the size in the **Window Rules** plugin in the *Fixed windows* section.  If its not working maybe it could be a bug in the plugin.  The people at the OpenCompositing forums may be able to help you.  At least for now you got yuri_rage's [workaround]("http://ubuntuforums.org/showpost.php?p=3257747&postcount=23").

Apparently the terminals must start before compiz does in order for the resizing and placement to take effect. I cannot seem to get all 4 terminals to open at once. When I use a sh script only the 1st window opens and when I close it the second does. If I put each one in the startup only the first one opens then. If I can get that working I can put compiz on a delay and the resize and placement should work.

How are you getting the terminals to start on startup?

---

### Post by phaedOne on 2007-08-27
> **sekazi said:**
> Apparently the terminals must start before compiz does in order for the resizing and placement to take effect. I cannot seem to get all 4 terminals to open at once. When I use a sh script only the 1st window opens and when I close it the second does. If I put each one in the startup only the first one opens then. If I can get that working I can put compiz on a delay and the resize and placement should work.

How are you getting the terminals to start on startup?

try something like

```

#!/bin/sh
gnome-terminal --window-with-profile=trans1 &
gnome-terminal --window-with-profile=trans2 &
gnome-terminal --window-with-profile=trans3 &
gnome-terminal --window-with-profile=trans4 &

sleep 3
compiz --replace &

```

---

### Post by sekazi on 2007-08-27
Using that script sortof works but still not completely. I still have the problem with only 1 terminal opening. This time it actually sized it right but its position was wrong. Im going to try and find more information on OpenCompositing.org later.

---

### Post by ittiam on 2007-08-27
thanks for your inputs..it is working good!

---

### Post by ittiam on 2007-08-27
one more quick question....may sound silly...i am just not able to see the icon of the current active window but just a glow...i have tried different glows for it wherein it will glow with icon visible...is there any way to make the icon of current active window visible?

---

### Post by chuckyp on 2007-08-28
> **Rupertronco said:**
> I'm not sure that's possible with these settings and compiz, I've been playing around with that, but with the way you anchor it, and the way compiz reacts to it, I can't get it to stop cloning the single terminal.

Why not create multiple profiles i.e. trans1 trans2 etc... then launch them on different workspaces.

---

### Post by Holder on 2007-08-29
I don't know how but it ****** up my whole compiz fusion =\

Thanks anyway..

---

### Post by Rupertronco on 2007-08-29
> **Holder said:**
> I don't know how but it ****** up my whole compiz fusion =\

Thanks anyway..

You probably took the effects away by keeping the exclamation in a few of the fields and leaving the word "any" there.

---

### Post by nest on 2007-08-29
say goodbye to devilspie.

thanks phaedOne :)

---

### Post by spaceship.rodeo on 2007-08-29
Excellent guide, thanks.  Is there any way to make it load when you boot?

---

### Post by phaedOne on 2007-08-31
> **spaceship.rodeo said:**
> Excellent guide, thanks.  Is there any way to make it load when you boot?

Add it to System->Preferences->Sessions

---

### Post by s_spiff on 2007-09-13
Fantastic! only one doubt, I want the terminal on my 4th workspce, not the first. What do I do? I know you've given that too in your HowTo, but didn't get it :D

---

### Post by alwiap on 2007-09-21
Just did the guide, and this looks sexy!

But I have 3 questions.

1. When I put this in System > Preferences > Sessions, do I just put "gnome-terminal --window-with-profile=trans" in for the command? I'm a nub and don't want to mess anything up.

2.  Is there a command to restart the terminal, so I can see how I adjusted the width and heighth?

3. What is a good width and heighth for the terminal (i.e. what is your setup in your screenshot?) I'm talking about where you adjust it in ```
In the  Fixed Size Windows section click add. Use title=^trans$ for the the Sized Window field and put the height and width you want for your shells.
```

Thanks so much for making this guide.

EDIT: I figured out how to close the terminal with right-clicking it, but is there an actual command i can type in terminal to get it to close? ty!

2nd Edit:  I set a good width and heighth for my setup (1600x1200), and it fills the whole left area of my screen, it is 520x1140.  Screenshot enclosed.

So I guess the only question I have is adding it in Sessions. :)

---

### Post by runescape1143 on 2007-09-21
To close the terminal just type exit,
And in sessions you can name it Desktop Console and give the command as
gnome-terminal --window-with-profile=DesktopConsole --geometry 100x57+140+18
The geometry is optional but the last two numbers allow you to position it on the screen, as i can't get compiz to do the positioning.

---

### Post by lebabyg on 2007-09-24
has anybody successfully got this to start on session startup on an XGL session?  When i do so, it loads up in the wrong position and with a fake transparency that obscures the icons underneath it.

---

### Post by amadeus266 on 2007-09-26
Well written guide I must say. But my wife already says my desktop is too "techie" with comiz-fusion, kiba-dock, and conky running. But my question isn't related. My question is what is the clock in the center of your screen?

---

### Post by Desigen on 2007-09-26
Hi, Thanks it's is a cool idea. 

How can I make the menu bar like the one you did?
Can you please give me any good articles. 

Thanks

---- 

Sorry I didn't read page 3. 

Bye

---

### Post by Desigen on 2007-09-28
Hi, I have a problem with Fixed Window Size. It doesn't change,, any idea ??

---

### Post by czepluch on 2007-09-28
Very stupid question from me, but i can't really see what this shell does and how it works? Haven't installed it yet. Want to know what it does before giving it a shot :P

---

### Post by Desigen on 2007-09-29
Bash Shell is an interpreter ; in other word, it will receive commands and orders from user or bash file and it will process those commands and return an output to monitor by default.

---

### Post by Desigen on 2007-09-30
Hi, From while to while the windows boarder disappear. 
Is it related to this trick ??

---

### Post by nosscire on 2007-10-05
> **Desigen said:**
> Hi, I have a problem with Fixed Window Size. It doesn't change,, any idea ??

I have the exakt same problem. Thing is, i've followed this guide before, and then it worked flawless. Maby something with latest verion of CF? Anyone know?

---

### Post by CC_Joe on 2008-06-15
> **Desigen said:**
> Hi, From while to while the windows boarder disappear. 
Is it related to this trick ??


It could be. See if your windows border disappears when you use your browser and search for "trans" or whatever you named your terminal. If that's the case, then you're missing the ^ and $ from the title=^trans$ in one of your compiz settings.

---

### Post by SoftwareExplorer on 2008-06-17
> **cawill said:**
> Am I right in saying that the name of the profile doesn't actually need to be trans? so if the name trans is a problem couldn't you replace trans in all the settings with something random? (1039402 etc that would never come up)

what if you made a rule that basically said not(title is trans and type is gnome terminal)? I don't really know the syntax for CF yet, though.

---

### Post by Lucid_3ntr0py on 2008-06-30
After following all the instructions, I am going to have to say that the --geometry is the best way to go. Editing the compiz fixed window doesn't seem to work.

Thank you

---

