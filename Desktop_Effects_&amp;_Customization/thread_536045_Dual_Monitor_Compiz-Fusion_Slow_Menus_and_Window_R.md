---
title: "Dual Monitor Compiz-Fusion Slow Menus and Window Resize"
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by BitHosts on 2007-08-27
Hey all!

First off this is the story so far:

I have a machine at home and a few days ago I decided to rid myself of windows and move to Ubuntu.  As part of my move I decided to give compiz-fusion a try and whilst it wasn't easy getting to this stage I have it more-or-less working on my dual monitors.  I followed [this thread]("http://ubuntuforums.org/showthread.php?t=508769") to get as far as I have.

My machine spec:
Core 2 Duo 2.4Ghz
2Gb 667 Ram
Asus P5B Deluxe/Wifi
BFG 8800GTX

1x 19" Monitor @ 1280x1024 (Monitor A)
1x 24" Monitor @ 1920x1200 (Monitor B)

I ended up using two seperate x sessions without Xinerama turned on.  With it configured like this, when I login I have to run the Compiz Fusion Icon program to get it started, which then loads it entirely on monitor B and does everything except the window decoration on monitor A.  

To get monitor A with window decoration I have to run "emerald --replace &" in a root terminal on that monitor.  This much I can put up with, but the bit that confuses me follows:

On monitor A, once loaded everything runs smoothly no problems at all, but on monitor B all menus (main menu and right click etc) take a couple of seconds to load and when window resizes are in normal mode it takes about 20 seconds to resize a window. 

There is no spikes in CPU activity and it doesn't appear to be a memory leak as it is like this from the very beginning after a full reboot.

Now a temporary fix for the window resizing is to change the method from normal to stretch, it doesn't look as good - but its usable again.  But I haven't worked out the menu thing yet.

Any help or pointers would be much appreciated!

---

### Post by autocrosser on 2007-08-27
As you are using a Nvidia card you can edit your xorg.conf or use the Nvidia control panel to use one Xsession for both units..I run a 7600OC GS with two 19" flats. I am including my custom xorg.conf for you to look at.....I am off to work, so I will be able to talk more in about 10 hours.....

---

### Post by BitHosts on 2007-08-27
Thanks for the reply!

I did try and use one session originally before I tried using compiz-fusion, but unfortunately it meant that the top or bottom of my smaller resolution screen got cut off and things disappeared.  I will have a look at your xorg.conf and see if that helps.

Do you think that this would solve the issue of having slow menus and window resizing?

I make 10 hours from now about 1 in the morning here, so i might be asleep...  But I will reply as soon as I see a post!

---

### Post by autocrosser on 2007-08-28
Have you enabled the Nvidia Twinview? If you have installed Sysinfo (Menu>System Tools>Sysinfo)--it has a tab for the Nvidia setting control panel.

In the Setting panel there is a "X Server Display Configuration" tab. You can set X-Y offsets--panning within a window--metamodes & several other factors. This can enable you to use both screens at native resolution & create a single display--there is a tab at the bottom to save to a conf file. 

I try to use screens of the same size to avoid this problem, but I think that you can still do all of it with one X Server---I'm including the "heavy" reading from Nvidia--you need to look thru it to help---my copy is slightly dated (last year), but the info you need has not changed much.

Cheers!!!

---

### Post by BitHosts on 2007-08-28
OK, I have looked through both the documents you have sent me, and changed the offsets etc and the best I can get it to do is have both screens but with the smaller screen have the bottom cut off.

I have even re-installed so that I dont have any compiz-fusion stuff that could possibly be getting in the way.

I have attached my xorg.conf if that helps.

Thankyou!

---

### Post by autocrosser on 2007-08-29
Hi there---
I'll take a look at the xorg.conf tonight (about 4/6 hrs from now) & post back any thoughts---

---

### Post by autocrosser on 2007-08-29
Greetings!!

