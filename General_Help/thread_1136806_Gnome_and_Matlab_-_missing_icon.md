---
title: "Gnome and Matlab - missing icon"
date: 2009-04-25
forum: General Help
---

### Post by cfogelberg on 2009-04-25
Dear all,

I've noticed that Matlab's window list entry often does not appear in Gnome's Window List applet. For example, see attached screenshot. At other times it does appear, although I can't identify any pattern (editor open/closed, variable editor open/closed) which will make it either appear or disappear.

[[IMG]http://img26.imageshack.us/img26/1198/whereismatlab.th.png[/IMG]](http://img26.imageshack.us/my.php?image=whereismatlab.png)

I am running Jaunty, Window List 2.26.0 and Matlab R2008b. This isn't a serious problem but it is bizarre and any wisdom on insight would be much appreciated!! :)

Christo

---

### Post by gazer22 on 2009-04-28
I'm getting the same thing.  If I minimize matlab, it shows up in the winow list again.  (Save versions of window list and matlab).

I'm using metacity w/ some desktop effects.  If you disable desktop effects (System->Preferences->Appearance then the Visual Effects tab), the matlab window stops disappearing, though you do lose your cool effects.

This also occured with prior versions of ubuntu.

Rather annoying.

---

### Post by cfogelberg on 2009-04-28
> **gazer22 said:**
> I'm getting the same thing.  If I minimize matlab, it shows up in the winow list again.  (Save versions of window list and matlab).

I'm using metacity w/ some desktop effects.  If you disable desktop effects (System->Preferences->Appearance then the Visual Effects tab), the matlab window stops disappearing, though you do lose your cool effects.

This also occured with prior versions of ubuntu.

Rather annoying.

Thanks for the suggestion - I just tried minimising it and it reappeared exactly as you suggested. For the record I have my visual effects set on "Normal" - the top setting looks cool, and I try it from time to time but I don't normally use it.

What is annoying (and it affects both Normal and Extra is how it can stick some windows to the edge of the screen for so much mouse travel. If anyone has any suggestions on how to change that I'd love to hear them! :)

Christo

---

### Post by Skeletonix on 2009-04-28
same here :(

---

### Post by Nepherte on 2009-04-28
How about disabling the visual effects completely? Matlab and visual effects never work well together. I bet the visual effects are kinda distracting you from your work in matlab in the first place.

---

### Post by gazer22 on 2009-04-28
> **Nepherte said:**
> How about disabling the visual effects completely? Matlab and visual effects never work well together. I bet the visual effects are kinda distracting you from your work in matlab in the first place.

Yes, that works.  However, I NEED to be distracted from matlab...

---

### Post by pritamps on 2009-10-19
I have this problem too. However, I use KDE (4.3.2) sometimes and even with desktop effects enabled, MATLAB shows up in all its glory all the time!

---

### Post by kesken88 on 2009-10-19
I use Matlab via terminal (./matlab -nodesktop)  and am very happy at the speed increase over the full desktop(on my nettop).

Just a thought to those who care.

---

### Post by Punkphysicist on 2010-11-03
Has anyone found a permanent solution?  I have this problem also and am using Matlab R2010a with Ubuntu 10.10.

---

### Post by deezer on 2011-01-13
Novell GroupWise also has this same issue - and disabling desktop effects seems to have corrected it.  However, this is not a desirable solution.  Does anyone else have an idea about this?

Is MatLab also a Java-based application?  Trying to think of similarities between GroupWise and MatLab that might help us figure out a solution...

---

### Post by deezer on 2011-01-13
One thing that I noticed when messing around with this is that all the windows would again appear whenever I switched between different Appearance settings - from Normal to None to Extra - no matter what selection I chose it would cause all of the windows missing from the GNOME window list to immediately appear.

---

### Post by wiltk on 2011-02-24
This problem has been bugging me for a while with Matlab.  I finally decided to write a script to iconify then focus all my open Matlab windows when I see they are missing from the window list.  Basically I added a custom launcher for this script to my panel and click it when I need to.  This is a pretty crude solution but it's an improvement for me since I lose my matlab windows constantly.  I would like to make it automatically figure out that matlab windows are missing from the list but I have no clue how to get the current window list from the window list applet (not anywhere near a proficient programmer).

For my uses, I typically only have the main matlab window open with an editor and figures; hence, this script only looks for those windows to fix.

```
#!/bin/bash -x
# This script requires the program XWIT, available from Ubuntu repo's


# Find the Matlab main window's ID
winID=`xwininfo -display :0 -root -children|grep "MATLAB "|awk '{print $1}'`
if [[ $winID ]]
then
	xwit -iconify -id $winID
	xwit -focus -id $winID
fi


# Find the Matlab editor window's ID
winID=`xwininfo -display :0 -root -children|grep "Editor"|awk '{print $1}'`
if [[ $winID ]]
then
	xwit -iconify -id $winID
	xwit -focus -id $winID
fi


# Find all Matlab figures
winID=`xwininfo -display :0 -root -children|grep "Figure $i"|awk '{print $1}'`
i=1
while [[ $winID ]]
do
	xwit -iconify -id $winID
	xwit -focus -id $winID
	i=$(($i+1))
	winID=`xwininfo -display :0 -root -children|grep "Figure $i"|awk '{print $1}'`
done
```

---

### Post by monguin61 on 2011-05-02
I have the same problem, looking for a solution and just had a few comments.

deezer: Yes, the MATLAB desktop is based on Java.

wiltk: Having to use a workaround is annoying, but yours is the closest to a solution I've found. Did you know about the -names option for xwit though? I was messing around with your code and reduced it to this:

```

xwit -iconify -names MATLAB Editor Figure
xwit -focus -names MATLAB Editor Figure

```

The nice thing is, you can call this using the unix() or system() function directly from the matlab command line (or create a script called fixwindows.m or something).

---

