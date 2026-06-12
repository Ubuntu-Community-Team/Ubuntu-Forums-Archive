---
title: "Windows open slightly off-screen"
date: 2007-12-27
forum: Desktop Effects &amp; Customization
---

### Post by A-dogg on 2007-12-27
Whenever I open certain programs (usually a pdf file, but some others), the window opens maximized... sort of. It's always shifted slightly to the right so half of the "close window" X and the vertical scroll bar are cut off. I can correct it by right-clicking the title bar and choosing maximize, but I'd really like to have this happen automatically. This is my ONLY issue with Ubuntu Gutsy, running on a Sony Vaio VGN-FS742/w.

 I only have one desktop, so that's not the issue. And I've messed around with the compiz advanced desktop settings (put, place and move windows), but can't seem to fix the issue.

Obviously it's not a deal-breaker, but it's a little annoying.

Anyone have any advice?

---

### Post by kryth on 2007-12-27
I get the same thing only my windows open slighting off the screen to the top.  I still have no clue.

---

### Post by facted on 2008-01-10
I'm also seeing this issue with Firefox, and some other programs including just the plain folder view. Anyone know what's going on and how to fix it?

---

### Post by A-dogg on 2008-01-10
I think it's just one of those things that we get because we were bad as kids.

---

### Post by tom957 on 2008-01-11
It happens to me too. Amarok, Nautilus are the notable culprits.... pretty annoying.

---

### Post by steeleyuk on 2008-01-11
Is everybody running Compiz when this happens? Or just Metacity?

Only happens to me when I run Compiz...

---

### Post by ader10 on 2008-01-11
Also happens to me. What I do is alt-drag the window in to view. Also, when I open the gimp (which has multiple windows) they open on top of each other and on the more cluttered screen.

Another problem: On themes with borders, when I un-maximize them, the edge runs off the screen into another side of a cube or another side of the desktop wall. Sometimes the unmaximized state is saved but it's annoying to have to resize the window when it's not.

---

### Post by Therion on 2008-01-11
I can pretty much confirm it's a Compiz' thing: Compiz' running, problem persists.  Turn off Compiz' and the problem goes away.  I've been right-clicking on the application-button in the tray and maximizing from there to get the min/max/close buttons back.

I've also looked high and low but I've not been able to find a solution.

---

### Post by immolat3 on 2008-01-11
I forget the setting, but in the Advanced Desktop Effects control panel area there is something along the lines of "Center New Windows" or something. Basically it will do its best to always center new windows, i use to have that same problem until i did that. Sorry I am at work at the moment and using the DEVIL (aka Win VISTA< lolz) so I cant check for sure.

---

### Post by Therion on 2008-01-11
> **immolat3 said:**
> I forget the setting, but in the Advanced Desktop Effects control panel area there is something along the lines of "Center New Windows" or something. Basically it will do its best to always center new windows, i use to have that same problem until i did that. Sorry I am at work at the moment and using the DEVIL (aka Win VISTA< lolz) so I cant check for sure.
Your post lead me to search Google (yet again!) for a solution.  After some additional poking around I found the following suggestion/post:
> 
I find myself having to use the Place Windows plugin also. If I don't, windows open with the title bar under the top panel as mentioned above. However, with it enabled, I get very strange results in some places. For example: vncviewer. When I hit the F8 button, it is supposed to pop up a menu under the cursor (with Compiz Fusion off), but with the Place Windows plugin enabled, it throws it off into a corner and I have to drag my mouse all the way over to where it's thrown. 

Excerpted from [HERE]("http://ubuntuforums.org/archive/index.php/t-526042.html").

I too am at work so I can't put this to the test, but it sounds like the Place Windows plugin (or one of its setting's in CCSM) could be the cause of, or the solution to, this annoying little problem.  I'll check this when I get home and see what I can figure out.  It's something to try at least.

---

### Post by A-dogg on 2008-01-11
interesting. I definitely use compiz. I guess in theory I could turn it off and have windows always onscreen, but that seems like cutting off your arms to cure a head-cold (okay, maybe that's an exaggeration). 

I'm 90% sure I checked that "center new windows" box in compiz. There's three controls -- Put Windows, Place Windows and something else I can't remember. It's in one of them. From what I remember, it felt like it worked for a day or two and then the problem reappeared.

I have never had the issue of a window's title bar opening under the top panel, though.

---

### Post by Therion on 2008-01-11
I started CCSM, enabled the Place Windows plugin and then, under the General tab, found a drop down menu for Placement Mode, which I changed to "Centered".  

I don't know if my problem was exactly the same as what the original poster was posting about, but my problem was that application windows were opening (so) maximized that the title bar was "off screen" - preventing me from using the min/max/close buttons in upper right corner, or grabbing the window itself to move it.  

At any rate, configuring the Place Windows plugin as I described above solved my problem.  I'll see if it's persistent, but so far so good!

---

### Post by atorch on 2008-04-12
I've tried Cascade, Smart and Centered under Compiz Config > Put Window > General > Placement Mode, and I'm still getting this problem.  It's nothing terrible, but I do find it very annoying...  I've started compulsively hitting alt-F10 when I open windows.

I think Maximized (again, under ... > Placement Mode) fixes the problem, but I don't like all my windows opening fully maximized.  Just the file browser, firefox, thunderbird et cetera.

---

### Post by atorch on 2008-04-13
Where should I go to ask the Compiz people to fix this?

---

### Post by kgk on 2008-04-15
COMPIZ SOLUTION

I had this problem for a bit.  I'm using Compiz though, so this is only a solution for those using it.

My windows would open to the upper right of the screen with the title bar off screen on the upper edge so I couldn't hit the minimize, maximize or close buttons.  Very irritating.  I suspect it was because when I was trying to disabled the "snapping" effect of wobbly windows that is enabled by default (which should have the designer shot for) I accidentally disabled the Place Windows.

I found the solution was to go to [U]System->Preferences->Advanced Desktop Effects Settings
[/U]
Scroll down do the _Window Management_ area and [U]check the box labeled Place Windows.
[/U]
Then when you open a new window it should open at the bottom left of your screen, but with everything on screen, aligned with the edges perfectly.  If you want to change where it places the new windows click the Place Windows to see the settings (making sure not to uncheck the box) and then under General you'll see Placement Mode.

You can choose _Cascade, Centered, Smart, Maximize or Random._

This worked for me.  Personally I like Cenetered, but it's nice to have choices :-)

Hope this helps.


I think it has something to do with video drivers and/or resolutions.  I'm running 1920x1200, which is only possible with proper drivers, and I'm running SLI, so I figure it just has trouble realizing where the "edges" are.  Enabling the Place Windows seems to correct the issue.

---

### Post by atorch on 2008-04-16
See attached image:  my windows are cropped horizontally, not vertically.  They're very slightly off-screen, so that the close-window-X is beginning to be hidden.

I already have Place Windows enabled, in Compiz.  

Strange bit:  the cropping *doesn't always* happen; rather, it seems (to me) random.  The file browser is the worst (ie most frequent) culprit, though.

---

