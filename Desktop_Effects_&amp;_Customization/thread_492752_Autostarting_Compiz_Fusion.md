---
title: "Autostarting Compiz Fusion"
date: 2007-07-05
forum: Desktop Effects &amp; Customization
---

### Post by shafin on 2007-07-05
How do I autostart Compiz Fusion Each time Ubuntu Starts?
I'm on Feisty 64 bit.

---

### Post by kevinlyfellow on 2007-07-05
The desired way of doing this is to open up gconf-editor (alt-f2 and run the command gconf-editor) and then navigate to '/desktop/gnome/applications/window_manager' and change the value of "default" to "/usr/bin/compiz"

But be warned, some users have experienced (extremely) slow login times doing it this way.  But try it first, if it doesn't work I'll give you the work around.

---

### Post by shafin on 2007-07-05
Thanks a lot

---

### Post by shafin on 2007-07-05
Man,I cant battle the urge to thank you again after I restart.

Works like a charm on my GMA950,no slowdowns :)

---

### Post by moredhel on 2007-07-05
awesome, I was wondering how to do this as well. For some reason when I added it to autostart programs in sessions it didn't play nicely :\

---

### Post by shafin on 2007-07-05
Now I have another question,How can I aurostart any other app in ubuntu?

I want tomboy to start each time I log in

---

### Post by AlexenderReez on 2007-07-05
actually the easiest way is to use 'session' which is under ---> system ....it state there auto start ...i used to put compiz --replace && emerald --replace ......

---

### Post by kevinlyfellow on 2007-07-05
> **shafin said:**
> Now I have another question,How can I aurostart any other app in ubuntu?

I want tomboy to start each time I log in

Actually, though I was tempted to startup tomboy when logging in and having it become a big mess, someone on the forums pointed out to me that there is an applet for it.  Just right click on the panel and "add to panel"

But you should still know how to start things up.  Under System -> Preferences -> Sessions  the first tab is for adding extra startup programs.  It's pretty self-explanatory, just add a new one and enter the command you want it to run.

---

### Post by kevinlyfellow on 2007-07-05
> **reez0105 said:**
> actually the easiest way is to use 'session' which is under ---> system ....it state there auto start ...i used to put compiz --replace && emerald --replace ......

Yes, but then you load metacity first, and then replace it with compiz.  It's a great workaround, but technically not the right way of doing it.  Many people need to do it this way because of an old bug that beryl had (the merger put the bug into compiz) where nautilus would hang on startup for about a minute.

---

### Post by shafin on 2007-07-06
> **kevinlyfellow said:**
> The desired way of doing this is to open up gconf-editor (alt-f2 and run the command gconf-editor) and then navigate to '/desktop/gnome/applications/window_manager' and change the value of "default" to "/usr/bin/compiz"

But be warned, some users have experienced (extremely) slow login times doing it this way.  But try it first, if it doesn't work I'll give you the work around.
When I use this,How do I autostart emerald?

---

### Post by Raineer on 2007-07-06
> **kevinlyfellow said:**
> Yes, but then you load metacity first, and then replace it with compiz.  It's a great workaround, but technically not the right way of doing it.  Many people need to do it this way because of an old bug that beryl had (the merger put the bug into compiz) where nautilus would hang on startup for about a minute.

I still have this bug, it seems no matter what I do it doesn't go away.  However, I can't even find anything on google discussing the bug, this is the first time I've read about it.

Placing compiz in my gconf-editor doesn't make it load right off, and (when I have the nautilus hang), it never seems to load from rc.local either. I can work around it with the console no problem, just wish I didn't have to every time I start X

---

