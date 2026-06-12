---
title: "New Compiz manager and Emerald"
date: 2007-10-17
forum: Desktop Effects &amp; Customization
---

### Post by pdavit on 2007-10-17
I've been using v7.10RC of Ubuntu and I have installed compizconfig-settings-manager
so that I can tweak the windows manager. Before I was using Beryl with the Emerald
add-on. 

What do I need in order to use Emerald themes now? Is there some kind of plug-in
for compiz-fusion I have to install?

Thank you!

---

### Post by gsiliceo on 2007-10-17
Have you already done:

sudo apt-get install emerald emerald-themes

?

---

### Post by pdavit on 2007-10-17
Nop! 

So, this is the compatible add-on to the new Compiz manager, right?

(not the old Beryl add-on?)

---

### Post by santiagoward2000 on 2007-10-17
> **pdavit said:**
> Nop! 

So, this is the compatible add-on to the new Compiz manager, right?

(not the old Beryl add-on?)

Actually, it's the same, it's compatible with both...

---

### Post by pdavit on 2007-10-17
Ok, I've installed Emerald via Synaptic Manager without problems. Using the terminal command suggested here I was getting the following error:

Package emerald-themes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emerald-themes has no installation candidate

Anyway, it's under Preferences now and while the Emerald Theme Manager works fine I see no changes on window boarders. I have all effects active. It must be some options I need to tweak since everything works like a charm. 

Any help?

---

### Post by 1337455 10534 on 2007-10-17
Yep.
Download the actual package Emerald-themes from a browser (official Ubuntu website repo), and install it w/ GdebI. Just google it.
:). Thats what it meant by a reffered package. If you try, you wont find themes in Synaptic...

edit>>> [http://packages.ubuntu.com/feisty/x11/emerald-themes](http://packages.ubuntu.com/feisty/x11/emerald-themes)  (thats the feisty repo, but i tink it will work)

---

### Post by JBAlaska on 2007-10-17
You can now have CF start Emerald, enable the "windows deroration" plugin and type emerald in the plugin command box

---

### Post by pdavit on 2007-10-18
It works fine with: Alt+F2 -> emerald --replace

---

### Post by steveneddy on 2007-10-18
Once I installed Emerald, it starts up with Emerald every time.

:popcorn:

---

### Post by mannheim on 2007-10-18
> **steveneddy said:**
> Once I installed Emerald, it starts up with Emerald every time.


I reported this as a bug. Of course, most people who install emerald want emerald. But the present compiz launch script will not give you the choice: if /usr/bin/emerald exists, then it gets used as the decorator. You *can* disable it by adding USE_EMERALD="no" to ~/.config/compiz/compiz-manager.

---

### Post by gdp77 on 2007-10-18
Hi, I installed 7.10 today (desktop - i386)

1) I've Installed restricted drivers
2) enabled compiz,
3) installed ccsm (advanced desktop effect settings)
4) I 've installed emerald (apt-get install emerald)

My problem is that there are no themes to choose  from, except  the default (red one) in the emerald theme manager. 

[[IMG]http://img155.imageshack.us/img155/1692/screenshotvw5.png[/IMG]](http://imageshack.us)




I used "apt-get install emerald emerald-themes" but it didn't work.  What am I doing wrong?


P.S. Also when I used 7.04+beryl, moving the mouse at the upper right corner of my screen, resulted in appearance of all windows on my screen. How can I activate this feature in compiz-fuzion? 

Thank u for your help

---

### Post by schneider707 on 2007-10-18
just use synaptic and search for emerald-themes...should be right there. Although using apt-get install emerald-themes should of worked just the same...

> P.S. Also when I used 7.04+beryl, moving the mouse at the upper right corner of my screen, resulted in appearance of all windows on my screen. How can I activate this feature in compiz-fuzion?

I believe this option is called 'Wall' or something like that. I can let you know when I get back to my apartment. It should be in the basic settings manager.

---

### Post by TwYst on 2007-10-18
as for the first problem with emerald i cant really help ya with yet as i havent installed it yet on mine to tinker with it. the second bit tho isnt too bad with the mouse to upper right corner to show all open windows.
check in system/preferences/appearance then look for the visual effects tab. tick the bottom one marked "extra" and you will have yer top right corner toy back working again.

---

### Post by gdp77 on 2007-10-18
> just use synaptic and search for emerald-themes...should be right there

No it isn't there...

---

### Post by Queig on 2007-10-18
I cant get the emerald-themes pack either, doesnt seem to be in the repositries.

I have been able to install downloaded themes from [www.gnome-look.org](www.gnome-look.org)

The mouse to the top right corner thing is the "scale" function under compiz-fusion 

start CCSM>window management>scale>actions>general>initiate window picker for all windows

---

### Post by yang on 2007-10-18
(1) I can't see emerald-themes either.

(2) Fetching GPL themes doesn't work (svn.beryl-project.org isn't available)

