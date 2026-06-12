---
title: "gnome-panel always on top"
date: 2009-11-03
forum: Desktop Environments
---

### Post by zcal on 2009-11-03
Does anyone know how I might configure the gnome-panel so that open windows can cover it?  I'd like to have it free floating in the middle of the desktop without always having to look at it floating on top of my applications.

And no, I don't merely want to hide it. :P

---

### Post by sentythee on 2009-12-22
Late reply, but I couldn't find an answer for this anywhere else, so I might as well post the answer here.

Right click the panel -> Properties -> Autohide
From Compiz: Go to "Window Rules" and add "class=Gnome-panel" under "Below"

See attachment, the top panel is covered by the browser, and it's never hidden.

Edit:
That didn't work the second time I did it. This did work, however:
Uncheck Autohide
Add the Window Rule
Recheck Autohide

If you don't want to do this for *every* panel, "Grab" the Window Title of the panel using the tool in compiz. Use that rather than "class=Gnome-panel". It'll look something like "title=Top Expanded Edge Panel".

---

### Post by umanzor on 2010-02-27
> **sentythee said:**
> Late reply, but I couldn't find an answer for this anywhere else, so I might as well post the answer here.

Right click the panel -> Properties -> Autohide
From Compiz: Go to "Window Rules" and add "class=Gnome-panel" under "Below"

See attachment, the top panel is covered by the browser, and it's never hidden.

Edit:
That didn't work the second time I did it. This did work, however:
Uncheck Autohide
Add the Window Rule
Recheck Autohide

If you don't want to do this for *every* panel, "Grab" the Window Title of the panel using the tool in compiz. Use that rather than "class=Gnome-panel". It'll look something like "title=Top Expanded Edge Panel".

hey that works perfectly fine, thanks a lot!!!!!!!

---

### Post by ghandon.2110 on 2010-08-27
Thanks  for your response
 I have Ubuntu 4.10.
 In this way my system works great  but the top panel to bottom panel does not work if there is another way  to solve
Help please and thank you for your attention

---

### Post by mlord on 2010-09-19
re: compiz-settings "Window Rules"

> **umanzor said:**
> hey that works perfectly fine, thanks a lot!!!!!!!
Well, it works -- and thanks for that!

But it needs a bit of extra sauce.  Add this rule as well:

***Above*   title=Panel Properties**

That fixes the "Properties" pop-up for the panel.

But I also have another panel, normally hidden, and now when it unhides it is still covered by everything else.. I need that one to stay on top.  How ?

I suppose the answer is probably in the "grab the Window Title" suggestion above.. but I haven't a clue how to do that ???

**EDIT:** Oh, found it.

Click on the PLUS SIGN to the right of the "Match-->Below" line.

An "Edit Match" pop-up should appear.  Change the "Type" field to "Window Title", click on "Grab", and then (finally) click on the panel who's title you want to discover.  The "title" will appear in the "Value" field of the "Edit Match" pop-up.

In my case, with the panel at the top of the screen, the "Window Title" for it was discovered to be "Top Expanded Edge Panel".  So I now use this rule to force it below other windows:

***Below*  title=Top Expanded Edge Panel**

And my other auto-hide panels still stay on top when un-hidden.  Woot!

Cheers

---

### Post by mlord on 2010-09-19
Oh bother.. all of the above stuff works.. until I log out and log in again.  At which point, gnome-panel is invisible.. buried under the desktop, I suspect.

So.. I've abandoned that entire approach, and just written a little script that uses the fantasic "**wmctrl**" app instead.

So.. first, install **wmctrl** from synaptic, and then put this script somewhere useful, and add it to your GNOME "Startup Applications".  Works like a charm, for me at least.  :)
```
#!/bin/bash
##
## Script to fix the top gnome-panel, so that it can be covered by other apps.
## Stick this into GNOME System->Preferences->Startup_Applications.
##
## Written by Mark Lord <mlord@pobox.com>, free for all redistribution/uses.
##
(
        ## If we change the property too soon,
        ## gnome-panel will start up buried under the desktop.
        ## Not sure how to know "how soon is too soon" (~6 seconds here),
        ## so we will wait for a good known app to start up first.
        ##
        WAITFOR="gnome-screensaver"
        ##
        for i in {0..40} ; do   ## 20sec max wait time
                killall -0 $WAITFOR && break
                sleep 0.5
        done
        ## logger -- "$0: waited $((i / 2)).$(((i % 2) * 5)) secs"
        wmctrl -r "Top Expanded Edge Panel" -b remove,above -b add,below
        exit 0
) &>/dev/null &
exit 0
```

---

### Post by mlord on 2010-11-05
I should add that this works much better when "Constrain Y" is unchecked, in CompizConfig Settings Manager, under the "Move Window" plugin settings.

-ml

---

### Post by reed1 on 2010-12-05
@**mlord**

I tried to add the rule from compiz but then the "always on top" function of other windows break. But when I tried wmctrl, all worked perfectly . Thanks ! :P

---

### Post by Axzercion on 2010-12-21
Didn't always work for me... My guess is that it tried to do the wmctrl command too soon. I modified the script a lot to fix it. Perhaps it's possible in mlords script aswell by adding another sleep 5 before the wmctrl command... I'm not very good - at all - at bash scripting but I've modified it to:
#!/bin/bash
process_found=false
while [ $process_found == false ] ;
do
sleep 1
pid=`ps -eo pid,args | grep 'gnome-screensaver' | grep -v grep | cut -c1-6`
if [ "$pid" != "" ] ; then
process_found=true
fi
done
sleep 5
wmctrl -r "Top Expanded Edge Panel" -b remove,above -b add,below
exit 0

It uses the process id of gnome-screensaver. I found the command while googling, but I don't know where anymore. Added a lot of extra commands I think, but I didn't know how the pkill command works and if it returns a value or not...
By adding the sleeps in there I suppose it's roughly 5 seconds max before the wmctrl kicks in after login. Ample time before you can put any screens over it...
I'm also not sure if the ps -e was such a good idea, but I suppose if it doesn't work you can always modify it to ps -u <username> -o pid,args as it only lists the processes of your user. The script now works on all of my systems.

Anyway thanks a lot Mark, this issue was really starting to irritate me about gnome

---

### Post by clockworktri on 2010-12-23
mlord,
I've added the script to my startup, and unchecked "constrain y" in compiz, but instead of having the panel appear below the windows, the windows just slide under the panel when I move them. Do you know why this might be happening or how I could fix it please? I would love to get this to work.

---

### Post by clockworktri on 2010-12-23
I've tried this script too, and the same thing happens. it shows up and windows will slide under it, but that's all. is the script just not working?

---

### Post by clockworktri on 2010-12-23
> **clockworktri said:**
> mlord,
I've added the script to my startup, and unchecked "constrain y" in compiz, but instead of having the panel appear below the windows, the windows just slide under the panel when I move them. Do you know why this might be happening or how I could fix it please? I would love to get this to work.

BTW, I added the script simply by saving the .sh in a folder then going to Startup Apps and browsing and selecting it. Is that how to do it? I've never added a script to the startup before.

---