Take a look at this overview on panning----

  A MetaMode string can be further modified with a "Panning Domain"
    specification; e.g.:
    
        "1024x768 @1600x1200, 800x600 @1600x1200"
    
    A panning domain is the area in which a display device's viewport will be
    panned to follow the mouse. Panning actually happens on two levels with
    TwinView: first, an individual display device's viewport will be panned
    within its panning domain, as long as the viewport is contained by the
    bounding box of the MetaMode. Once the mouse leaves the bounding box of
    the MetaMode, the entire MetaMode (i.e. all display devices) will be
    panned to follow the mouse within the virtual screen. Note that individual
    display devices' panning domains default to being clamped to the position
    of the display devices' viewports, thus the default behavior is just that
    viewports remain "locked" together and only perform the second type of
    panning.

    The most beneficial use of panning domains is probably to eliminate dead
    areas -- regions of the virtual screen that are inaccessible due to
    display devices with different resolutions. For example:
    
        "1600x1200, 1024x768"
    
    produces an inaccessible region below the 1024x768 display. Specifying a
    panning domain for the second display device:
    
        "1600x1200, 1024x768 @1024x1200"
    
    provides access to that dead area by allowing you to pan the 1024x768
    viewport up and down in the 1024x1200 panning domain.

    Offsets can be used in conjunction with panning domains to position the
    panning domains in the virtual screen space (note that the offset
    describes the panning domain, and only affects the viewport in that the
    viewport must be contained within the panning domain). For example, the
    following describes two modes, each with a panning domain width of 1900
    pixels, and the second display is positioned below the first:
    
        "1600x1200 @1900x1200 +0+0, 1024x768 @1900x768 +0+1200"
    
    Because it is often unclear which mode within a MetaMode will be used on
    each display device, mode descriptions within a MetaMode can be prepended
    with a display device name. For example:
    
        "CRT-0: 1600x1200,  DFP-0: 1024x768"
    
    If no MetaMode string is specified, then the X driver uses the modes
    listed in the relevant "Display" subsection, attempting to place matching
    modes on each display device.


It would look like this is what you need to do, whilst keeping both screens at native resolution.

---

### Post by Bil-E-daKid on 2007-09-02
Hey there!

Just wondered if you managed to get the menu/resize thing fixed?  I'm having the exact same problem at the moment.

:-)

---

### Post by ner0tic on 2007-09-09
> **Bil-E-daKid said:**
> Hey there!

Just wondered if you managed to get the menu/resize thing fixed?  I'm having the exact same problem at the moment.

:-)

i'm in the same boat.. any resolutions?

---

### Post by Bil-E-daKid on 2007-09-09
Not that I've found so far sorry.

---

### Post by DeepThoughts on 2007-09-10
Add me to the crowd with the slow menus and resizing. From my research I've concluded that it's only GTK that is suffering from this issue.

I noticed this when running Virtualbox (made in QT) yesterday and I confirmed this with Skype. On my machine it's only GTK-apps that are affected (or not QT-apps, but since I only have GTK and QT I can't confirm which).

Can someone else confirm that this is a GTK-issue?

---

### Post by Bil-E-daKid on 2007-09-10
Wow - hadn't even thought of that.  I just tried resizing a k3b window (QT) and it works fine.

