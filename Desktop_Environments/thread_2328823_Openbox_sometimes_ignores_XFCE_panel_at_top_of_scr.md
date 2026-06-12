---
title: "Openbox sometimes ignores XFCE panel at top of screen"
date: 2016-06-24
forum: Desktop Environments
---

### Post by &amp;KyT$0P# on 2016-06-24
I have a Xubuntu 16.04 VM with 2048-qt installed.  The window size of 2048-qt is too big vertically for my virtual screen, and I don't have room on my physical screen to increase the virtual screen vertical size.

Using xfwm4, the 2048-qt window is placed immediately below the panel on the top of the screen, with a (unimportant) small amount of the bottom of the window off-screen.
Openbox places the window at the very top of my screen - under the xfce panel - and I can't access the menus.  Fortunately, the bottom of the window is visible, so I can right-click it > Move, and drag it down.

Openbox does see an edge where the panel is - as it will edge-resist when dragging a window under/out-from-under the panel.
I've tried setting margin in Openbox but it seems to ignore that.

Something I notice, in my Lubuntu 14.04 the bottom of my top panel is seen as "0" whereas here the very top of the virtual screen is what's seen as "0".

I'm finding that XFCE desktop + Openbox window manager to be the most stable environment that suits my needs, so using other desktop environment or window manager won't work.

So how to prevent Openbox from placing windows under the XFCE panel?

---

### Post by vasa1 on 2016-06-24
Does 2048-qt accept any --geometry type arguments? If so, you could specify the size of its window when it starts up.

Or maybe it remembers its last size and opens again to the last size?

(I don't know anything about virtual screens). I used to play 2048 a bit before but I don't remember it being a qt app then. Now it wants to bring in all of qt5 :(

What do you have in ~/.config/openbox? Do you have rc.xml?

If you've sorted out the opening size issue, you could try editing rc.xml to set where exactly 2048 opens. 

After you've backed it up for safety, check it in a terminal with **openbox --reconfigure**. There should be no pop-up. If the xml has been messed with, you'll get a pop-up.

Now, go right to the bottom of the file to the section that starts with **<applications>** and ends with </applications>. It has a lot of commented out lines that indicate just what this section can do. Here's a part:```
    <position force="no">
      # the position is only used if both an x and y coordinate are provided
      # (and not set to 'default')
      # when force is "yes", then the window will be placed here even if it
      # says you want it placed elsewhere.  this is to override buggy
      # applications who refuse to behave
      <x>center</x>
      # a number like 50, or 'center' to center on screen. use a negative number
      # to start from the right (or bottom for <y>), ie -50 is 50 pixels from the
      # right edge (or bottom).
      <y>200</y>
      <monitor>1</monitor>
      # specifies the monitor in a xinerama setup.
      # 1 is the first head, or 'mouse' for wherever the mouse is
    </position>
```

---

### Post by &amp;KyT$0P# on 2016-06-24
This from 2048-qt man page:
```
OPTIONS
       2048-QT is configured graphically and does  not  have  any  commandline
       options.


```
There are no options to graphically change the startup window size.  Anyway I'm just using 2048-qt as a working example, I'm sure other programs are affected too.

> What do you have in ~/.config/openbox? Do you have rc.xml?
Yes and that's it.

> you could try editing rc.xml to set where exactly 2048 opens.
Thank you that suggestion fixes 2048 :D
What's odd is the exact XML code to place the 2048 window immediately below the top panel:
```

    <application title="2048 Game">
      <position force="yes">
        <x>center</x>
        [COLOR="#FF0000"]**<y>0</y>**[/COLOR]
      </position>
    </application>
```
The desired <y> is apparently 0 and not the vertical size of the top panel.  This configuration directly contradicts the Openbox window position indicator.
So I'm not sure what to think?

(Just a note for passers-bys, the comments starting with # are apparently not treated as comments by the XML parser and if they contain anything that looks like XML tags it will cause [FONT=Courier New]openbox --reconfigure[/FONT] to bork exactly as described by vasa1 with an error message that's hard to make sense of.  Mousepad's syntax highlighting was really helpful to figure that out.)

Anyway thanks again vasa1 for the fix. :KS

---

### Post by vasa1 on 2016-06-25
> **halogen2 said:**
> ...
What's odd is the exact XML code to place the 2048 window immediately below the top panel:
```

    <application title="2048 Game">
      <position force="yes">
        <x>center</x>
        [COLOR="#FF0000"]**<y>0</y>**[/COLOR]
      </position>
    </application>
```
The desired <y> is apparently 0 and not the vertical size of the top panel.  This configuration directly contradicts the Openbox window position indicator.
So I'm not sure what to think?

(Just a note for passers-bys, the comments starting with # are apparently not treated as comments by the XML parser and if they contain anything that looks like XML tags it will cause [FONT=Courier New]openbox --reconfigure[/FONT] to bork exactly as described by vasa1 with an error message that's hard to make sense of.  Mousepad's syntax highlighting was really helpful to figure that out.)

Anyway thanks again vasa1 for the fix. :KS
Hi, if you also have obconf, take a look at it. I think Openbox tries not to let application windows cover panels, docks, systrays, etc. So even when a window is maximized, the area taken by them is excluded. If you start playing with the "snap" aspects of rc.xml, you'll agree.

About comments, the impression I have is that anything following **#** is seen as a comment unless, as you say, the parser thinks it's xml code. Oh, and the parser doesn't like **--** in comments!

If you want more on rc.xml, aka lubuntu-rc.xml if you're running a Lubuntu session, there's [a wiki bit]("https://help.ubuntu.com/community/Lubuntu/Windows#Launching_Windows_Maximized_or_Fullscreen") I wrote a couple of years ago and two links I found very helpful:
[http://pclosmag.com/html/Issues/201011/page09.html](http://pclosmag.com/html/Issues/201011/page09.html) ::: LXDE: Meet The Heart & Soul — lxde-rc.xml
[http://pclosmag.com/html/Issues/201107/page08.html](http://pclosmag.com/html/Issues/201107/page08.html) ::: Openbox - Edit rc.xml to Gain Control

---

### Post by &amp;KyT$0P# on 2016-06-25
> Hi, if you also have obconf, take a look at it. I think Openbox tries not to let application windows cover panels, docks, systrays, etc. So even when a window is maximized, the area taken by them is excluded. If you start playing with the "snap" aspects of rc.xml, you'll agree.
I do have obconf, but none of the settings there seem to change this.  In all cases:
 - maximized windows maximize below the top panel
 - 2048-Qt opens above & under the panel (unless rc.xml is manually edited as above)

After discovering this I tried maximizing 2048 and that also gets it placed below the panel.

So maybe it's actually some setting in XFCE that takes precedence over the Openbox configuration, in terms of how Openbox treats that panel?
(Panel settings can make windows go above the panel but they always stay under it.)


And thanks for the links on rc.xml.

---

### Post by vasa1 on 2016-06-25
BTW, thanks for reminding me about 2048. I had it installed as a browser version quite some time ago. I dug it out again after reading your post!

---

### Post by &amp;KyT$0P# on 2016-06-26
no problem :mrgreen:

---

