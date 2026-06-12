---
title: "Compiz Fusion and Emerald"
date: 2007-07-01
forum: Desktop Effects &amp; Customization
---

### Post by maggs on 2007-07-01
Hi, I installed Compiz Fusion and it works great. I also installed Emerald Theme Manager and I can get into the manager but can't find a way to apply a new theme. All the posts I've read say to use the Beryl icon but I don't have one of those. Do I need to install Beryl as well as Compiz Fusion or am I missing something else? I thought Compiz Fusion was the replacement for Beryl.

Maggs

---

### Post by Kakurady on 2007-07-01
Well, you can restart emerald to apply the new theme, and you can do it with Beryl Manager (the beryl icon).

I'm not sure if Compiz Fusion provides this functionality.
If not you can always kill Emerald and restart it by hand.

---

### Post by WinterWeaver on 2007-07-01
Have you checked if you have the actual Themes installed?

Open up Synaptic, and Search for emerald. Select the emerald-themes package. This should install all the themes.

The first time I installed Compiz Fusion and Emerald, I forgot to install the themes.

EDIT: and NO, you do NOT need Beryl with Compiz Fusion.

---

### Post by bodhi.zazen on 2007-07-01
You should be able to install beryl-manager without all of beryl. This will give you easy access to emerald themes.

---

### Post by steveneddy on 2007-07-01
> **bodhi.zazen said:**
> You should be able to install beryl-manager without all of beryl. This will give you easy access to emerald themes.

If you install Emerald, you can access Emerald from

System --> Preferences --> Emerald Theme Manager

---

### Post by maggs on 2007-07-01
I can run the Emerald Manager and see the themes but I dont know how to apply a theme. There is no apply button or such. When I click a theme it just gets highlighted and I can't seem to do anything else.
I checked my synaptic packages and Emerald Manager and themes are installed.

---

### Post by WinterWeaver on 2007-07-01
First check if you have the themes installed. Then use Emerald Theme manager to change your themes... With Compiz Fusion, and Emerald installed, you do not need anything beryl related ^_^

Once the themes is installed, access emerald theme manager as 'steveneddy' mentioned.

EDIT: Ignore Post, didn't notice your reply

---

### Post by WinterWeaver on 2007-07-01
As far as I remember you can select your default theme manager for Compiz Fusion. Open up the Compiz Fusion Manager, and search there for a window decoration engine or something along those lines. There should be a Dropdown List Box, to select Emerald as your Window Manager.

Sorry for being vague, I'm not in front of my home PC atm (at work).

---

### Post by maggs on 2007-07-01
I did another reboot and now it's working. Thanks to all.:D

maggs

---

### Post by WinterWeaver on 2007-07-01
You may notice that Compiz Fusion might have some buggs, since it's still under heavy development.

Here is something you can do for yourself to reset compiz, should it start doing funny things, like loose window decorations, black windows etc.

Create a Shortcut on the Desktop, the command to run is
```
compiz --replace -c emerald
```

Just in case you need it in the future :)

---

### Post by bodhi.zazen on 2007-07-01
> **steveneddy said:**
> If you install Emerald, you can access Emerald from

System --> Preferences --> Emerald Theme Manager

Ah, me beryl head. compiz has come a long way, but I like the burning windows ....

---

### Post by steveneddy on 2007-07-01
> **bodhi.zazen said:**
> Ah, me beryl head. compiz has come a long way, but I like the burning windows ....

There are burning windows in Compiz-Fission

Me thinks this

```
compiz --replace -c emerald
```

should be

```
compiz --replace -c emerald --replace&
```

---

### Post by revertex on 2007-07-01
answer here,

[http://ubuntuforums.org/showthread.php?t=489664&highlight=compiz+fusion+themes](http://ubuntuforums.org/showthread.php?t=489664&highlight=compiz+fusion+themes)

---

### Post by AndrewGene on 2007-07-03
actually, the script that i type is 
"compiz --replace -c emerald &"
that works.  And as far as changing themes, which I do a LOT, I leave beryl manager up (even though I no longer have a lot of beryl on my system) and go to the emerald theme manager through that.  I find that if I leave beryl theme manager open on start up and have the code I just gave you run at start up then everything works flawlessly.  You don't even have to restart emerald/compiz to get the theme to take effect.

---

### Post by whereareyoutakingme on 2007-07-06
aaahh...  :)  i did all these things and i am not having the same good fortunes as you are....

let me further explain...

1. i installed beryl and emerald through the terminal command
2. i checked synaptic and the themes were not installed, so i installed them
3. i closed beryl and emerald, then restarted them and found a whole bunch of themes now
4. i selected the theme i wanted by left clicking it once, then i tried double clicking it

....the end result is still the same: the theme becomes highlighted when i click on it, but nothing changes...

.....i've tried reloading the windows manager and windows decorator several times in all kinds of orders after having selected themes, i've tried reloading my x server w/ ctrl+alt+backspace and nothing seems to make my desktop environment look any different.

......also, i'm confused about which windows manager and decorator i should be using....

....have i missed some small step somewhere along the process of installing all this stuff?  
....could someone write out the whole process or point me to someone who already has?

---

### Post by NeoLithium on 2007-07-06
> **whereareyoutakingme said:**
> aaahh...  :)  i did all these things and i am not having the same good fortunes as you are.... can anyone suggest another solution??

Depending on how you installed fusion, open up synaptic and search for beryl.  If you have fusion install; remove the beryl components. Some people are having luck with that.

---

### Post by whereareyoutakingme on 2007-07-06
i don't have fusion at all, please reread my first replay as i have retyped it to better explain my problem :)  thanks for any help you may have!

---