Thunderbird, firefox, VMWare console, gnome-terminal (all GTK I'm assuming) exhibit the problem.

---

### Post by stevejesus on 2007-09-22
Same problem here.  Even noteworthy composer (wine) resizes quickly and has fast response clicking on menus.  This is definitely a GTK issue.

---

### Post by gtaluvit on 2007-09-25
I seem to have the same problem but also a temporary workaround.  With today's updates to Gutsy, I wanted to see if I could finally use the Appearance tab to do compiz instead of my manual method.  Basically, I have the problem of wanting to run compiz on one monitor but not the other as it's not supported.  Here's basically what I see:

If I run compiz using the Appearance preference bar, compiz tries to load on both monitors.  I seem to have wobbly windows and such on my main, not on my secondary.  I don't have any window decoration at all on my secondary.  Also, on my main screen, menus are very slow.

If I run compiz delayed 5 seconds as a session startup (and have it only replace my main screen), then I have compiz running on my main, and metacity on the secondary.  Both seem to work fine without any menu issues.

So, I would suggest the following script to add to your session:

```

#!/bin/bash
sleep 5
compiz --replace --only-current-screen &
gtk-window-decorator --replace &

```

---

### Post by oderus on 2007-09-28
I have a similar setup. I have a laptop with an Nvidia card and I have two displays, the 1440x900 native LCD on the laptop and a 1280x1024 Dell 19" LCD panel. I have 64-bit Gutsy loaded with Compiz-Fusion, Nvidia 100.14.x drivers and with separate screens, everything works well. Speed of menus on both are the same.

I noticed that Compiz-Fusion has a setting for each screen. Perhaps you have something like 'blur' enabled on the one screen and that is slowing it down. Perhaps your animations aren't setup the same and are taking more time than your other screen. I noticed that all my animations were different depending on which monitor I opened them up with. I don't want Xinerema due to the dead space but I'll try the steps that autocrosser provided and see how well that works with my setup.

Hope that helps.

---

### Post by schneiko on 2007-10-22
> **gtaluvit said:**
>  

So, I would suggest the following script to add to your session:

```

#!/bin/bash
sleep 5
compiz --replace --only-current-screen &
gtk-window-decorator --replace &

```

This solves the problem on my computer. Thanks a lot for this trick. I don't need compiz on the other screen (TV) at all, so this is a very good solution for me.

---

### Post by Linder on 2007-10-22
Same boat, same problem. :(

---

### Post by darigaz625 on 2007-10-22
i have a similar problem... i can't even get compiz to run on my dualscreen setup using xinerama one screen is @ 1280x124 and the other one @ 1024x768...

whenever i try to enable visual effects i get the error "desktop effects couldn't be enabled"

any ideas what i'm doing wrong?

---

### Post by Bil-E-daKid on 2007-10-22
Great workaround for the slow menus thanks!  I use the 2nd monitor for a windows terminal server session so don't need any special effects there either.

The resizing in gutsy works differently so isn't a problem anymore but the slow menu problem still is.  WIth starting Compiz via this script (mentioned above), the menus are real quick again.

Awesome!

---

### Post by ktulu1115 on 2007-10-23
I believe it's a GTK-only issue as well.

There's a bug filed for it - [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/)

---

### Post by galv on 2007-10-30
1+ here :(
The workaround works

---

### Post by kierskoe on 2007-10-31
> **gtaluvit said:**
> I seem to have the same problem but also a temporary workaround.  With today's updates to Gutsy, I wanted to see if I could finally use the Appearance tab to do compiz instead of my manual method.  Basically, I have the problem of wanting to run compiz on one monitor but not the other as it's not supported.  Here's basically what I see:

If I run compiz using the Appearance preference bar, compiz tries to load on both monitors.  I seem to have wobbly windows and such on my main, not on my secondary.  I don't have any window decoration at all on my secondary.  Also, on my main screen, menus are very slow.

If I run compiz delayed 5 seconds as a session startup (and have it only replace my main screen), then I have compiz running on my main, and metacity on the secondary.  Both seem to work fine without any menu issues.

So, I would suggest the following script to add to your session:

```

#!/bin/bash
sleep 5
compiz --replace --only-current-screen &
gtk-window-decorator --replace &

```

Great stuff, thanks for this, had been bugging me for ages and this worked a charm.

Just one thing though,..

My primary monitor is out DVI and secondary LCD(TV) is through VGA, the title bars of windows do not show on the secondary LCD .. any suggestions?

---

### Post by TB2 on 2007-11-08
This is a bit funny. I'm using two X screens, both with Compiz-Fusion activated.

I have exactly the same symptoms as you have, but there is an extension of this workaround, which makes using CF on both screens possible without the menus delaying:

1. Put the script in you sessions, as you already did.
2. Copy two instances of the script, e.g. "script0.sh" and "script1.sh" to your desktop and place script1.sh on the second screen. (They must have different names because both desktops share the same directory)
3. If you log in, CF / emerald will start on the primary screen because of your sessions settings, no borders on the second screen.
4. Start the script1.sh on the second screen, you will loose the borders on the first screen.
5. Start the script0 on the primary screen again, you will get borders on that screen, too, and on my side, the menus now react instantly.

Don't know why this works, but here it does ^^ So, the script needs to be run three times, primary->secondary->primary, and you will get CF working with beryl and not-lagging menus on both screens ^^

Does someone know how to automate this?

---

### Post by hihihi on 2007-11-12
hey,

i made two scripts, which detect if there is a second monitor (mine is a TV) or not,
it spares you some 5seconds at least:



#!/bin/bash
#switch between compiz 2 screens or 1 screen
VIDEOCARD1=`/bin/cat /var/log/Xorg.0.log |grep -c TV-0`
if [ "$VIDEOCARD1" = 0 ]; then
sleep 0
else
sleep 5
compiz --replace --only-current-screen &
emerald --replace &
fi

IN CASE YOU WANT DECO ON BOTH (but than menus are slow again):


#!/bin/bash
#switch between compiz 2 screens or 1 screen
VIDEOCARD1=`/bin/cat /var/log/Xorg.0.log |grep -c TV-0`
if [ "$VIDEOCARD1" = 0 ]; then
sleep 0
else
compiz --replace &
sleep 5
emerald --replace --display :0.1 &
sleep 5
emerald --replace
fi


:lolflag:

---

### Post by galv on 2007-11-12
Can someone explain me how it works? Who does compiz it has to replace stuff on screen0 (monitor) and metacity that it has to replace stuff on screen1 TV

Thanks :D

---

### Post by Yoooder on 2007-11-15
*happy sigh*  I've been using Gutsy since Tribe 5 and have just gotten used to the slow menu issue whenever I enable Compiz (not all that often).

I thought it was just my lil old machine until a friend's $3000 box had the same problem.  Thanks for the work, guys!

---

### Post by chewearn on 2007-11-25
> **TB2 said:**
> This is a bit funny. I'm using two X screens, both with Compiz-Fusion activated.

I have exactly the same symptoms as you have, but there is an extension of this workaround, which makes using CF on both screens possible without the menus delaying:

1. Put the script in you sessions, as you already did.
2. Copy two instances of the script, e.g. "script0.sh" and "script1.sh" to your desktop and place script1.sh on the second screen. (They must have different names because both desktops share the same directory)
3. If you log in, CF / emerald will start on the primary screen because of your sessions settings, no borders on the second screen.
4. Start the script1.sh on the second screen, you will loose the borders on the first screen.
5. Start the script0 on the primary screen again, you will get borders on that screen, too, and on my side, the menus now react instantly.

Don't know why this works, but here it does ^^ So, the script needs to be run three times, primary->secondary->primary, and you will get CF working with beryl and not-lagging menus on both screens ^^

Does someone know how to automate this?

Based on TB2 idea of running separate instance of compiz for each screen, I saw a tip here on how to do that:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/comments/11](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/comments/11)

Thus, this simple script works for me (add into Sessions> Startup Programs):

```
#!/bin/bash
DISPLAY=:0.0 compiz --only-current-screen &
DISPLAY=:0.1 compiz --only-current-screen &

```

So, dual screen compiz, no more pop-up menu lag.
:guitar:

---

### Post by NoThanksM$ on 2007-11-25
The workaround does the trick, thank you!

---

### Post by ktulu1115 on 2007-11-26
sweet!  this worked perfectly.  many thanks. :)

someone needs to sticky this.

---

### Post by woodsby on 2007-11-27
Script worked for me - no more slow menus - woohoo!

---

### Post by L1NU5 on 2007-11-28
Thanks AstalaVista, your Script solves the delay-problem for me.
But it brings up another problem :confused:
If i use the script, I have no window-decorations, not on the first nor on the second screen.

Anyone else got this problem, or any ideas to solve it?

This damn dual-monitor problem is driving me crazy...

---

### Post by Bil-E-daKid on 2007-11-28
Hey there L1NU5,

You and me both - I did have it all working using the scripts and then - all of a sudden - no more window decorations.  If I ditch the script the windecs come back so do the slow menus.

Better having slow menus than not being able to move windows around - but it would be nice to have it working again!  :-)

