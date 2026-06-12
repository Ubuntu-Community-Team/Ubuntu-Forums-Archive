---
title: "Windows will not stretch across screens in multi screen mode"
date: 2010-05-12
forum: Desktop Environments
---

### Post by Jonners59 on 2010-05-12
I have 10.4 and nVIDEA 5500 on my PC.  I am running two screens, run as twin so that the desktop spans the two monitors.

I have noticed that when I try and stretch a window across the two screens, very useful in spreadsheets, the window 'pings' back to a much smaller size.

I open in, say my main monitor.  I move the window to span across the two and than manually stretch the window.  It will stretch to some extent but if I then go beyond a certain pint it then slams shut.

Screen shots on enclosed which I hope makes sense of what I am saying.

Also, if I click the MAXIMISE button on the window it only expands to full screen in one terminal.

This did NOT happen in 9.10, and does not happen in any Windows OS, so I know it has something to do with the new 10.4 build.

---

### Post by Jonners59 on 2010-05-13
[SIZE=5][B][COLOR=Red]Any Help, Please.  This has been hanging around for a couple of days

[/COLOR][/B][/SIZE]> **Jonners59 said:**
> I have 10.4 and nVIDEA 5500 on my PC.  I am running two screens, run as twin so that the desktop spans the two monitors.

I have noticed that when I try and stretch a window across the two screens, very useful in spreadsheets, the window 'pings' back to a much smaller size.

I open in, say my main monitor.  I move the window to span across the two and than manually stretch the window.  It will stretch to some extent but if I then go beyond a certain pint it then slams shut.

Screen shots on enclosed which I hope makes sense of what I am saying.

Also, if I click the MAXIMISE button on the window it only expands to full screen in one terminal.

This did NOT happen in 9.10, and does not happen in any Windows OS, so I know it has something to do with the new 10.4 build.

---

### Post by Jonners59 on 2010-05-23
[color=red]any help please????????????????????????[/color]

---

### Post by sruetti on 2010-05-27
I can't really help you but only confirm the problem.

I'm running ubuntu desktop 10.04 with a ATI Radeon HD 5770, proprietary (fglrx) drivers (8.723.1-100408a-098580C-ATI). I'm using the ATI specific multi-head solution "Multi-display desktop with display(s) 2". I have two displays 1024x1280 (portrait) next to each other.

Since it affects ATI and nVidia it's likely not a bug in the driver. To me it looks like a problem with the hints snapping windows to the display borders as it is still possible to have windows across two display.
@Jonners59: What geometry do your displays have? Might the problem arise with screens in portrait mode?

With a bit of trickery I can even expand a window to multiple display: I move the window of about the size of one display to the right screen, about 1/4 of the width if this screen away from the right border. I then can expand the window with one of the right border handles up to the right display border without it snapping anywhere. If the initial distance is to big (1/2 of the screen is to big...) it will snap to the left border of the right screen (i.e. the middle border). That way, i can enlarge a window by about a quarter of the display width. By repeating this procedure, I can even expand a window to roughly the size the whole two displays.

---

### Post by Jonners59 on 2010-05-27
Yup, I get the same.  Interesting none of the developers or experts have been able to assist.  I too believe it's a bug.  It did not happen in 9.10, interestingly, though the setup was easier.

I do hope one of them takes an interest and tried to help us.

---

### Post by acroporas on 2010-05-27
This is a "Feature" of Compiz.  If I recall properly, this feature was actually introduced in 9.10. I suspect that you just did not have compiz enabled before, or else you just never noticed it.

Workarounds:
 - Resize your windows with alt + F8
 - Resize your windows with alt + middle click
 - Disable Compiz

---

### Post by acroporas on 2010-05-27
I found the explanation.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/455378](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/455378)

> Resizing by dragging window borders is limited to work area by Compiz to prevent window edges from becoming inaccessible while resizing by going behind panels or beyond screen edges. To handle this issue, Metacity instead uses snapping during resize, which Compiz 0.8.4 lacks.

---

### Post by Jonners59 on 2010-05-28
> **acroporas said:**
> 
Workarounds:
 - Resize your windows with alt + F8
 - Resize your windows with alt + middle click
 - Disable Compiz

This is great.  At least I do not feel alone, and I can see others find it a pain too.  What happened to choices, and being of the free world.  Besides the ability to look at more than one window at once to compare, the other point of two screens is to spread wide open any doc, especially a spreadsheet.  Understand the reasoning, I did find some MS Office docs would go "off screen" and had to be forced to close, but a bad move in execution, again.  I think a "Alt + Right click or F8" if you got stuck, because that's when you need it and you would look in the list of view options for a solution.  The default should have been the other way round.

OK, the F8 works, but not as convenient...
Alt+ Middle click, I found as RIGHT click on my mouse

And how does one "Disable Compiz"...????

---

### Post by acroporas on 2010-05-28
> **Jonners59 said:**
> 
And how does one "Disable Compiz"...????

System -> Preferences -> Appearance

Go to Visual Effects, select None

---

### Post by Jonners59 on 2010-05-28
Al though it would be nice to have more control - in simple form for us non techies, something for the developers to thin k about, this is great and solves the problem very effectively.  Thank you.

[INDENT]- Resize your windows with alt + F8
 - Resize your windows with alt + middle click
 - Disable Compiz:
[INDENT]System -> Preferences -> Appearance
Go to Visual Effects, select None

[/INDENT]:)
[/INDENT]

---