(3) Fetching non-GPL themes from generation.no works, but how do I enable these themes? Tried entering "emerald" in the "window decorations" plugin in compizconfig but that didn't do anything.

---

### Post by buntunub on 2007-10-18
[http://ubuntuforums.org/showthread.php?t=578691&highlight=compiz+themes](http://ubuntuforums.org/showthread.php?t=578691&highlight=compiz+themes)


Just 4 posts beneath this one. tssk tssk.

---

### Post by Vorian on 2007-10-18
merged

---

### Post by yang on 2007-10-18
I already tried specifying emerald (and emerald --replace) in the command line box (as I mentioned), and I also tried running emerald from the command-line, which gives me an error about not being able to acquire the decoration manager.

---

### Post by cjm5229 on 2007-10-18
Try turning off Desktop effects and then turning them back on, Worked on mine. And you should be able to download the theme's in "Fetch GPL'D themes but you have to install Subversion and enable the Repositories ```
sudo apt-get install subversion repositories
```   ```
svn ls https://svn.generation.no/emerald-themes
```

---

### Post by yang on 2007-10-18
Actually, that's for getting the non-GPL'd themes. (That was working for me.)

---

### Post by linuxlizard on 2007-10-19
Can anyone tell me how to make the windows "float" above the background when the cube is active? It looks really 3d cool, but can't seem to figure it out in compiz- I used to have it in beryl.

---

### Post by airbornemist6 on 2007-10-19
that is the 3d windows plugin, which you can turn on with the advanced desktop effects option which you get by installing compiz-fusion-settings. *sigh* however, i don't think the settings on it are actually working. It makes me sad. Seriously, I hate this "new" compiz manager, you can't do like anything. The fact that you could customize beryl and compiz fusion is what made them great. But this thing is driving me crazy. I'm also having the same problem with not being able to get my emerald-themes package, But there is one difference for me... I can't get my non-GPL'd either, subversion says it got it, but it won't show up. I was hoping compiz fusion would finally be working beautifully with the introduction of gutsy... but I guess not.

(Note: I am also unable to load from 4 "official" ubuntu repo's, if someone also has this problem, I get the feeling the repo we need may be down and thus the reason why we can't get ahold of emerald-themes)

---

### Post by Screaming Monkey on 2007-10-19
I'm having a similar difficult time with Beryl and Compiz.  I've upgraded to 7.10 from 7.04 and have tried to enable certain effects and have found that I have to go into my Beryl settings manager to set some, and then some get overridden by Compiz and then some just get disabled altogether.  Really damn confusing.

Anyone got any advice on this?  Should I uninstall Beryl and just go with the default?  I mean I had to get Beryl up and running just to get the 3d cube!  I have it turned off now and yet, I have the cube.  It's just really buggy.  

And I'm enough of a newb that I don't have any advice, but will gladly heed others.

---

### Post by Vorian on 2007-10-19
```
sudo apt-get install compizconfig-settings-manager
```

run

> ccsm

configure to your hearts contentment.

3d windows are not compatible with the version of compiz in gutsy.  You can find individual Emerald themes at gnome-look or beryl-look.

---

### Post by Screaming Monkey on 2007-10-19
Still getting bugs.  

With Beryl running, and choosing Beryl as the window manager, I get all the Beryl effects and it works great.  With it running and choosing Compiz as the window manager, I can apply almost all the bindings and shortcuts I want to but it seems to do bupkiss.

What's working?  The fire plugin, the expo plugin.  And those work even when I choose Beryl as my window manager. 

I am confused.  Anyone?

I can't activate the window edges in Compiz, I can't seem to get any of the key shortcuts that I want working.  I am stuck.

---

### Post by WestCoastSuccess on 2007-10-19
Here's my $0.02: I searched Synaptic for "emerald", selected "libemeraldengine0" and "emerald", installed them, the followed the instructions in a post above: Alt+F2 and typed "emerald --replace" and hit run - voila - my emerald decorations are back!

---

### Post by Julius on 2007-10-20
I'm having problems with the emerald theme manager. Every setting I modify isn't applied, I have to run "emerald --replace" each time I've changed something.

---

### Post by cjm5229 on 2007-10-20
> **yang said:**
> Actually, that's for getting the non-GPL'd themes. (That was working for me.)

On mine neither one worked until I did that, after I put that in both GPL"D and nonGPL'd worked.

---

### Post by mahendra on 2007-10-20
Same set of issues here. The most annoying thing is that after installing the emerald package, and -replace'ing it one time, emerald gets launched automatically at each session... and metacity too : very surprisingly, it made switching tabs in firefox very slow (that's what made me realize something was wrong !)