---

### Post by chewearn on 2007-11-28
> **L1NU5 said:**
> Thanks AstalaVista, your Script solves the delay-problem for me.
But it brings up another problem :confused:
If i use the script, I have no window-decorations, not on the first nor on the second screen.

Anyone else got this problem, or any ideas to solve it?

This damn dual-monitor problem is driving me crazy...

I did not see this problem, so I will not be able to find the exact fix for you.  But, I think there are sufficient info in this thread for you to experiment with the commands that might solve it.

Some hints:
When your window decorations went missing, you run this command to bring it back:

If you use gtk-window-decorator:
```
gtk-window-decorator --replace &
```

If you use emerald:
```
emerald --replace &
```

Try adding one of the commands into the script; try also add a delay between the commands, if it doesn't work.

For 5 seconds delay:
```
sleep 5
```

If one screen has decoration, while the other don't, use the display option, e.g.:
```
 emerald --replace --display :0.1 &
```

Good luck!:)

---

### Post by L1NU5 on 2007-11-29
Thanks for you help!

But I tried all that before. When I use your script and add
```
gtk-window-decorator --replace
```
I get my decorations on the first screen and no slowdown, but on my second screen (my TV) there are no decorations. When I replace the decorations on the TV they disappear on my first screen...

I had allready given up, but then I switched from Metacity to Emerald and well... 
your script works like a charm :)

**So everyone having decoration-issues, try Emerald instead of Metacity.**

Thanks for your replies!

Linus

---

