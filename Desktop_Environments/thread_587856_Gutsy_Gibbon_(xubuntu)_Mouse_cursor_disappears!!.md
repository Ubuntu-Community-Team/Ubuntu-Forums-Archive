---
title: "Gutsy Gibbon (xubuntu): Mouse cursor disappears!!"
date: 2007-10-23
forum: Desktop Environments
---

### Post by aspora.isernia on 2007-10-23
Hi!!
I recently installed the new Xubuntu 7.10 and it is SUPERB: much faster and really cool!!
But I have a really strange flaw: sometimes (and I don't know why) the mouse cursor suddenly disappears!! :confused: I can still click on everything but it becomes "invisible". I tried to logout and login again or to restart X but my cursor comes back only after reboot :(
I looked on the forum for any suggestion, but I didn't find anything...
Could someone help me??

I have a Dell Latitude X200 and installed the released version of Gutsy Gibbon (not r.c.).
Many thanks

a.i :)

---

### Post by doublemeat on 2007-10-24
I have the same problem.  After nearly an hour of searching, I've found no definite solutions (only guesses).  I don't want to jump to conclusions and shout "bug"!

Mine's a bit different though: my mouse cursor comes back.  It only disappears over certain controls when the system is busy.  This is most noticeable in Firefox: while fetching a page, the cursor will disappear when moved over the tab and/or toolbar area--sometimes even the whole page. Moving the cursor off those areas "restores" it.  And once things settle down, the cursor is visible everywhere once again.

MacBook (non-pro gen 2), 2gb RAM, 7.04 > 7.10, Compiz-Fusion + Emerald (problem exists with just Metacity too, if I recall correctly).

Logoff/logon, restart X, and/or reboot does not solve the issue.

---

### Post by aspora.isernia on 2007-10-24
Actually, it seems that the problem is slightly similar...
Mmm: I forgot to mention that my Xubuntu does not use Compiz, neither Xgl: the most basic settings...
Any help?
Thanks

a.i :)

---

### Post by lomeo on 2007-10-24
doublemeat, try to set INDIRECT to yes in /usr/bin/compiz

---

### Post by fluffynuts on 2007-10-25
I had this problem the other day. If I remember correctly, I rebuilt my icon cache, and that sorted it out. Although I can't remember *exactly* what I did, I think it was along the lines of

```
update-icon-caches /usr/share/icons
```

Hope this helps.

---

### Post by metalpres on 2007-10-27
I am also having the same problem,  the cursor will disappear when certain things are ogint then reappear a few seconds later,  like loading a webpage it disappears then comes back when the page is loaded,  also installing software it will do the same and come back when its done.  In Amarok loading tracks does it, and also clicking the stop button will cause it for a few seconds...  so yea it happens a lot.  Im running 7.10 with Compiz, other then this cursor issue the OS is rock solid and fast as hell!

---

### Post by Stunts on 2007-10-27
I'm having a silhtly different problem here...
I'm running Gutsy with Compiz and emerald themes. I chenged my cursor theme, but it keeps changing back to the default cursor when it's over the desktop or menus bars. When it is on top of an application, it goes back to the cursor I had selected... It's somewhat anoying... I've tried the sugestions on the thread, but noe worked... any more sugestions?
Thanks!

---

### Post by aspora.isernia on 2007-10-27
> **fluffynuts said:**
> I had this problem the other day. If I remember correctly, I rebuilt my icon cache, and that sorted it out. Although I can't remember *exactly* what I did, I think it was along the lines of

```
update-icon-caches /usr/share/icons
```

Hope this helps.

Did you execute the command while the cursor was invisible?

---

### Post by Stunts on 2007-10-27
Hey all, I seem to have solved my problem, tough it's somewhat different from yours.
The cursor seemd to be changing only while hoovering on stuff controled by emerald, so I used synaptic manager to uninstall "Emerald Themes". This made the cursor look good right away.
After a Restart I reinstalled emerald themes again with synaptic and now everything is fine. Hope the same works for you...

---

### Post by doublemeat on 2007-10-27
> **lomeo said:**
> doublemeat, try to set INDIRECT to yes in /usr/bin/compiz

