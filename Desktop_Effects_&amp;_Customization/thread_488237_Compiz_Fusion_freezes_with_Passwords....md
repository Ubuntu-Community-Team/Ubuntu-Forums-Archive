---
title: "Compiz Fusion freezes with Passwords..."
date: 2007-06-29
forum: Desktop Effects &amp; Customization
---

### Post by crimesaucer on 2007-06-29
Does anyone else have trouble with their password entry for root privileges such as Synaptic or gksudo?


Every time I run Synaptic, or try to open my Thunar File System in root privileges (gksudo thunar), I get the "shaded password screen" and the password dialog box for entering my password...so, as soon as I enter my password, the shaded screen freezes and the app never loads.


I always have to shut the computer off manually, and when I do it, I see the opened root app "behind" the shaded screen while my computer is shutting off.




...everything works perfectly when not using Compiz Fusion.

---

### Post by speaker219 on 2007-06-30
Hmm, I've been using Compiz Fusion for quite a while and that doesn't happen for me...

---

### Post by crimesaucer on 2007-06-30
I've had it since page one of that stickied thread above...and it has been my only real problem.

I hate that shaded screen anyway, but this has been my first time ever having problems with it...Beryl never did this, and xfwm4 doesn't do this either.

---

### Post by crimesaucer on 2007-06-30
Just to clear things up, it is a problem with the "disable-grab" in gksu...

The dimmed screen gets stuck on it every time...I could always "ctrl+alt+backspace" after the password screen freeze, and then I'll still be in root when I log back in... but I went about fixing it in a different way because it was to time consuming to always have to log back in after typing "ctrl+alt+backspace".

First I tried to see if it had something to do with my .conkyrc: 

```

# Create own window instead of using desktop (required in nautilus)
own_window no
own_window_transparent yes
#own_window_type normal
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
# I think the "use spacer" option only works with mono fonts.
use_spacer yes
use_xft yes

```

I only changed this part with no luck:

```

own_window no

```

in fact it ruined my desktop each time I tired it that way...

...so instead (temporarily), I typed:

```
alt+F2
```

and then:

```
gconf-editor
```

...then I clicked: apps-->--gksu

...and checked disable-grab


I know there are some security things about that, but I'll just do this while I wait for someone else with a similar problem to be find a fix for it.

(I use xubuntu with a conky script if that helps explain anything having to do with the grab problem)

---

### Post by imcc on 2007-07-06
Sorry to bump this if its been answered elsewhere. I ran a search and this appears to be the only thread on this subject.

I get exactly the same error. 

I don't really want to disable-grab really as it lowers security. Is there another fix that anyone can suggest, please?

I have everything else running perfectly, but would really like to fix this issue.

---

### Post by crimesaucer on 2007-07-06
I haven't found an answer for this yet. If you learn how to fix it, then please let me know.

---

### Post by miggl on 2007-07-13
I've been having this issue as well. Additionally, the second time the the "freeze" occurs, I am unable to CTRL-ALT-BACKSPACE my way out of it and have to perform a hard-reset.

Do we know if disabling the shader feature will alleviate the problem?

---

### Post by crimesaucer on 2007-07-14
Yes,

if you press alt+f2 and enter:

```
gconf-editor
```


Then in the tree menu, click: apps-->--gksu


...then on the right side, check the box to: disable-grab



This will work perfectly. The only problem is that it is supposed to be bad for security when entering your password. I have nothing to hide so I'm not worried about it for now, however I still want to fix this problem when I am able to.

---

### Post by shanepardue on 2007-08-02
I'm also having the same problem...Have you figured anything out yet?

---

### Post by miggl on 2007-08-02
> **shanepardue said:**
> I'm also having the same problem...Have you figured anything out yet?

Here's what I do, without needing to use the grab-work-around. Whenever it hangs itself (usually the first time I do any admin functionality, like open Synaptic), I wait till it has completed whatever processing it has done "behind" the scenes, then I hit ALT-F4 to close the now hidden application. The fading goes away, and I repeat the previous process (kiej opening Synaptic). Now that I have entered my password, it won't request it again, and I'm good to go.

I'm using this until they implement and actual fix in compiz.

---

### Post by thetictacaddict on 2007-08-04
I've been having the same problem.  I found that adding the -g option to disable grab worked, but I wanted to disable it globally.  Checking the box in gconf-editor has solved it for me for now.  Thanks :)

---

### Post by crimesaucer on 2007-08-04
What's strange is that I had this problem about a month ago, but after using my gconf-editor to disable-grab for that month, it seems that the problem fixed it's self with one of the updates...because I re-enabled my grab screen and it works perfectly now...in fact, the dimmed grab screen is much better then how it used to be with Beryl.

---

### Post by screaminj3sus on 2007-08-07
Same thing is still happening to me, incredibly annoying. I just installed it from trevinos repo yesterday so it's the newest update I assume.

---

### Post by LordMau on 2007-08-17
Posted this behaviour in another thread. I'm using the ATi+XGL+Compiz instructions with Amaranths repos. Did not notice this behaviour under trevino's repos. For now going with the Ctrl-Q then reopen route.

---

### Post by shanepardue on 2007-08-17
> **LordMau said:**
> Posted this behaviour in another thread. I'm using the ATi+XGL+Compiz instructions with Amaranths repos. Did not notice this behaviour under trevino's repos. For now going with the Ctrl-Q then reopen route.
I've used both Trevino's and Amaranths repositories and I still get the problem.

---

### Post by crimesaucer on 2007-08-17
Like I said earlier, I had this problem for a month when I first installed Compiz Fusion (Trevino's Repository), and so I "disabled-grab".


.....then, I checked my problem a month latter, and it had fixed it's self...and is still working good.


Now, what I think I might have done is...that I possibly turned a plug-in off, or changed a setting while I had the "grab screen" disabled for that month, and when I re-enabled the "grab screen", it had been fixed because a plug-in had been turned off...


So, maybe go through your ccsm and try turning certain plug-ins off and see if that fixes the problem. I use very few Compiz Fusion plug-ins and 2 of them that I know I turned off in that month were Application Switcher and Snapping Windows.


And who needs Application Switcher or Ring Switcher now that there is Shift Switcher in the "compiz-fusion-plugins-unofficial".

---

### Post by shanepardue on 2007-08-18
> **crimesaucer said:**
> Like I said earlier, I had this problem for a month when I first installed Compiz Fusion (Trevino's Repository), and so I "disabled-grab".


.....then, I checked my problem a month latter, and it had fixed it's self...and is still working good.


Now, what I think I might have done is...that I possibly turned a plug-in off, or changed a setting while I had the "grab screen" disabled for that month, and when I re-enabled the "grab screen", it had been fixed because a plug-in had been turned off...


So, maybe go through your ccsm and try turning certain plug-ins off and see if that fixes the problem. I use very few Compiz Fusion plug-ins and 2 of them that I know I turned off in that month were Application Switcher and Snapping Windows.


And who needs Application Switcher or Ring Switcher now that there is Shift Switcher in the "compiz-fusion-plugins-unofficial".
I did see your post before, but unfortunately I was unable to link this to a particular plugin. I 
suppose I'll disable-grab for now. It doesn't happen on my nvidia desktop, just my intel video'd 
laptop if that means anything.

---

