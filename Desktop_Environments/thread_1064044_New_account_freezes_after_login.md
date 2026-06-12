---
title: "New account freezes after login"
date: 2009-02-08
forum: Desktop Environments
---

### Post by license on 2009-02-08
I've been using the same account for a few weeks now with no problems. I'm trying to create a new account for my wife and I'm not able to get further than logging in. I tried to create her account from the command line but when I logged in with that account, these problems started, so I deleted that account and its home dir. Then I used the administration menu to create an account with the same username and had the same problem. Then I tried to create an account with a different username. No use.

I'm links to some photos I took (no screencap for obvious reasons). I didn't embed because they're pretty big and I don't want to break the
page formatting.

When I log in to the account I created for her directly after booting, I get to the desktop with 2 media locations on it but no menu bar. When I try to open either of the media locations, or create a launcher, the OS freezes (although the cursor continues to rotate).
[http://antilicense.googlepages.com/useracctprobs2.JPG](http://antilicense.googlepages.com/useracctprobs2.JPG)

If I log in to my own account after boot, and then log out and log in to the new account, I get an empty beige screen. Momentarily, a light grey box appears in the upper left corner occupying approximately 1/9 of the screen. Moving the mouse pointer into this box changes it to a text edit icon. Typing bash commands into it appears to do nothing.
[http://antilicense.googlepages.com/useracctprobs1.JPG](http://antilicense.googlepages.com/useracctprobs1.JPG)

What is going on?

Thanks!

---

### Post by Yashiro on 2009-02-10
What video card and driver are you using?

---

### Post by license on 2009-02-10
Looks like it's an Intel GMA950.

I'm not sure how to check the driver. This portion of my xorg.conf seems to be relevant but it looks pretty generic. Anyway it worked out of the box, haven't had any problems up to now.

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

---

### Post by Yashiro on 2009-02-11
That's the generic 'no driver' xorg. Which means that IF your account is set to use Desktop Effects, which sounds to be the case, then it will show a blank screen or weird artifacts.

I'm not sure that this is your issue though. Hard to say from the info. You could try using the actual intel video driver or uninstalling compiz from synaptic.

But like I say, I'm not sure that this is the cause. As a troubleshooting step removing compiz won't kill anything anyway.

---

### Post by license on 2009-02-11
I'm not sure how to switch the driver. I tried installing xserver-xorg-video-intel as indicated by this thread:
[http://ubuntuforums.org/showthread.php?p=2431414](http://ubuntuforums.org/showthread.php?p=2431414)
But it was already installed although Ubuntu isn't trying to use it. I guess I could just edit xorg.conf but I don't know what I should put in there.

I enabled some of the compiz effects and they seem to be working in my account without a hitch. After doing so, I switched to the account I created for my wife (without logging out) and this time, I could see the menu bar. When I tried to open firefox from it, the menu bar became unresponsive. However, I could still open the media location on the desktop. When I did, it said I didn't have permission to open it. The message box was responsive and when I clicked OK the media location disappeared. At this point the desktop was entirely unresponsive except for the mouse cursor. I ctrl+alt+backspaced and logged back into my account just fine.

Maybe this is a permissions issue - do I need to chmod some graphics driver related configuration file(s)?

Thanks!

---

### Post by Yashiro on 2009-02-11
Disable Compiz and see what happens. Do not use the fast user switching style of logging in/out. It's very buggy.

---

### Post by license on 2009-02-11
I thought I had compiz disabled in the first place, but I went ahead and removed it. Progress! I could open Firefox but there was no title bar, although it seemed to work otherwise. I tried to go into the Appearance menu to see if I could make some adjustments there and then it become unresponsive again.

Getting closer...

Thanks again.

---

