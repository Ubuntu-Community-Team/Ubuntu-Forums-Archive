---
title: "Move application between screens (not workspaces)"
date: 2009-08-15
forum: Desktop Environments
---

### Post by jctweb on 2009-08-15
I feel like I'm 90% "there" with what I'm trying to achieve... a little background first:

In WinXP (at the office), I run a program called "UltraMon" - very cool.
Anyway, one of the coolest features (to me, at least) is the ability for me to move windows between desktops.  It adds a little icon in the window bar.

What's even cooler is that a maximized window moves to maximized status - in the resolution of the destination monitor!  So moving a maximized firefox from my main screen running at 1680x1050 over to an attached LCD @ 1440x900 simply resizes the firefox window - and vice versa.

The other cool thing is ultramon adds an additional taskbar to the external monitor.

enough background...

Here's what I was able to to do:
[LIST]
[*]The panel is located on the bottom - on the external monitor
[*]I added the "window list" app to the pane
[*]The window list only shows the open applications that are on that monitor!  (way cool)
[/LIST]
OK - all that I have left is to either
[LIST=1]
[*]get a button in the window manager that moves the applications between the two monitors
[*]figure out a keyboard shortcut that moves the maximized application between the two monitors
[*]mouse gesture to move the active window?
[/LIST]

I've been researching this for a couple of days and it doesn't look like there's "one solution to rule them all" - anyone else able to accomplish this?

My system:
Dell e1505
ATI x1400 video
OSS ATI Video drivers
Compiz running like a champ :)
Main screen: 1680x1050
External screen: Dell 19" LCD 1440x900

thanks for any help anyone can provide!

[Solved] See it here:
[http://ubuntuforums.org/showpost.php?p=8572940&postcount=3](http://ubuntuforums.org/showpost.php?p=8572940&postcount=3)

---

### Post by littlesatan on 2009-12-28
Problem still not solved? I ask because it's actual trouble for me now.

---

### Post by jctweb on 2009-12-28
Actually - I figured it out; but neglected to update this:

Using CompizConfig Settings Manager, there's an item called "Extra WM Actions"

In the General Tab, the last item is "Move Window to Next Ouput"

I set the shortcut to <Control><Super>Right

So now I can switch a maximized app between the two screens - even if it's maximized.

---

### Post by littlesatan on 2009-12-28
Jctweb, thanks for your answer.
Are you sure that *extra wm*+*mwno* is the whole solution?

---

### Post by jctweb on 2009-12-28
It's possible that I have other settings as well.  I've attached the file I exported from compiz.

---

### Post by littlesatan on 2010-01-10
So. []
Your config didn't solve the problem, but cause a few of new troubles (when I load my own old config it's all gone).
[] thanks for your participation.

---