### Post by hihihi on 2007-12-02
when compiz enabled, i have no keyboard access on my second xscreen!!
NOBODY HAS THAT ISSUE?
this work-arround helped to get first xscreen more responsive, but i can not write nor commandd anything with on second xscreen...
anybody?? :(

---

### Post by hihihi on 2007-12-16
unbelieveble but must be the truth, nobody seems to use the keyboard on second xscreen,
so why people do you in havens name need xscreen? u could use twinview, there this issue does not happen. but i cannot believe that anybody is not using keyboard on the second xscreen...

---

### Post by chewearn on 2007-12-16
> **hihihi said:**
> unbelieveble but must be the truth, nobody seems to use the keyboard on second xscreen,
so why people do you in havens name need xscreen? u could use twinview, there this issue does not happen. but i cannot believe that anybody is not using keyboard on the second xscreen...

I used keyboard in the second screen all the time.  I didn't see the problem you are facing, so I don't have a straight working solution to offer.  What you might be able to do is look into the /var/log/Xorg.0.log (or other system logs) to see if there is any hint about your problem.

When I was tinkering with dual screens setup a couple of months back, I struggle for hours trying different combination.  I couldn't get twinview to work the way I wanted, and the best solution I can live with is via two separate screens.

---

### Post by hihihi on 2007-12-18
thx for your answer!!
are u working with keyboard and compiz on second xscreen????
i chcked my XOrg.log file and its ok.
the thing is: all works fine when running dual xscreens WITHOUT compiz.
WITH compiz no keyboard on second xscreen.
it works fine with twinview and compiz though.
i need xscreens for live performing video. video-quality is 1100 times better than with twinview. and while live performing i need keyboard on 2. xscreen.
when i am performing live on stage i will use fluxbox-window-manager without fancy effects anyway to have more power, but in daily live would be nice to be able to run the live-video-apps without having to leave GNOME, restart xserver or have to switch off glx/compiz/effects....

---

### Post by chewearn on 2007-12-18
> **hihihi said:**
> thx for your answer!!
are u working with keyboard and compiz on second xscreen????
i chcked my XOrg.log file and its ok.
the thing is: all works fine when running dual xscreens WITHOUT compiz.
WITH compiz no keyboard on second xscreen.
it works fine with twinview and compiz though.
i need xscreens for live performing video. video-quality is 1100 times better than with twinview. and while live performing i need keyboard on 2. xscreen.
when i am performing live on stage i will use fluxbox-window-manager without fancy effects anyway to have more power, but in daily live would be nice to be able to run the live-video-apps without having to leave GNOME, restart xserver or have to switch off glx/compiz/effects....

In my set-up, I have the second screen connected to my LCD TV to watch video on my couch.  I use RF keyboard and mouse to operate in the second screen, like a remote control.  So, really, I don't have keyboard problem for the second screen.  Apologized, I can't help you any further than that, as I have not encounter your problem.

Though, I really share you pain and frustration.  I have been encountering random system lock-up ever since I started using Gutsy.  After numerous trial and errors, I almost have it figured that the hard-lock went away when compiz is off.

I thought Gusty is finally the one with a working stable 3D desktop (for my set-up); guess I have to wait for Hardy.

---

### Post by hihihi on 2007-12-19
thanks for your kind reply and  good link on your signature BTW.
i am not frustrated yet as ubuntu / linux is so cool, it improved amazingly over the last years and there are always good solutions or alternatives when something is not working right away, i was just wondering that nobody nearly seems to be complaining about the missing keyboard support on second xscreen. till now i found just one person on launchpad, and he is the only one so far... so that means that people are probably not encountering the same problem as me and another one.... aha... ok than, lets wait for hardy, no question about that.
btw, i heard its probably a GNOME bug, issues with compiz desktop, but i am not sure...
ok, cheers!! :popcorn:  and enjoy the films on your couch!!

---

### Post by lobo-tuerto on 2008-01-10
> **AstalaVista said:**
> Based on TB2 idea of running separate instance of compiz for each screen, I saw a tip here on how to do that:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/comments/11](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/comments/11)

Thus, this simple script works for me (add into Sessions> Startup Programs):

```
#!/bin/bash
DISPLAY=:0.0 compiz --only-current-screen &
DISPLAY=:0.1 compiz --only-current-screen &

```

So, dual screen compiz, no more pop-up menu lag.
:guitar:

Hello, I'm new to Ubuntu, and I'm having the same problem you describe here (slow popup menus and windows). I was wondering how can I include those 3 lines in my Sessions > Startup Programs, since you can only enter 1 line with the "new" button.

Or where should I include those 3 lines? or do I need to enter 3 different commands for it?

---

### Post by chewearn on 2008-01-10
> **lobo-tuerto said:**
> Hello, I'm new to Ubuntu, and I'm having the same problem you describe here (slow popup menus and windows). I was wondering how can I include those 3 lines in my Sessions > Startup Programs, since you can only enter 1 line with the "new" button.

Or where should I include those 3 lines? or do I need to enter 3 different commands for it?

Create a text file at a convenient location, e.g.
```
gedit ~/startcompiz.sh
```Copy/paste the codes:
```
 #!/bin/bash
sleep 5
DISPLAY=:0.0 compiz --only-current-screen &
DISPLAY=:0.1 compiz --only-current-screen &
```

Save and close the editor.  Then run this command to allow the file to execute:
```
chmod +x startcompiz.sh
```Then, add startcompiz.sh into Sessions > Startup Programs.


Note:
I found I have to add the "sleep 5" on the second line, else the PC will sometimes got "stuck" during boot.

---

### Post by gkzhang on 2008-02-04
hey guys, I tried the solution posted in the last response and it didn't quite work for me.  
Instead now when I log in, I just get my mouse cursor, the solid Ubuntu Orange color as the background, and the startup sound.  It just hangs there.  

I tried adding in the sleep 5 option, but it still didn't work.  The weird thing now is that even if i remove the script or change the script, it still hangs and does nothing.  I tried to go to Failsafe Gnome and same thing.  I've tried messing with my xorg.conf as well and no luck there either?  Any suggestions or am i really s*** f***ed?

---

### Post by nstamoul on 2008-02-16
This may not help you at all but I have the exact same problem due to another reason.

Anyway as a workaround go into console using control+alt+F1,go to init 1and then back to init 2.Restart gdm and you should be in gnome ;)

Tell me if this helps you at all.

---

