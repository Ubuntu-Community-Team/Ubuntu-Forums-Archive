---
title: "opening konqueror always leads to &quot;malformed URL&quot;"
date: 2009-07-07
forum: Desktop Environments
---

### Post by bottleman on 2009-07-07
Hi, I'm using Kubuntu 9.04 and KDE 4.2.2.  

I would like to use Konqueror instead of Dolphin as the default file manager.  Accordingly I adjusted the "inode" preference for opening folders to prioritize Konqueror over Dolphin.  Also I made a KDE menu entry for Konqueror as a file manager, using command:

```
kfmclient openProfile filemanagement
``` 

(in which "filemanagement" was a profile that already existed in Konqueror).

Now when I open Konqueror, using that menu command, or just using the plain konsole command "konqueror", I always get an immediate "malformed URL" error.  In fact I get that error twice, suggesting that there are 2 malformed urls on startup.

Similarly, when I have used Konqueror to browse or preview an individual file, then use the "back" arrow button to return to my Konqueror home view, I get that samed "malformed URL" message, but only once.

I've tried setting my "home page" to the paths for various local folders or external web sites, but the behavior is always the same.

Other threads mentioning malformed URLs have mentioned deleting part or all of a folder named .dcop, but I don't seem to have that folder on my system.

Anyone have any idea what's going on?

Thanks!!

---

### Post by 4ebees on 2009-10-19
> **bottleman said:**
> 
Other threads mentioning malformed URLs have mentioned deleting part or all of a folder named .dcop, but I don't seem to have that folder on my system.

Anyone have any idea what's going on?

Thanks!!


Hi there,

I realise your post was a while ago. However, if you're still struggling with this, you're not alone!

In relation to .dcop, the file can be found in your /home/<user/name> directory. It is a hidden file (hence the '.' at the beginning of the file name).

To view this, in the toolbar you can select 'view' and then 'show hidden files'

(see the attached image)

I'd suggest finding the file, renaming it something like .dcop.orig (so it's still there but the system doesn't recognise it as the original file.

Then restart your machine. If this IS the fix, you're okay and go ahead and delete that file. If not, and something crashes, you can always change it's name back to .dcop and you're no worse off.

This is far better than just deleting the file - because if this DOES cause a problem deleting it removes the file and, well, your up the proverbial in a barbed-wire canoe!

See how you go.

---

### Post by bottleman on 2009-10-19
Hey 4ebees, thanks for the input.  For better or worse I already knew about hidden files and folders, and .dcop isn't there.

I'm still getting the malformed URL message from Konqueror, but I was able to tweak Dolphin to more or less work the way I wanted, so it's not terribly distracting right now.  It would be nice though if there are any other approaches I could take.  Or perhaps this is an actual bug?

Cheers! bottleman

---

### Post by 4ebees on 2010-01-07
> **bottleman said:**
> Hey 4ebees, thanks for the input.  For better or worse I already knew about hidden files and folders, and .dcop isn't there.

I'm still getting the malformed URL message from Konqueror, but I was able to tweak Dolphin to more or less work the way I wanted, so it's not terribly distracting right now.  It would be nice though if there are any other approaches I could take.  Or perhaps this is an actual bug?

Cheers! bottleman

Well, well, well. I installed Karmic 9.10. It ran well for a month or so and today..."Malformed URL"

Bugger. Damn, ham and spam.

Previously reported bug is here: [https://bugs.kde.org/show_bug.cgi?id=205888](https://bugs.kde.org/show_bug.cgi?id=205888)

---

### Post by rdznl on 2010-03-02
> **bottleman said:**
>   
"... I always get an immediate "malformed URL" error." 


Hi bottleman,
I've had the same error message popping up when browsing with Konqueror under KDE4 (after clicking 'OK' the URL loades).
I managed to track the issue down to the file:
/home/.kde/share/apps/konqueror/view_properties/global/.directory
where I then changed the line :
ViewMode=2
to:
ViewMode=1
and then no such error message pops up anymore.
I don't pretend to know what this setting actually controls, guess it's something to do with the default viewing mode.
Maybe a similar setting is relevant in your case.
Hope this helps!

---

### Post by 4ebees on 2010-03-02
> **rdznl said:**
> Hi bottleman,
I've had the same error message popping up when browsing with Konqueror under KDE4 (after clicking 'OK' the URL loades).
I managed to track the issue down to the file:
/home/.kde/share/apps/konqueror/view_properties/global/.directory
where I then changed the line :
ViewMode=2
to:
ViewMode=1
and then no such error message pops up anymore.
I don't pretend to know what this setting actually controls, guess it's something to do with the default viewing mode.
Maybe a similar setting is relevant in your case.
Hope this helps!


Matey!

Will have to try that and get back to you.

Many thanks for your work!!!!

:)

---

### Post by bottleman on 2010-03-02
> **rdznl said:**
> 
I managed to track the issue down to the file:
/home/.kde/share/apps/konqueror/view_properties/global/.directory
where I then changed the line :
ViewMode=2
to:
ViewMode=1
and then no such error message pops up anymore.


That fixed it! In my copy of that file, that setting was under a section called [Dolphin].  But changing it doesn't seem to have changed Dolphin in any way.  Go figure. 

I've never delved into it, but it seems that Konqueror and Dolphin are somehow related.  For example, if you change the Konqueror setting that allows you to have a Delete context menu item that bypasses the Trash Bin, that option appears in Dolphin as well.  

Perhaps this malformed URL thing came out of some unintended or unremembered tie between Dolphin and Konqueror. ??

Anyway, thanks much!

---

### Post by 4ebees on 2010-03-06
> **rdznl said:**
> Hi bottleman,
I've had the same error message popping up when browsing with Konqueror under KDE4 (after clicking 'OK' the URL loades).
I managed to track the issue down to the file:
/home/.kde/share/apps/konqueror/view_properties/global/.directory
where I then changed the line :
ViewMode=2
to:
ViewMode=1
and then no such error message pops up anymore.
I don't pretend to know what this setting actually controls, guess it's something to do with the default viewing mode.
Maybe a similar setting is relevant in your case.
Hope this helps!



Well, I can confirm that this fix is just that - a fix!!!

Works perfectly. I am so very appreciative of the fact you've worked it out.

Many, many thanks.

---

### Post by datenhalde on 2010-10-26
Since this problem keeps reappearing every few days (no idea what causes the change from Viewmode 1 to 2, neither what the view mode's actually supposed to do), I put a small script in cron.hourly: 

```

#!/bin/bash
TARGET="/home/[username]/.kde/share/apps/konqueror/view_properties/global/.directory"
sed -i".bkp" s/"ViewMode=2"/"ViewMode=1"/  $TARGET 

```Maybe this bug will be fixed one fine day, until then, this should keep the annoyance to a minimum.

---

