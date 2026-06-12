---
title: "Beryl:  No Emerald Themes and No Minimize/Maximize/Close Window Buttons"
date: 2007-02-24
forum: Desktop Environments
---

### Post by satchelpig on 2007-02-24
I have finally managed to get beryl installed and working -- kinda.

Now I'm just trying to figure out how to make it behave properly.

(1) There are no minimizing/maximizing/close window buttons on the top right of the windows.  The function is there, but you have to kind of guess where the button "would" be if it were rendered properly.

(2) Related to the first, I have seen others with the problem I described above advised to select a theme in the emerald theme manager, which should correct the issue.  My problem:  when I go to the emerald theme manager there are . . . well . . . NO THEMES THERE!!!  Now if I go to "Engines" there are some choices there but I don't have a pre-populated set of them.  Any ideas what happened or how to fix?

(3) Unrelated -- when I first got beryl going, there was this extremely cool feature that allowed you to click and drag the title bar in such a way that it in effect "peeled back" the window to see what was behind it and then snapped back when you let go.  Now it's not doing that anymore and so far as I know I didn't change a setting.  Any ideas what I'm talking about and how to restore that bling?

Thanks.

---

### Post by Stemp on 2007-02-25
(2) is **emerald-themes** package installed ?

---

### Post by satchelpig on 2007-02-25
Ooops.  No.  I have it now.  Thank you.  Wow I  can't believe I missed that,  OK, well, any ideas about the third item, which is hopefully a better question?

:oops:

---

### Post by Stemp on 2007-02-25
I can't answer your third question, but in fact it's working for me when my window is maximized.

---

### Post by ronmarley1 on 2007-02-25
As far as question 3, as the poster above wrote, the window needs to be maximised.  Also, at least for me, if I change any of the settings of Resize Display Mode under Behaviour under Resize Windows under Window Management, it "breaks" the peel back feature.  I need to keep the setting as Normal.

---

### Post by satchelpig on 2007-02-25
> **ronmarley1 said:**
> As far as question 3, as the poster above wrote, the window needs to be maximised.  Also, at least for me, if I change any of the settings of Resize Display Mode under Behaviour under Resize Windows under Window Management, it "breaks" the peel back feature.  I need to keep the setting as Normal.
OK, that works for me too (maximizing the window).  However, I notice that if you pull too much or too hard in any direction, the window "pops off" and becomes un-maximized, etc.  Any way to increase the resistance to "popping off"?  I have to think there's a setting somewhere.  Thanks.

---

### Post by hustle7 on 2007-03-01
> **Stemp said:**
> (2) is **emerald-themes** package installed ?

I'm having problems with my emerald theme manager in beryl. I try to select a theme but no changes would occur. My windows have no un-minimize, minimize, and close buttons when using beryl. Would you please be so kind to help me solve this dilemma? Thank You!

---

### Post by TimJBart on 2007-03-01
> **hustle7 said:**
> I'm having problems with my emerald theme manager in beryl. I try to select a theme but no changes would occur. My windows have no un-minimize, minimize, and close buttons when using beryl. Would you please be so kind to help me solve this dilemma? Thank You!


I had the exact same problems.

a) There were no maximize and minimize buttons/titlebars.
b) Clicking on a new theme in Emerald Manager did nothing.

I asked on the forums and someone posted this response and it WORKED!!!



> 
If you have a nvidia card and if you are using the non-opensource drivers, run this command.
Code:

```
sudo nvidia-xconfig --add-argb-glx-visuals
```

Then hit <CTRL><ALT><Backspace> and log back in again. That should fix your problem.