### Post by csiemantel on 2008-02-22
Thank you AstalaVista!  My menus on screen0 are now running at normal speed again.  One thing I also had to do to was remove the other compiz entry I had for Sessions->Startup Programs once I added your script.  After that everything works great.

Thanks again!!

---

### Post by lfjewett on 2008-02-26
> **L1NU5 said:**
> Thanks for you help!

But I tried all that before. When I use your script and add
```
gtk-window-decorator --replace
```
I get my decorations on the first screen and no slowdown, but on my second screen (my TV) there are no decorations. When I replace the decorations on the TV they disappear on my first screen...

I had allready given up, but then I switched from Metacity to Emerald and well... 
your script works like a charm :)

**So everyone having decoration-issues, try Emerald instead of Metacity.**

Thanks for your replies!

Linus

How exactly does one do this?  I can't seem to get window decorations to draw and it seems when using the above script I have to use --replace

---

### Post by L1NU5 on 2008-02-26
> **lfjewett said:**
> How exactly does one do this?  I can't seem to get window decorations to draw and it seems when using the above script I have to use --replace

Using Emerald instead of Metacity fixed my problem.
You can install it with:
```
sudo apt-get install emerald
```

This is the startup-script I use:
```
#!/bin/bash
DISPLAY=:0.1 compiz --only-current-screen &
DISPLAY=:0.0 compiz --only-current-screen &
```

---

### Post by cfmunster on 2008-03-13
autocrosser's xorg.conf setup worked for me, now I have both displays working correctly, with window borders, effects, etc. and no annoying double menu system like normal Twinview. Thanks autocrosser!

---

### Post by MountainX on 2008-03-22
I solved my similar problem. It is described in this thread:

[http://forum.compiz-fusion.org/showthread.php?t=6687](http://forum.compiz-fusion.org/showthread.php?t=6687)

I ended up purchasing a new video card and hand-editing my xorg.conf file (which is attached to the above post)

Hope that helps someone.

---

### Post by marriouss on 2008-03-28
The same issue in Hardy Beta. The compiz --only-current-screen option makes slow menus issue go away, but on the second screen, there are no window borders, nor does the keyboard work (its seems to work when I fullscreen a movie with smplayer). 

Without --only-current-screen, compiz animations seem to work on both screen, but with slow menus, slow unminimize, on the first screen.

---

### Post by chewearn on 2008-03-28
> **marriouss said:**
> The same issue in Hardy Beta. The compiz --only-current-screen option makes slow menus issue go away, but on the second screen, there are no window borders, nor does the keyboard work (its seems to work when I fullscreen a movie with smplayer). 

Without --only-current-screen, compiz animations seem to work on both screen, but with slow menus, slow unminimize, on the first screen.

Does it work, if you follow L1NU5 post #47 above?

---

### Post by forestpixie on 2008-04-12
Thank you thank you thank you - thought I'd have another bash with compiz and the awful delay - found this and have got compiz on both monitors with no delays anywhere at all :D

Edit - had found a similar script once before but it didn't work and I gave up trying and turned it off, so it was nice to find this and turn compiz on again.

---

### Post by bve on 2008-04-12
> **gtaluvit said:**
> I seem to have <snip>...</snip>
If I run compiz delayed 5 seconds as a session startup (and have it only replace my main screen), then I have compiz running on my main, and metacity on the secondary.  Both seem to work fine without any menu issues.

So, I would suggest the following script to add to your session:

```

#!/bin/bash
sleep 5
compiz --replace --only-current-screen &
gtk-window-decorator --replace &

```

This is working for me too, thanks.

---

### Post by notquitemichael on 2008-04-14
it seems you've already got there: but here's what i've just added to the bug-fix on launchpad:

With Hardy, the compiz seems to support the hack i used in Beryl. Here's a solution:

make a script with these two lines (i.e. ~/.compiz-dual.sh)

## start compiz
DISPLAY=:0.0 compiz --only-current-screen --replace &
sleep 3
DISPLAY=:0.1 compiz --only-current-screen --replace &

then in gnome-session-manager add a new program:
sh ~/.compiz-dual.sh

this hack just runs a simple script a log-in, if you use the defualt name it's hidden, the script restarts compiz as two seperate sessions along both heads: note the DISPLAY=#.# line. You might need to change the numbers, a quick way to test weather your screens are 0.1 and 0,0 is to run (from the terminal,):

DISPLAY=:#.# gedit

that'll open gedit on which ever screen the numbers relate to.

i can confirm this works fine.

---

### Post by marriouss on 2008-04-18
*notquitemichael: the script works great. Now I've compiz on both screens and the menus are slow no more!!! :guitar:

I've made the following:
1. compiz-dual.sh script that looks like:
> #!/bin/sh
DISPLAY=:0.0 compiz --only-current-screen &
sleep 3
DISPLAY=:0.1 compiz --only-current-screen &
sleep 3
DISPLAY=:0.0 avant-window-navigator &
DISPLAY=:0.1 avant-window-navigator &

2. Added compiz-dual.sh to gnome startup (System->Preferences->Sessions)

3. Appearance->Visual effects - Set to None.

!Ubuntu Hardy rc

---

### Post by marriouss on 2008-04-18
A more nicer compiz-multi.sh script would look like this:

> #!/bin/sh

xdpyinfo -display :0.0 > /dev/null 2>&1
if [ $? -eq 0 ]
then
	DISPLAY=:0.0 compiz --only-current-screen &
	DISPLAY=:0.0 avant-window-navigator &
#	echo "Screen :0.0 ok"
fi

xdpyinfo -display :0.1 > /dev/null 2>&1
if [ $? -eq 0 ]
then
	sleep 3
	DISPLAY=:0.1 compiz --only-current-screen &
	DISPLAY=:0.1 avant-window-navigator &
#	echo "Screen :0.1 ok"
fi

xdpyinfo -display :1.0 > /dev/null 2>&1
if [ $? -eq 0 ]
then
	DISPLAY=:1.0 compiz --only-current-screen &
	DISPLAY=:1.0 avant-window-navigator &
#	echo "Screen :1.0 ok"
fi

xdpyinfo -display :1.1 > /dev/null 2>&1
if [ $? -eq 0 ]
then
	sleep 3
	DISPLAY=:1.1 compiz --only-current-screen &
	DISPLAY=:1.1 avant-window-navigator &
#	echo "Screen :1.1 ok"
fi


If anyone knows a better way of testing/retrieving the list of the available X screens ...

---

### Post by Davidux on 2008-04-22
> **AstalaVista said:**
> Based on TB2 idea of running separate instance of compiz for each screen, I saw a tip here on how to do that:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/comments/11](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/comments/11)