### Post by revertex on 2007-07-06
[SIZE=1]deleted[/SIZE]

---

### Post by cor2y on 2007-07-06
i HAve the same problem myself the only solution i have found is to restart emerald for the them to take effect.
It doesn't require you restart compiz or beryl.
Its a hassle if there is a fix for this i'd like to know it myself.
By the way this problm for me effects beryl, compiz and compuiz fusion no they are not all installed at the same time but i have tried all three and emerald has behaved like this in all three.

---

### Post by whereareyoutakingme on 2007-07-06
i have now tried restarting emerald a couple of times and no luck.  i have an nVidia 6800SE, why am i having so many problems :(   i thought nVidia was like the best video card ever for Ubuntu!!  

let me ask this.....when you say restart emerald,  what i did was open beryl manager, open emerald theme manager and highlight the theme i wanted.  nothing happened so i clicked quit and then reopened emerald theme manager from the red diamond again.  still when i clicked the theme again it just sits there, dumbfounded, waiting for me to do something right :(  

is this what you meant when you said restart emerald? ( i know it may seem silly to ask but i'm at a loss for words after having spent hours trying to get this working)

---

### Post by marsmissionaries on 2007-07-06
You must restart emerald to change the theme after selecting it when running emerald with compiz.

to do this use the alt+f2 shortcut to open the application launcher and then type 

```
emerald --replace
```

that will take care of everything.

---

### Post by whereareyoutakingme on 2007-07-06
thank you for your device, but i think i'm using metacity (gnome windows manager) from the drop down menu on the red diamond.  i tried using the compiz windows manager but it just combines all my virtual desktops into one and my title bars disappear from my windows and i can't move them around anymore.  the same thing happens when i use beryl window manager, so i just keep trying to get it working on the metacity window manager....

....but obviously i'm still doing something wrong

---

### Post by psyopper on 2007-07-07
> **whereareyoutakingme said:**
> i have now tried restarting emerald a couple of times and no luck.  i have an nVidia 6800SE, why am i having so many problems :(   i thought nVidia was like the best video card ever for Ubuntu!!  

let me ask this.....when you say restart emerald,  what i did was open beryl manager, open emerald theme manager and highlight the theme i wanted.  nothing happened so i clicked quit and then reopened emerald theme manager from the red diamond again.  still when i clicked the theme again it just sits there, dumbfounded, waiting for me to do something right :(  

is this what you meant when you said restart emerald? ( i know it may seem silly to ask but i'm at a loss for words after having spent hours trying to get this working)

I had this problem when I was using Beryl. I had Emerald and Emerald-themes installed but couldn't use it. Then I figured out that I didn't actually have Emerald *running*! Once I turned Emerald on changing themes was as easy as selecting them in the Emerald Theme Manager. I could even make "on the fly" customizations to the theme and see them real time on my desktop.

Apparently under Compiz Fusion this is different - you need to restart Emerald to see changes to your themes/ theme selections.

> **whereareyoutakingme said:**
> thank you for your device, but i think i'm using metacity (gnome windows manager) from the drop down menu on the red diamond.  i tried using the compiz windows manager but it just combines all my virtual desktops into one and my title bars disappear from my windows and i can't move them around anymore.  the same thing happens when i use beryl window manager, so i just keep trying to get it working on the metacity window manager....

....but obviously i'm still doing something wrong

You may be doing something wrong, but not actually are aware of it at all. The most common reason that window borders disappear when running Compiz/Beryl on an nVidia card is an X configuration setting. There are about 100 threads in this forum about Compiz (or Beryl) not showing window borders...

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup2

sudo gedit /etc/X11/xorg.conf

```

Then add the following line : 

Option      "AddARGBGLXVisuals" "True"  to the Drivers section for your video card so that it looks like this in your xorg.conf

```

Section "Device"
    Identifier     "<your display device name>"
    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"
EndSection

```

There may be other options listed for your display device, keep them. Only add the line I pasted above.

Once you do this save and close any open documents and then press [CTRL]+[ALT]+[Backspace]. This will restart your X Server and put you back to a login screen. Log back in, come back to this post and let us know if you are still having problems!

---

### Post by BL00dFox on 2007-07-08
> **maggs said:**
> I can run the Emerald Manager and see the themes but I dont know how to apply a theme. There is no apply button or such. When I click a theme it just gets highlighted and I can't seem to do anything else.
I checked my synaptic packages and Emerald Manager and themes are installed.

I also am experiencing the same problem... Please help

---

### Post by psyopper on 2007-07-08
What video card do you have?

DId you check your xorg.conf for the line I described above?

Are you actually RUNNING emerald (did you issue a command somewhere to start Emerald?)

To start emerald press [ALT]+[F2] and type:

emerald --replace

Then open the Emerald Theme Manager and select your theme.

---

### Post by Calcipher on 2007-07-15
To anyone still having problems one thing that worked for me was to do the following:
1. System->Preferences->Sessions
2. In the startup tab delete anything related to compiz or emerald (you may wish to wright down what commands they run in case this fails)
3. Make a new item:
    -Name: Compiz
    -Command: compiz --replace
4. Hit OK to save the new item and click new to make another new item:
    -Name: Emerald
    -Command: emerald --repalce
5. Hit OK to save the new item and go to the Sessions Options tab
6. Click Save the current session
7. hit [ctrl]+[alt]+[backspace] to restart your XSession
8. Log back in and verify that your chosen theme has loaded

---

### Post by Psy-Krow on 2007-11-30
@psyopper

awesome man, thanks for the code above.  seems to have worked like a charm, havn't had any more title bars doing their disappearing act yet.

---

### Post by pip_134 on 2007-12-20
Calcipher, Brilliant solution, solved all my problems as well!

---

