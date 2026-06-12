---
title: "Wine breaks all window decorations"
date: 2012-05-01
forum: Desktop Environments
---

### Post by Paddy Landau on 2012-05-01
I have been using Quicken since I purchased it several years ago.

With 8.04, it worked perfectly (using Wine via PlayOnLinux).

With 10.04 and 11.04, parts of the screen were drawn in the wrong place.

Now, with 12.04, it breaks the window decoration. When I start Quicken  (I use PlayOnLinux), all window decorations from all windows -- not just  the Wine ones -- disappear. The only thing I can do is Ctrl-F4  repeatedly to close all windows, and log out and in again.

Do you know what I can do to get Wine programs to work correctly with the graphics again, as they did in 8.04?

---

### Post by *^kyfds( on 2012-05-01
> **Paddy Landau said:**
> I have been using Quicken since I purchased it several years ago.

With 8.04, it worked perfectly (using Wine via PlayOnLinux).

With 10.04 and 11.04, parts of the screen were drawn in the wrong place.

Now, with 12.04, it breaks the window decoration. When I start Quicken  (I use PlayOnLinux), all window decorations from all windows -- not just  the Wine ones -- disappear. The only thing I can do is Ctrl-F4  repeatedly to close all windows, and log out and in again.

Do you know what I can do to get Wine programs to work correctly with the graphics again, as they did in 8.04?

could you fill us in on what quicken is?

google results only show it as a banking and finance planning software

(nice to meet someone in the UK too.)

---

### Post by Paddy Landau on 2012-05-01
Quicken is a banking and finance planning software :)

Moneydance is almost a good-enough replacement, but it lacks the planning bit sadly.

> **Thehumorouscheese said:**
> (nice to meet someone in the UK too.)
Plenty of us here!

---

### Post by mc4man on 2012-05-01
I've seen this in 12.04 on _some_ progs in wine.
So for instance ImgBurn breaks WD but EAC doesn't

Get the feeling it's gtk+3 related

---

### Post by Paddy Landau on 2012-05-02
> **mc4man said:**
> I've seen this in 12.04 on _some_ progs in wine.
Ah, I see that you are indeed right. Another of my programs works fine.

> **mc4man said:**
> Get the feeling it's gtk+3 related
You may be right. I ran Quicken using Ubuntu 2D, and it worked.

---

### Post by Paddy Landau on 2012-05-02
> **Paddy Landau said:**
> You may be right. I ran Quicken using Ubuntu 2D, and it worked.
Correction. I've just run it again in 2D, and although it worked, it hid the launcher, panel, and all other new windows (which made  rebooting a bit of guess-work).

---

### Post by mc4man on 2012-05-02
Actually here it seems to be possibly compiz, at least as far as ImgBurn.
Works fine in unity-2d, gnome-shell & Classic (no effects
Breaks Wd in unity & Classic with effects. Whats odd is it usually works once ok per session, then breaks Wd after that.

Have tried downgrading wine to an actual 1.3 version (natty build), same thing.
Something is definitely amiss in 12.04, see this in xsession-errors though haven't pursed any further

> The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 36799 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by Paddy Landau on 2012-05-02
I have raised a bug for this.

Please [pop along and vote for it]("https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/993265") (the green wording near the top of the page).

---

### Post by Dngrsone on 2012-05-02
In Unity, hit Alt+F2 and type in ```
unity --replace
``` and that will get things going again without having to close windows and log out.

I have the same type of problem running a schematic program in wine-- ExpressSCH.

---

### Post by Paddy Landau on 2012-05-02
> **Dngrsone said:**
> In Unity, hit Alt+F2 and type in ```
unity --replace
```
Unfortunately, that loses any customisations I have made.

---

### Post by Dngrsone on 2012-05-02
> **Paddy Landau said:**
> Unfortunately, that loses any customisations I have made.

It does?  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/eh.gif[/IMG]

---

### Post by Paddy Landau on 2012-05-02
> **Dngrsone said:**
> It does?  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/eh.gif[/IMG]
Yes. If you customise Compiz (usually with CompizConfig Settings Manager -- CCSM), then unity --reset sets it back to the defaults. That is useful if you have broken your system by changing Compiz settings, but not useful if something else broke it and Compiz merely needs to restart.

---

### Post by Dngrsone on 2012-05-02
Huh.  The only customizations I have done in CCSM are spinning cube, and that still works fine.

---

### Post by Paddy Landau on 2012-05-02
> **Dngrsone said:**
> Huh.  The only customizations I have done in CCSM are spinning cube, and that still works fine.
Interesting. I'll have to experiment with that.

---

### Post by *^kyfds( on 2012-05-03
> **Paddy Landau said:**
> Quicken is a banking and finance planning software :)


i thought were talking about some sort of 3D modelling software....

and actual window rendering problems....

:lolflag:

---

### Post by dodo3773 on 2012-05-03
Running wine applications on a compositing window manager has always been problematic for me. Just run a different window manager (something light and plain like openbox or fluxbox)on a seperate tty and then switch to it to do your wine stuff.

---

### Post by Paddy Landau on 2012-05-03
Today, an interesting thing happened. I had not used Wine at all since I started the machine, and it happened again!

So, it is obviously not Wine that causes it, but rather that Wine happens to trigger it reliably.

I have added that note to the bug report.

---

### Post by Desert Sailor on 2012-06-03
For what it's worth, my Ubuntu / Quicken relationship has always been slightly problematic.  Usually have to update Wine or fiddle around each new Ubuntu version.  I am having the same problem with 12.04 and Quicken that you are experiencing.  Each session my first run of Quicken works fine, but any subsequent starts come up with out the top line tool bar, and it also breaks the tool bar on any subsequent programs.  Updated to the latest Wine, but that didn't fix the problem this time. 

GNU-Cash, MyMoney, Skrooge, just wasn't as smooth and elegant as what I was used to in Quicken.  

Today, I finally broke down and have given MoneyDance a try.  Looks promising and I may be making the switch.  It's a shame Intuit never caught the Linux vision and ported Quicken over.  
Kiss another customer goodbye.

---

### Post by Paddy Landau on 2012-06-04
> **Desert Sailor said:**
> Today, I finally broke down and have given MoneyDance a try.
I tested MoneyDance thoroughly. It would be good (not great), but for one glaring problem: it does not have a financial planner (an equivalent to Quicken's Financial Calendar). For me, that is a deal-breaker — how can you have a financial planner without the ability to plan and run what-ifs? There is a plug-in for it, but the plug-in is buggy and too restrictive.

---

### Post by FrankyG on 2012-06-10
To get the window decorations back issue
```
gtk-window-decorator --replace
```
using Alt-F2 or in a terminal do
```
gtk-window-decorator --replace &
```

In my case the command
```
unity --replace
```
didn't work so well for me and caused some of the windows to stall and stop responding.

---

### Post by Paddy Landau on 2012-06-10
> **FrankyG said:**
> To get the window decorations back issue...
FrankyG, that's a much faster solution than the other one. Thank you.

---

