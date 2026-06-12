---
title: "HOW-TO: Truly transparent borderless terminal inset in your background with Compiz"
date: 2008-02-12
forum: Desktop Effects &amp; Customization
---

### Post by mozetti on 2008-02-12
This tutorial will give you a truly transparent terminal window either as a desktop background or inset into your Ubuntu desktop (my preference). There is a screenshot showing this setup attached to the bottom of this HOW-TO.

Requirement/Assumptions
1) Gnome-terminal
2) Compiz
3) Compiz-Config-Settings-Manager (CCSM)

**_Step 1 - Setting your Gnome-terminal Profile settings_**

In terminal, either edit your current profile or create a new profile (we'll assume you named it "DesktopConsole" for the purposes of this HOW-TO) to use.

1) Under the General Tab, uncheck "Show menubar by default in new terminal" - we want a clean look here, so no menubar to clutter things up. You can always show the menubar by right-clicking the terminal.

2) Under the Title and Command Tab, change "Dynamically-set title" to **Isn't displayed***
--* This is only for Avant Window Navigator (AWN) compatibility. If AWN crashes it won't recognize the terminal as already opened with a dynamically-set title, resulting in 2 instances in your AWN bar.

3) Under the Scrolling Tab, change "Scroll bar is:" to **Disabled** - same as the menubar, we want a clean look.

4) You can choose to have a "framed" terminal like Screenshot 1 below or a completely transparent terminal (with just the text showing) like Screenshot 2 below *(coming 19-Feb-08 )* using gnome-terminal's transparency effect. Compiz finally brings true transparency to gnome-terminal's transparency effect, instead of just redrawing the desktop image as the background (pseudo-transparency) prior to compositing.

**For a "framed" terminal (Screenshot 1)**

Select the background color or image you wish to use (I use black).

Under the Effects Tab, select **Transparent Background** and adjust the slider to your liking.

**For a completely transparent terminal with just the text showing (Screenshot 2 - *coming 19-Feb-08*)**

Under the Effects Tab, select **Transparent Background** and move the slider all the way to the left.

5) Click **Close**

**_Step 2 - CCSM Settings_**

1) First, make sure you have **Custom Effects** enabled. Preferences-> Appearance-> Visual Effects and select **Custom**

2) Open CCSM

3) Under "Window Decoration", in **Decoration windows** put:

**If using your default gnome-terminal profile:**
 ```
any & !name=gnome-terminal
```

**If using a custom gnome-terminal profile:**
 ```
any & !title=DesktopConsole
```

*This removes the frame and titlebar from the terminal window.*

4) Enable the "Regex Matching" plugin. You may also need to enable the "Dbus" plugin, I can't remember but it's probably already enabled.

5) Under "Place Windows", select the Fixed Window Placement Tab.

--5a) In the "Windows with fixed positions" box, click **Add** and use these settings:

**If using your default gnome-terminal profile:**
```
Positioned windows: name=gnome-terminal
X Positions: 150
Y Positions: 75
```

**If using a custom gnome-terminal profile:**
```
Positioned windows: title=DesktopConsole
X Positions: 150
Y Positions: 75
```

--5b) In the Windows with fixed viewport" box, click **Add** and use these settings:

**If using your default gnome-terminal profile:**
```
Viewport positioned windows: name=gnome-terminal
X Viewport Positions: 1
Y Viewport Positions: 0
```

**If using a custom gnome-terminal profile:**
```
Viewport positioned windows: title=DesktopConsole
X Viewport Positions: 1
Y Viewport Positions: 0
```

[i]These settings (along with Step 7) will get the terminal window around the center of your desktop. My resolution is 1440x900, so you'll need to tweak these to your liking once you get everything set.

Apparently Compiz starts counting viewports at 0, because using 1 puts the terminal on my 2nd viewport, and using 2 puts the terminal on my 3rd viewport.[/i]

6) Under "Window Rules" 

**For a terminal window of specific size (not fullscreen):**

In the "Fixed Size Windows" box click **Add** and use these settings:

**If using your default gnome-terminal profile:**
```
Sized Windows: name=gnome-terminal
Width: 1250
Height: 750
```

**If using a custom gnome-terminal profile:**
```
Sized Windows: title=DesktopConsole
Width: 1250
Height: 750
```

**For a fullscreen terminal:**

Skip or Undo Step 5a , follow step 5b and then in the **Fullscreen** box use this setting: 

**If using your default gnome-terminal profile:**
```
name=gnome-terminal
```

**If using a custom gnome-terminal profile:**
```
title=DesktopConsole
```

--*This will make the terminal fullscreen and appear to be a desktop background instead of being inset.*

8) Click **Close** and then fire up terminal. If all works well, then you'll have a borderless, truly transparent terminal window on a specific viewport, in a specific place, with a specific size.

---

### Post by DaymItzJack on 2008-02-13
I'm so glad you posted this, it's way better than using devilspie.

Just some things I did instead of you that others might like:

I made a new profile instead of using the default one (I named it "DesktopConsole"). That way not _every_ terminal you load will be a background terminal.

If you make that change, you'll probably want to change everything he put from
```
name=gnome-terminal
``` to ```
title=DesktopConsole
``` (note, you still need !'s where he put his)

After I changed that around, I set up the "Widget layer" (the first time I've done this.) and set the "Widget Windows" in the Behaviors tab to "title=DesktopConsole". That way you can press F9 (you might have to set this) and it'll pop up to the front for you to use.

I also didn't do your "Solid color" suggestion because the transparency works fine if you have compiz running, without messing with Opacity settings.

I did a few more things that probably didn't matter much/others wont care for.

Thanks again for this, I'm glad you posted it.

---

### Post by mozetti on 2008-02-13
Thanks for the additional options. And I agree about devilspie -- it's a great program, but Compiz can accomplish it without needing another program and using workarounds.

---

### Post by mozetti on 2008-02-13
bump

It's my first HOW-TO and I've seen a number of requests for something like this over the past few days.

---

### Post by airbornemist6 on 2008-02-13
My first question is, what exactly does this look like? could you screenshot it for those of us who have no idea what exactly you're talking about and don't really want to waste time following the guide when we don't even know what exactly it does.

---

### Post by mozetti on 2008-02-13
> **airbornemist6 said:**
> My first question is, what exactly does this look like? could you screenshot it for those of us who have no idea what exactly you're talking about and don't really want to waste time following the guide when we don't even know what exactly it does.

Sorry, I meant to add a screenshot but hadn't gotten to it. I've added a screenshot to the first post showing the "inset" terminal (notice the top & bottom terminal edges cutting across the moon). Size, placement on the desktop, placement on particular viewport, and opacity can all be set by the user so it appears exactly as you choose.

 If you used the fullscreen option, you wouldn't see the edges.

---

### Post by skankster on 2008-02-13
Hello, it's not quite working for me.

STEP 1

I've unchecked "Show menubar by default...etc." but the menu still appears.

STEP 2

Some of the Window recognition stuff is working. I've set terminal title "DesktopConsole" in the profile, and I use title=DesktopConsole everywhere. It's the window sizing and positioning that doesn't seem to work. Transparency is fine, as is the removal of the Window Decorations.

I've gone through the instructions and I can't see that I've missed anything.

Using xwininfo I can see that the title is DesktopConsole.

I don't suppose there's anything else I need to check? 

Thanks.

---

### Post by skankster on 2008-02-13
Okay, I got it working. I think it might be that I gave the profile a different name to DesktopConsole. Seems you need that and the Title to be set the same. Either that or one of the many restarts fixed it. Anyway, many thanks. Works a charm, now.

---

### Post by DaymItzJack on 2008-02-13
If you look at the screenshot, you can see a black square, that won't happen if you use the terminals transparency instead of compiz fusion's.

---

### Post by mozetti on 2008-02-13
> **DaymItzJack said:**
> If you look at the screenshot, you can see a black square, that won't happen if you use the terminals transparency instead of compiz fusion's.

You're right! I thought that even with Compiz, the gnome-terminal transparency still faked it. But, that's not the case. I kind of like the look of both ways, so I'll have to see which one I stick with. It's way too late here, so I'll update this HOW-TO and add another screenshot in a few days (off to Paris tomorrow). :D

---

### Post by DaymItzJack on 2008-02-13
> **mozetti said:**
> You're right! I thought that even with Compiz, the gnome-terminal transparency still faked it. But, that's not the case. I kind of like the look of both ways, so I'll have to see which one I stick with. It's way too late here, so I'll update this HOW-TO and add another screenshot in a few days (off to Paris tomorrow). :D

I would hate to see that black box around the sides on my desktop. Also the way you do it, the text is also kind of transparent which would make me mad. ;p

---

### Post by mozetti on 2008-02-14
Ok, updated the HOW-TO to use gnome-terminal opacity settings instead of Compiz. It's a better choice, considering the Compiz opacity also fades the text.

---

### Post by skankster on 2008-02-14
Here's a couple of items that may be of use to people. This is to get around a few foibles that may be system specific, or may be more general. Remember mileage may vary:

1) I found that if I save the running apps in Sessions, when I re-start I get a large terminal window on the wrong desktop with no transparency and with window decoration. By putting the gnome-terminal command in the start-up section and making sure I close my terminal(s) when I save currently running apps, this is avoided.

2) I have also found that I need to make the DesktopConsole profile the one to be used when starting a new session. Using --window-with-profile=DesktopConsole in the gnome-terminal session start-up area didn't work (for some as yet unknown reason).

3) To enable myself to open terminals with a profile that's not the DesktopConsole one, I've added the following to the Compiz-Fusion commands (under General):

gnome-terminal --window-with-profile=Default

and set-up a short-cut key for it under Actions (also under the General in Compiz-Fusion). I've used Ctrl+Alt+T but obviously this is individual preference. 

Now I have a permanent, transparent background one, and can call up others if and as and when needed.

---