As an update, I tried the suggestion above.  But it prevented Compiz-Fusion from loading at all--so all I would get would be metacity.  If I tried to execute "compiz --replace" from a gnome-terminal, it would complain about something like xgl not being found.  (I researched that--apparently the intel 915 onboard graphics doesn't need xgl for compiz.)

Anywhoo, I gave up, then remembered I had changed this setting (at top).  I changed it back, rebooted, and voila--compiz was back in business.  Not only that, but the cursor disappearing problem was somehow magically gone!  (No idea how--I think the "Wiggle Method" [just mess with stuff randomly until it works even if you didn't actually change anything] worked for me again.)

And not only that, but as a second bonus side effect: since upgrading to Gutsy, I had the problem where compiz would only work on the first login.  If you logged out normally and/or restarted X, Compiz would never run again until you rebooted.  

But now, it works all the time every time--log out, reboot, restart X, whatever.

---

### Post by doublemeat on 2007-10-27
BTW, I also have emerald installed and enabled.  Every time I referred to "compiz" in my posts above, I meant the Gutsy-installed Compiz-Fusion, plus Emerald which I installed after upgrading.

---

### Post by metalpres on 2007-10-28
the only solution i have found so far atleast for myself is restarting X,  everytime i restart the mouse works perfect with no disappearing or flickering, but then after 5-10mins the problem comes right back with no apparent reason,  its really strange that it goes away and comes back without anything changing, or at least anything im seeing.

---

### Post by seldenthuis on 2007-10-29
The problem with animated mouse cursors disappearing (like the loading cursor in Firefox) is described [here]("http://dev.beryl-project.org/~kristian/category/the-gnulinux-desktop/compiz-fusion/") [beryl-project.org].  Apparently the 'Scale the mouse pointer' and 'Hide original mouse pointer' options of the Enhanced Zoom plugin from Compz Fusion work by changing the size of the cursor to 1x1. After zooming out the static cursors are restored, but the animated are not.  This is also why the bug appears so random.  It only occurs after the first usage of the zoom function.

The solution is to disable the options mentioned above, and probably use the 'Sync Mouse' option, log out and log back in.  The size of the cursor will now always stay the same, but it will also not disappear anymore.

---

### Post by aspora.isernia on 2007-10-30
> **seldenthuis said:**
> The problem with animated mouse cursors disappearing (like the loading cursor in Firefox) is described [here]("http://dev.beryl-project.org/~kristian/category/the-gnulinux-desktop/compiz-fusion/") [beryl-project.org].  Apparently the 'Scale the mouse pointer' and 'Hide original mouse pointer' options of the Enhanced Zoom plugin from Compz Fusion work by changing the size of the cursor to 1x1. After zooming out the static cursors are restored, but the animated are not.  This is also why the bug appears so random.  It only occurs after the first usage of the zoom function.

It is not possible for me, since I have xubuntu without compiz-fusion and beryl... :(
> 
The solution is to disable the options mentioned above, and probably use the 'Sync Mouse' option, log out and log back in.  The size of the cursor will now always stay the same, but it will also not disappear anymore.
Where can I find this option?
Thanks...

a.i

---

### Post by metalpres on 2007-10-30
> **seldenthuis said:**
> The problem with animated mouse cursors disappearing (like the loading cursor in Firefox) is described [here]("http://dev.beryl-project.org/~kristian/category/the-gnulinux-desktop/compiz-fusion/") [beryl-project.org].  Apparently the 'Scale the mouse pointer' and 'Hide original mouse pointer' options of the Enhanced Zoom plugin from Compz Fusion work by changing the size of the cursor to 1x1. After zooming out the static cursors are restored, but the animated are not.  This is also why the bug appears so random.  It only occurs after the first usage of the zoom function.

The solution is to disable the options mentioned above, and probably use the 'Sync Mouse' option, log out and log back in.  The size of the cursor will now always stay the same, but it will also not disappear anymore.

SPOT ON! awesome solution and many thanks!

---

### Post by Jonne on 2007-11-03
> **seldenthuis said:**
> The problem with animated mouse cursors disappearing (like the loading cursor in Firefox) is described [here]("http://dev.beryl-project.org/~kristian/category/the-gnulinux-desktop/compiz-fusion/") [beryl-project.org].  Apparently the 'Scale the mouse pointer' and 'Hide original mouse pointer' options of the Enhanced Zoom plugin from Compz Fusion work by changing the size of the cursor to 1x1. After zooming out the static cursors are restored, but the animated are not.  This is also why the bug appears so random.  It only occurs after the first usage of the zoom function.

The solution is to disable the options mentioned above, and probably use the 'Sync Mouse' option, log out and log back in.  The size of the cursor will now always stay the same, but it will also not disappear anymore.
Thanks a lot, that worked :). 
I thought it was related to the nvidia driver update of yesterday, but apparently it had nothing to do with it.

---

### Post by doublemeat on 2007-11-03
> **doublemeat said:**
> As an update, I tried the suggestion above.  But it prevented Compiz-Fusion from loading at all--so all I would get would be metacity.  If I tried to execute "compiz --replace" from a gnome-terminal, it would complain about something like xgl not being found.  (I researched that--apparently the intel 915 onboard graphics doesn't need xgl for compiz.)

Anywhoo, I gave up, then remembered I had changed this setting (at top).  I changed it back, rebooted, and voila--compiz was back in business.  Not only that, but the cursor disappearing problem was somehow magically gone!  (No idea how--I think the "Wiggle Method" [just mess with stuff randomly until it works even if you didn't actually change anything] worked for me again.)

And not only that, but as a second bonus side effect: since upgrading to Gutsy, I had the problem where compiz would only work on the first login.  If you logged out normally and/or restarted X, Compiz would never run again until you rebooted.  

But now, it works all the time every time--log out, reboot, restart X, whatever.

Well, I discovered accidentally that this (odd fix in quote above) wasn't actually a fix.  I just hadn't used the zooming plugin since doing this so I thought it worked.  But recently I did use zooming, and discovered the mouse pointer still disappears sometimes.  The compiz-fusion / scale mouse pointer problem mentioned earlier in this thread, was indeed the fix that solved the problem.  

So, just to reiterate: even in my case (and with intel 915 graphics), disabling scale mouse cursor on the compiz enhanced zoom plugin, fixed the disappearing mouse problem.  I noticed that there were a bunch of automatic compiz updates today, I wonder if that solves the underlying problem?  If not, no big deal.  The workaround is easy to live with.

---

### Post by Jonne on 2007-11-03
I think i spoke too soon. Even wth the zoom plugin disabled the 'busy' cursor won't show...

---

### Post by bananaman on 2007-11-05
Thank you... disabling enhanced desktop zoom fixed the problem :)

---

### Post by aspora.isernia on 2007-11-15
Very happy for your success, but... My bug is still here!!
BUT: now I have a procedure to reproduce it... And it is extremely easy: in my laptop (a Dell X200) you can press Fn+up or Fn+down to increase or decrease the brightness of the screen. Well, if I push one of those combinations, my pointer... "puff"... disappears as a kind of magic!!
Any ideas?
Many thanks

a.i

---

### Post by yhwhan on 2007-11-28
Funny thing, I have a problem that seems so similar...yet so different.

In contrast to any of you guys's problems, my cursor never appeared! I inserted the CD, rebooted my Windows XP desktop, and I'm faced with a nice and pretty Ubuntu desktop interface without a cursor! Like the guys above, my cursor still "works": If I push my mouse on the mousepad up diagnally up and to the left, then click, a menu pops down from beneath the Ubuntu icon. If I push my mouse down and the to the left, I can see the "Hide/Show Desktop" (or whatever) button light up. Leave my mouse untouched there, and the helper text box pops up: "Hide/Show Desktop" (or whatever). 

Like I said, my cursor *works* fine, I just can't see it!

I used the new Ubuntu 7.10 (Gutsy Gibbon?!?) CD.

---

### Post by Zarneth on 2007-11-29
I've been dealing with the disappearing mouse problem for half a year now. never thought it'd be compiz causing it. Disabling Hide mouse, and Scale mouse in the compiz zoom plugin fixes it though, and I can still use the zoom plugin.

---

### Post by celticninja on 2008-04-01
My problem is kinda different also:

Every time i logout of Ubuntu and log back in, the cursor is gone. But is still works

---

### Post by Jonne on 2008-04-01
Do you have compiz enabled? I fixed it by disabling the zoom plugin. Although it might be a completely different cause, ofcourse.

---

### Post by celticninja on 2008-04-01
that did it, and i also reinstalled my Nvidia drivers just in case with Envy

---

### Post by arun.pbk on 2008-06-08
Hii I had the following problem
in Ubuntu now and fedora 7,8 before.
I followed the same procedure as I did for fedora and I guess it does not dissappear again.

I have a compaq laptop with nvidia graphics.

Add 

```
Option "hwcursor" false
```
to the Device section in xorg.conf

Read more here
[http://digitalpbk.blogspot.com/2008/01/fedora-8-compaq-presario-v3000.html]("http://digitalpbk.blogspot.com/2008/01/fedora-8-compaq-presario-v3000.html")

---

### Post by carlosbertholdi on 2008-07-16
I did as arun.pbk said, adding this "Option "HWcursor" "false"" to the device section in xorg.conf, it almost work for me, instead of disappear, the cursor started blinking and every time I click, some wierd glitch appear instead of a cursor, any way, I fix this problem turning on the option above like you can see below:

Option "HWcursor" "on"

to the device section in /etc/X11/xorg.conf

---