### Post by mjpoetic on 2007-07-06
I think the absolute best way is to install the fusion-icon package from the repository of shame.  Go to [http://shame.tuxfamily.org/repo/](http://shame.tuxfamily.org/repo/)

The current fusion-icon deb package is here:
[http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/](http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/)

The package would read something like:
***[COLOR=DarkSlateBlue]"fusion-icon****.deb"[/COLOR]***

After installing, just start it using fusion-icon or fusion-manager (or put that command in your gnome-session-properties startup).  For you newbies...on your Ubuntu menubar go:

System ---> Preferences ---> Sessions

---

### Post by kevinlyfellow on 2007-07-06
You can put compiz and emerald into the gnome-sessions and put metacity into gconf-editor.  For discussion on this, go to [http://ubuntuforums.org/showthread.php?t=482776](http://ubuntuforums.org/showthread.php?t=482776)

---

### Post by jdriessen on 2007-07-08
I have gotten a little lost in the midst of all the threads and discussion on how to autostart Compiz Fusion.

I really liked kevinlyfellows method of setting compiz as default window manager in gconf-editor.
when I have this enabled compiz seems to start much better than when I added a startup command, secifically compiz --replace.
thing is... (and here it comes) I'm using emerald window decorator, and when I enabled compiz using kevinlyfellow's method, I was unable to start emerald window decorator using emerald --replace. so in the end I have to envoke the full "compiz --replace -c emerald &" command, to make sure my window borders are working properly.

has anybody successfully managed to get compiz fusion with emerald working, with compiz starting the proper way (kevinlyfellow method) and emerald starting at login/boot?

My whole reason for changing the way compiz starts was because it was taking quite long to login and it looked pretty ugly. (kevinlyfellow's method improves this)
although I would much prefer if i could edit the boot order to put compiz and emerald much earlier on in the chain so that I get a much smoother transition from GDM to my desktop.

---

### Post by kevinlyfellow on 2007-07-08
> **jdriessen said:**
> I have gotten a little lost in the midst of all the threads and discussion on how to autostart Compiz Fusion.

I really liked kevinlyfellows method of setting compiz as default window manager in gconf-editor.
when I have this enabled compiz seems to start much better than when I added a startup command, secifically compiz --replace.
thing is... (and here it comes) I'm using emerald window decorator, and when I enabled compiz using kevinlyfellow's method, I was unable to start emerald window decorator using emerald --replace. so in the end I have to envoke the full "compiz --replace -c emerald &" command, to make sure my window borders are working properly.

has anybody successfully managed to get compiz fusion with emerald working, with compiz starting the proper way (kevinlyfellow method) and emerald starting at login/boot?

My whole reason for changing the way compiz starts was because it was taking quite long to login and it looked pretty ugly. (kevinlyfellow's method improves this)
although I would much prefer if i could edit the boot order to put compiz and emerald much earlier on in the chain so that I get a much smoother transition from GDM to my desktop.

I think if you open up /usr/bin/compiz in your favorite editor and define the decorator variables, it will start up.

```

# Defines the decorator and arguments.
# Set it to empty to make the script use the best decorator for your environment
DECORATOR="emerald"
DECORATORARGS=""

```

---

### Post by jdriessen on 2007-07-08
> **kevinlyfellow said:**
> I think if you open up /usr/bin/compiz in your favorite editor and define the decorator variables, it will start up.

```

# Defines the decorator and arguments.
# Set it to empty to make the script use the best decorator for your environment
DECORATOR="emerald"
DECORATORARGS=""

```

I just tried that. no change. will keep searching around for a fix. anymore tips, much obliged.

---

### Post by kevinlyfellow on 2007-07-08
> **jdriessen said:**
> I just tried that. no change. will keep searching around for a fix. anymore tips, much obliged.

You know, I've messed around with all of this way too much.  I think it really is just easier to put the compiz replace and the emerald stuff as an extra startup program.  Messing around with gnome sessions is just way too hard for me... well, I'm off to compile a new kernel ;-)

---

### Post by Espreon on 2007-07-08
Actually the Easiest way is to install the Beryl Manager

sudo apt-get install beryl-manager

Then start it, right click the Ruby icon on the tray. Then select the WM to be Compiz
and select the Window Decorator to be Emerald.

Then goto System>Prefrences>Sessions and hit new
then name it Beryl Manager and enter beryl-manager in the command part.

Then hit ok and you are good 2 go.

---

### Post by jdriessen on 2007-07-09
> **Espreon said:**
> Actually the Easiest way is to install the Beryl Manager

sudo apt-get install beryl-manager

Then start it, right click the Ruby icon on the tray. Then select the WM to be Compiz
and select the Window Decorator to be Emerald.

Then goto System>Prefrences>Sessions and hit new
then name it Beryl Manager and enter beryl-manager in the command part.

Then hit ok and you are good 2 go.

yea, my point was i wanted to integrate compiz and emerald better into my session. so that I get a nice fluid transition from my GDM to the Desktop. ie. the splash screen staying active until everything had loaded up, and that there are no graphic glitches like white lines or bars on screen and redraws etc.

guess I should wait for Gutsy G. to be ready.

---

### Post by AlexenderReez on 2007-07-09
> **mjpoetic said:**
> I think the absolute best way is to install the fusion-icon package from the repository of shame.  Go to [http://shame.tuxfamily.org/repo/](http://shame.tuxfamily.org/repo/)

The fusion-icon deb package is here:
[http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/fusion-icon_0.1.1+git20070705-shame-0_i386.deb](http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/fusion-icon_0.1.1+git20070705-shame-0_i386.deb)

Then just start it using fusion-icon or fusion-manager (or put that command in your gnome-session-properties startup).  For you newbies...on your Ubuntu menubar go:

System ---> Preferences ---> Sessions

i use it....but as i'm using gutsy....there will broken if i only use that repo only...i need it to install plugin package....and the rest i use trevino package....

i used add compiz --replace and emerald --replace in my autostart....it is seems better for me rather than change it in gconfig ...i think because if i change the default...then if for sudden compiz stop working...it will give trouble to me(suppose to others too)...because when replacement decorator having problem,it will go to default decorator...but at the same time,the default also set that decorator to be decorator that having problem at the same time(compiz)....i'm working fine...but if you still having problem...how about creating autostart script....i think it is better...

p/s: hey Espreon,you are seems deidara fan...me too!...but i really hate latest naruto manga... sasuke defeated deidara ...damn..oh no..my hero got beaten ..:lolflag::lolflag:

---

### Post by UserXYZ on 2007-07-11
> **jdriessen said:**
> I just tried that. no change. will keep searching around for a fix. anymore tips, much obliged.

I got it working by putting emerald --replace as the decorator variable instead of just emerald.

---

### Post by staticsage on 2007-07-12
Edit: I'm actually still working on figuring this out... I had it working, but it's strange. Will post back if I come up with anything.

---

### Post by Espreon on 2007-07-12
> **reez0105 said:**
> i use it....but as i'm using gutsy....there will broken if i only use that repo only...i need it to install plugin package....and the rest i use trevino package....

i used add compiz --replace and emerald --replace in my autostart....it is seems better for me rather than change it in gconfig ...i think because if i change the default...then if for sudden compiz stop working...it will give trouble to me(suppose to others too)...because when replacement decorator having problem,it will go to default decorator...but at the same time,the default also set that decorator to be decorator that having problem at the same time(compiz)....i'm working fine...but if you still having problem...how about creating autostart script....i think it is better...

p/s: hey Espreon,you are seems deidara fan...me too!...but i really hate latest naruto manga... sasuke defeated deidara ...damn..oh no..my hero got beaten ..:lolflag::lolflag:

1st of all are using Gutsy as your main OS, if so bad idea, wait for Gutsy Beta at least!

2nd Yes I am a Deidara fan and I don't read Japanese Naruto manga (Shoenen Jump distributed, which I read is still to the part of defeating Gaara in giant Shukkau form), I watch Naruto Shippuden on the Net (Japanese +Subtitles). I am also a Sasori and Zetsu fan. Also I even watch the Fun with Akatsuki series.

---

### Post by macker3 on 2007-07-12
source: [http://illusion22.wordpress.com/2007/07/01/fusion-iconunaltra-tray-icon-per-compiz/](http://illusion22.wordpress.com/2007/07/01/fusion-iconunaltra-tray-icon-per-compiz/)

```
wget http://illusion22.interfree.it/fusion-icon.tar.gz
tar xzf fusion-icon.tar.gz
cd fusion-icon
sudo make install
fusion-icon
```

go to System > Preferences > Sessions

[New]
Name: Compiz Fusion
Command: fusion-icon
[OK]

;)

---

### Post by desJaCkAl on 2007-07-17
> **kevinlyfellow said:**
> Actually, though I was tempted to startup tomboy when logging in and having it become a big mess, someone on the forums pointed out to me that there is an applet for it.  Just right click on the panel and "add to panel"

But you should still know how to start things up.  Under System -> Preferences -> Sessions  the first tab is for adding extra startup programs.  It's pretty self-explanatory, just add a new one and enter the command you want it to run.
Using system-->preferences--> sessions, i then pressed new, and added Name: compiz Command: --replace

but when i restart...still compiz does't run automatically...what am i doing wrong?

TIA

---

### Post by macker3 on 2007-07-17
Command should be:
compiz --replace -c emerald &

it worked for me

---

### Post by desJaCkAl on 2007-07-18
that did it

Name: Compiz Fusion
Command: compiz --replace

Thank you macker3

---

### Post by Maci_01 on 2007-07-19
Can anyone help me out? When I login to my session using Gnome, Compiz-fusion fails to load automatically. The Gnome splash screen hangs there until I click on it. Metacity is loaded, I think. To load Compiz-fusion I have to hit alt-f2 and type 'compiz' or 'compiz &#8211;replace -c emerald &' or 'fusion-icon'. I tried adjusting gnome-session-properties (system>preferences>sessions) to load fusion-icon or compiz on startup but both fail to start. I also tried editing the variables in gconf-editor and also played around with the decorator settings in my compiz config file ( /usr/bin/compiz). Any help would be appreciated.

edit: my startup programs load but after about a minute. I suppose I'm in the wrong topic now sorry!

---

### Post by sssam on 2007-07-20
thanks to all its work on my amd athlon 2.400+ 1gb ram nvidia fx 5200gt with compiz fusion-icon

---

### Post by BDNiner on 2007-07-22
> **AlexenderReez said:**
> actually the easiest way is to use 'session' which is under ---> system ....it state there auto start ...i used to put compiz --replace && emerald --replace ......

This worked perfectly for me. I am loving Linux more and more. In fact i am going to build a more powerfull computer for ubuntu. i am currently using old spare parts that i had.

---

### Post by dk@ on 2007-07-30
Hello, guys.
Please help me.

I'v done following:
> The desired way of doing this is to open up gconf-editor (alt-f2 and run the command gconf-editor) and then navigate to '/desktop/gnome/applications/window_manager' and change the value of "default" to "/usr/bin/compiz"

Now after login I have just "blank screen" with mouse pointer. Nothing more. I can boot using Ubuntu Live and edit some file to get back "/usr/bin/metacity" value for "default" variable. But I don't know which one I should to edit (I'm new to Linux).

Please, give me some instructions to get back my previous window manager!

Thanks.

---

### Post by shafin on 2007-07-30
go to terminal in your live session.
Then open up your Computer from places,your ubuntu drive should be identified with something like "** GB volume".Enter it.Goto home,then to the folder with your user name.hit ctrl+h and go through the following directory.

***your user name***/.gconf/desktop/gnome/applications/window_manager

copy the address.

Then in termilnal write

sudo gedit ********/.gconf/desktop/gnome/applications/window_manager/%gconf.xml

*****---->paste the address here,it should be something like /media/sda1/home/shafin

and then change the values to /usr/bin/metacity

That would work.

---

### Post by dk@ on 2007-07-30
Thanks,

I'll try it this evening.

---

### Post by dingleberry420 on 2007-07-30
> **kevinlyfellow said:**
> I think if you open up /usr/bin/compiz in your favorite editor and define the decorator variables, it will start up.

```

# Defines the decorator and arguments.
# Set it to empty to make the script use the best decorator for your environment
DECORATOR="emerald"
DECORATORARGS=""

```

> **kevinlyfellow said:**
> The desired way of doing this is to open up gconf-editor (alt-f2 and run the command gconf-editor) and then navigate to '/desktop/gnome/applications/window_manager' and change the value of "default" to "/usr/bin/compiz"

But be warned, some users have experienced (extremely) slow login times doing it this way.  But try it first, if it doesn't work I'll give you the work around.

I used both of these together and compiz and emerald start up perfectly and it's way faster than using the session entry option.  One note however, when I first did this I forgot to uncheck/remove the session for compiz (compiz --replace -c emerald &) and my machine locked up.  I had to start with safe mode terminal only to run gconf-editor and reset it to metacity.  Once I did that I could login again, took out the session entry for compiz, reset the gconf-editor setting and it worked.

edit:  I also used "emerald --replace" not just "emerald".

---

### Post by dingleberry420 on 2007-07-30
> **dingleberry420 said:**
> I used both of these together and compiz and emerald start up perfectly and it's way faster than using the session entry option.  One note however, when I first did this I forgot to uncheck/remove the session for compiz (compiz --replace -c emerald &) and my machine locked up.  I had to start with safe mode terminal only to run gconf-editor and reset it to metacity.  Once I did that I could login again, took out the session entry for compiz, reset the gconf-editor setting and it worked.

edit:  I also used "emerald --replace" not just "emerald".

I guess I spoke too soon.  Everything worked except my desktop cube.  The horizontal size was stuck at 1 and when I tried to change it via compizconfig my system would lock and I would have to push the reset button.  I went back to the old session standby and I'm back in business.

FYI

---