Thus, this simple script works for me (add into Sessions> Startup Programs):

```
#!/bin/bash
DISPLAY=:0.0 compiz --only-current-screen &
DISPLAY=:0.1 compiz --only-current-screen &

```

So, dual screen compiz, no more pop-up menu lag.
:guitar:

you are my hero ;)
thanks! :lolflag:

---

### Post by gupi-gupi on 2008-04-23
it used to work fine with the script > #!/bin/bash
DISPLAY=:0.0 compiz --only-current-screen &
DISPLAY=:0.1 compiz --only-current-screen & untill this new 8.04 hardy, now when I start my machine on screen 0 I get this bug where any dropdown menu just don't show up, on second screen they do worck:confused: , any suggestion?

edit: I'm getting mad, tried evry script on the thred, still without menudropdown. just to know... anyone else with this problem in hardy?

---

### Post by Tristan Schmelcher on 2008-04-26
Sorry gupi-gupi, I'm on Hardy final and the workaround is still working for me. This is the script I'm using:

#!/bin/bash
# start compiz
DISPLAY=:0.0 compiz --only-current-screen --replace &
disown $!
sleep 3
DISPLAY=:0.1 compiz --only-current-screen --replace &
disown $!

FYI, the entry in Launchpad for this bug is:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/149764](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/149764)

---

### Post by gupi-gupi on 2008-04-26
yes you are right, I did a fresh install to find out if the trouble was due to the dist upgrade from gutsy, and after trying here and there, it came up to be a problem of the old compiz settings, (the /home/user/.config/compiz) remouved that and with the script> #!/bin/bash
# start compiz
DISPLAY=:0.0 compiz --only-current-screen --replace &
disown $!
sleep 3
DISPLAY=:0.1 compiz --only-current-screen --replace &
disown $!
sleep 3
export DISPLAY=:0.1 emerald --replace & all works fine. (I just experience some bug where objects are not added to desktop :0.1, there is something in the link of lounchpad you provided, like I create a lounch icon on scree =0:1 and instead of appearing there it goes to 0:0, will see if I can fix that too) 
thanks for answering:popcorn:

---

### Post by mwiley63 on 2008-04-30
> **gupi-gupi said:**
> it used to work fine with the script  untill this new 8.04 hardy, now when I start my machine on screen 0 I get this bug where any dropdown menu just don't show up, on second screen they do worck:confused: , any suggestion?

edit: I'm getting mad, tried evry script on the thred, still without menudropdown. just to know... anyone else with this problem in hardy?

I'm having this same problem, I installed emerald with compiz manager and such, and none of these scripts are solving the slow drop down menus on monitor 0.

---

### Post by gupi-gupi on 2008-04-30
are you upgrading from feisty or fresh into hardy? in a fresh install the script from tristan worked for me > #!/bin/bash
# start compiz
DISPLAY=:0.0 compiz --only-current-screen --replace &
disown $!
sleep 3
DISPLAY=:0.1 compiz --only-current-screen --replace &
disown $!