Maybe I have some other unknown tasks that slow down the system ;)

cheers,
mahen

---

### Post by DouglasAWh on 2007-10-24
> **gsiliceo said:**
> Have you already done:

sudo apt-get install emerald emerald-themes

?

I get 

```

whitdoug@linux-laptop:~$ sudo apt-get install emerald emerald-themes
[sudo] password for whitdoug:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package emerald-themes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emerald-themes has no installation candidate

```

What does that mean?

---

### Post by DouglasAWh on 2007-10-24
> **cjm5229 said:**
>  ```
sudo apt-get install subversion repositories
```  

I get

whitdoug@linux-laptop:~$ sudo apt-get install subversion repositories
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package repositories

---

### Post by Vorian on 2007-10-24
> **DouglasAWh said:**
> I get 
```

whitdoug@linux-laptop:~$ sudo apt-get install emerald emerald-themes
[sudo] password for whitdoug:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package emerald-themes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emerald-themes has no installation candidate

```What does that mean?
emerald-themes is not in gutsy, it is in feisty however [http://packages.ubuntu.com/feisty/x11/emerald-themes](http://packages.ubuntu.com/feisty/x11/emerald-themes)


> **DouglasAWh said:**
> I get

whitdoug@linux-laptop:~$ sudo apt-get install subversion repositories
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package repositoriesjust install subversion  
$sudo apt-get install subversion

---

### Post by LinuxSaab on 2007-10-25
Linux noob here... I've finally gotten compiz working, and installed emerald themes manager and I have some issues.
1. I have themes showing in emerald themes manager, however when I select one nothing changes.
2. I have no title bar (with close, minimize, maximize, etc) there are just small "tabs" at each corner of each window I open.  If I move my mouse in the general area where the buttons should be, I can use the (close, minimize, etc).
3. When I use a quick launch icon from my task bar such as firefox or a terminal window, I end up with "tracers" so to speak that don't go away until I restart...

I'm running on a dell 9400, 7.04 feisty.

Please help, if any screen shots or anything is needed please let me know.
Thanks,
E

---

### Post by paulg on 2007-10-25
> **LinuxSaab said:**
> Linux noob here... I've finally gotten compiz working, and installed emerald themes manager and I have some issues.
1. I have themes showing in emerald themes manager, however when I select one nothing changes.
2. I have no title bar (with close, minimize, maximize, etc) there are just small "tabs" at each corner of each window I open.  If I move my mouse in the general area where the buttons should be, I can use the (close, minimize, etc).
3. When I use a quick launch icon from my task bar such as firefox or a terminal window, I end up with "tracers" so to speak that don't go away until I restart...

I'm running on a dell 9400, 7.04 feisty.

Please help, if any screen shots or anything is needed please let me know.
Thanks,
E

E, I believe you need to restart X in order to make changes. Any of these should do it just make sure you've saved your work.

```
ctrl+alt+backspace
sudo /etc/init.d/gdm restart (or kdm for kubuntu) -> should work, haven't tested
Restart your system as you normally would from the menu.

```

---

### Post by cjm5229 on 2007-10-26
You need to go to your Compiz Config Settings Manager and in the Effects section check Window Decoration. Then you need to click on it and type the command "emerald" in the line that says command. Restart Compiz and you shoukd be good.

---

### Post by ic00 on 2007-10-26
Emerald is in Feisty repository. I had Beryl and Emerald, and then upgraded to Gusty. In Gusty I only removed Beryl and kept Emerald. Now Emerald works with Compiz Fusion like charm. I am very pleased.

---

### Post by DouglasAWh on 2007-10-29
> **Vorian said:**
> 
just install subversion  
$sudo apt-get install subversion

Sweet!!!

Now, to fix all the other problems!

---

### Post by Vorian on 2007-10-29
just so you know... :)  Compiz uses git for revision controll

$ sudo apt-get install git-core

---

### Post by beng165 on 2008-05-21
Tried that, but when I was downloading emerald, I got the following output

Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xgl is already the newest version.
Package emerald-themes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emerald-themes has no installation candidate

---

### Post by gsiliceo on 2008-05-21
Visit this page to get emerald themes, 
[http://themes.beryl-project.org/](http://themes.beryl-project.org/)
You installed them using the emerald theme manager in preferences.

---