Hope this fixes your problem.  If not, there are some other suggestions in the thread: [http://ubuntuforums.org/showthread.php?t=367850](http://ubuntuforums.org/showthread.php?t=367850)

---

### Post by badave on 2007-03-15
After trying a number of other things, I found that what actually worked was changing the default depth from 16 to 24 under screen in xorg.conf (after keeping all the other changes).  Here is how my screen section under xorg.conf appears now.  To edit (for those getting a grasp of this), simply

```
sudo gedit /etc/X11/xorg.conf
```

and scroll down to screen and edit to have DefaultDepth of 24.  If that doesn't work adding the options below that may also help.  Good luck.

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Nvidia GeForce Go 6150"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
	Option "AddARGBGLXVisuals" "True"
	Option "RenderAccel" "True"
	Option "AllowGLXWithComposite" "True"
	Option "backingstore" "True"
	Option "TripleBuffer" "True" 
    SubSection     "Display"
        Depth       1
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```



The FAQ was for compiz, but worked well for beryl.  Beryl works really well now.

---

### Post by bvanaerde on 2007-03-15
> **TimJBart said:**
> I had the exact same problems.

a) There were no maximize and minimize buttons/titlebars.

Hmm, I'm having this problem too.
I thought it was just meant to be like that: it looks so clean this way :D

When I hover over the place where the buttons should be, they appear, and remain visible afterwards.
Never bothered much about it though, haven't even tried another theme.

This thread made me curious, I'll check it out when I get back home :)

edit: no, the buttons disappear again, after hovering over them.
I like it :D

---

### Post by Neo4 on 2007-03-23
Hi,

I'm having the similar problem with my emeral themes! 


I select one from the emerald theme manager and nothing happens!!! :( 


but all the rest is working fine!


Thanks

---

### Post by linnaen on 2007-06-05
For the buttons issue,  there is an option within the "visual effects" tab in beryl-manager called "windows decoration". If this is unticked, then menu bars, and buttons disappear.

---

### Post by David Oxland on 2007-06-07
Not only that; for me terminal screen is blank making editing awkward

---

### Post by sdf88 on 2007-06-24
> **badave said:**
> After trying a number of other things, I found that what actually worked was changing the default depth from 16 to 24 under screen in xorg.conf (after keeping all the other changes).  Here is how my screen section under xorg.conf appears now.  To edit (for those getting a grasp of this), simply



The FAQ was for compiz, but worked well for beryl.  Beryl works really well now.

Thankyou this worked for me

---

### Post by bbooker5 on 2007-07-21
Awesome. Thanks. This is the second time I've had this problem and couldn't find any help anywhere. It took a while to find this thread but I got it :) Last time I forgot to reply my thanks to you so THANK YOU TimJBart: sudo nvidia-xconfig --add-argb-glx-visuals fixed my problem. Many thanks.

---

### Post by a7med911 on 2007-07-22
hey bro ..

type this on terminal and i know it will work

run « sudo nvidia-xconfig --add-argb-glx-visuals[COLOR="Red"] -d 24[/COLOR] », then restart !X

dont forget run this part -[COLOR="Red"]d 24[/COLOR] with the command..

hope it will work

see ya

---

### Post by linux-farm on 2007-09-02
"I'm having the similar problem with my emeral themes!
I select one from the emerald theme manager and nothing happens!!! 

   I was having the same problems - all of my windows would be working fine, no missing minimize or close buttons, but i couldn't change my themes in the emerald theme manager.

   I figured out that beryl uses two different decoders for its themes:
                 - Standard Beryl Decoder (emerald)
                 - GTK Window decoder
   You might be stuck in GTK.  To fix this:
                 - right click on the beryl manager (the red emerald thingie in your running applications manager)
                 - scroll down to "Select Window Decoder"
                 - and choose emerald
   You don't need to refresh your x window, the change should happen automatically

Hope this solves your problem :)

---

### Post by therritt on 2007-11-03
After trying all the various fixes for this, I just installed the Heliodor Window Decorator, then restarted X (Ctrl-Alt-Backspace), then selected Heliodor for as my Window Decorator.  Everything seems to work great now and I have the title bars back under Heliodor.

Using ATI x1400 card

---

### Post by Night4lover on 2008-04-23
> **a7med911 said:**
> hey bro ..

type this on terminal and i know it will work

run « sudo nvidia-xconfig --add-argb-glx-visuals[COLOR="Red"] -d 24[/COLOR] », then restart !X

dont forget run this part -[COLOR="Red"]d 24[/COLOR] with the command..

hope it will work

see ya

:)

This worked for me. I had it all working then it died and I was trying to fix it for the last two days. It must need 24bit color to display window decorations. thx then.

---