just make sure the permissions are right in the sturtup.sh script, and that it's executable, add it to session and you should be good to go.
If you dist upgrade you might have to rename the .config/compiz to see if starting anew with compiz configuration solve the problem (it solved mine)

---

### Post by mwiley63 on 2008-04-30
I tried changing the permissions and removing the .config/compiz directory and still am having no luck.  

Right now in my script I have this:

```
#!/bin/bash
# start compiz
compiz --replace gconf &
gtk-window-decorator --replace
sleep 3
DISPLAY=:0.0 compiz --only-current-screen --replace &
disown $!
sleep 3
DISPLAY=:0.1 compiz --only-current-screen --replace &
disown $! 
```

I need to start compiz when I am logging in, should I make it a different script?  If I don't start compiz in the script then I have to manually start it myself.  I am on a fresh install of 8.04 64 bit.

---

### Post by gupi-gupi on 2008-04-30
I would try to leave the file like this:
> DISPLAY=:0.0 compiz --only-current-screen --replace &
disown $!
sleep 3
DISPLAY=:0.1 compiz --only-current-screen --replace &
disown $!
then I'd try to install emerald engine and add it to session manager, emerald --replace &
(also may be the case you have to deactivate from sistem preference appearence the compiz effect) It worked for me.

---

### Post by mwiley63 on 2008-04-30
Ok I got it to work, using the script with a sleep 5 at the start of it.  I didn't use any scripts to start up compiz or emerald in session manager.  Here is my script:
```
#!/bin/bash
# start compiz
sleep 5
DISPLAY=:0.0 compiz --only-current-screen --replace &
disown $!
sleep 3
DISPLAY=:0.1 compiz --only-current-screen --replace &
disown $! 
```

The only thing that bothers me is the screen flashes maybe 8-9 times before it is done booting (after I login).  This is probably my fault of something I changed.

I have another question though, and maybe I should open a new topic for this one.  Every time I reboot or hit ctrl + alt + backspace my second monitor gets a message saying "Input Not Supported" because the refresh rate for it is set incorrectly.  I followed the exact specs of the monitor when adding it to my xorg.conf file, but it doesn't want to listen.

Some how I think that the monitor's display settings are copied from my primary monitor, or its just not listening to what I tell it in the xorg.conf file.  Is there any way I can tell a monitor to load up a specific refresh rate in the xorg.conf file?  I have given it ranges but that is not helping.  I always end up going into nvidia-settings and setting the monitor refresh rate there.

---

### Post by asphixmx on 2008-05-16
I would like to share my solution to the menu lag issue. 
The script 

DISPLAY=:0.0 compiz --only-current-screen --replace &
DISPLAY=:0.1 compiz --only-current-screen --replace &

placed in System/Preferences/Session was working for me (have 8.04, Hardy). Eventually, it stopped working with no reason. BUT if I made a double click on the script, the menu lag was fixed again. Why, if placed in the startup, was not working, only if I started it manually?
I then changed the script (when I red this post) in the startup to:

sleep 5
DISPLAY=:0.0 compiz --only-current-screen --replace &
disown $!
sleep 3
DISPLAY=:0.1 compiz --only-current-screen --replace &
disown $!

The problem still there. Then, I changed "sleep 5" to "sleep 15", and it worked! Maybe some of you have to change the wait value to more seconds, as I do and then it will fix the problem.

---

### Post by chacham23 on 2008-05-18
Thanks ALL!
that worked to me
> 
#!/bin/bash
# start compiz
sleep 5
DISPLAY=:0.0 compiz --only-current-screen --replace &
disown $!
sleep 3
DISPLAY=:0.1 compiz --only-current-screen --replace &
disown $!


now my ubuntu is perfect!!!!!!!!!!! :)

---

### Post by UnixGeeK on 2008-05-18
The above script almost worked, but the title line is gone on my first screen. No menu delay on second screen. Using KDE & Compiz.

---

### Post by yonexFactory on 2008-06-05
> **marriouss said:**
> *notquitemichael: the script works great. Now I've compiz on both screens and the menus are slow no more!!! :guitar:

I've made the following:
1. compiz-dual.sh script that looks like:

```

#!/bin/sh
DISPLAY=:0.0 compiz --only-current-screen &
sleep 3
DISPLAY=:0.1 compiz --only-current-screen &
sleep 3
DISPLAY=:0.0 avant-window-navigator &
DISPLAY=:0.1 avant-window-navigator & 
```

2. Added compiz-dual.sh to gnome startup (System->Preferences->Sessions)

3. Appearance->Visual effects - Set to None.

!Ubuntu Hardy rc


Works perfectly. Thank you! :)

---

### Post by mike16889 on 2008-06-21
i was having the same problem but this script fixed it:

```
#!/bin/bash
# start compiz
DISPLAY=:0.0 compiz --only-current-screen --replace &
disown $!
sleep 3
DISPLAY=:0.1 compiz --only-current-screen --replace &
disown $!
```

---

