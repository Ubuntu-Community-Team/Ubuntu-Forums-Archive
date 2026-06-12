---
title: "increase delay time for panel minimization in &quot;Automatic Hiding&quot;, Lubuntu 15.10"
date: 2016-01-31
forum: Desktop Environments
---

### Post by anotherChris on 2016-01-31
I prefer to use "Automatic hiding" in Lubuntu's Panel Preferences to automatically minimize the panel when it's not in use.  However, this is causing me some problems (see below* for details if you want...).  **Question: **Can someone tell me how to increase the delay time in Automatic hiding between when the cursor leaves the Panel and when the Panel minimizes? I've Googled it, but can't find an answer. Thank you!!


* _Long explanation of problem_:
I frequently have to re-connect my wi-fi.  I use free wi-fi from my landlady, but for some reason it frequently drops my connection (about once or twice an hour).  To resolve, I have to go down to the wi-fi icon of the Indicator Applets in my desktop panel and then scroll/browse up the menu to my wi-fi connection and select it, which automatically disconnects and re-connects it.  HOWEVER, when Automatic hiding is on, there is not enough time between when my cursor stops hovering over the wi-fi icon and when it reaches my wi-fi connection in the menu: before I can select my wi-fi connection from the menu, the panel minimizes, which closes the menu.  As a result, about once or twice an hour, I have to go into Panel Preferences, turn off Automatic hiding, re-connect my wi-fi, then turn on Automatic Hiding again and leave Panel Preferences.  This is a pretty big annoyance, and seems like it should work better.

---

### Post by anotherChris on 2016-02-02
Nobody has an idea?  Really?  Is the question too complicated?  I just want to know how to make the panel persist longer before it minimizes when "Automatic hiding" is turned on...

Thanks.

---

### Post by vasa1 on 2016-02-02
> **anotherChris said:**
> Nobody has an idea?  Really?  Is the question too complicated?  I just want to know how to make the panel persist longer before it minimizes when "Automatic hiding" is turned on...

Thanks.
You can't blame the question (or yourself). I think your usage is something the developers of lxpanel haven't considered or provided a visible option for.

It's possible some other panel may such an option.

For example, tint2 has the following:```
# Panel Autohide
autohide = 0
autohide_show_timeout = 0.3
autohide_hide_timeout = 2
autohide_height = 2
strut_policy = follow_size
```which seems to imply users can fiddle with values.

I looked at lxpanel's options when I first saw your question but didn't find anything like that. So I kept quiet ;)

Plus, I'm still on Lubuntu 14.04 and wouldn't know if your later version of Lubuntu has what you are looking for (and I don't use lxpanel or autohide).

Edit: I don't know what your usage is or why you need the autohide feature. Even though I have a small screen (laptop, 15.6") I dedicate a few pixels (40 px or so) at the top of my screen to conky and tint2. What does your screen look like?

---

### Post by anotherChris on 2016-02-03
> **vasa1 said:**
> I looked at lxpanel's options when I first saw your question but didn't find anything like that. So I kept quiet ;)

Well, I can't argue with that.

> **vasa1 said:**
>  I don't know what your usage is or why you need the autohide feature. Even though I have a small screen (laptop, 15.6") I dedicate a few pixels (40 px or so) at the top of my screen to conky and tint2. What does your screen look like?

For some reason, when I'm using programs, the windows frequently get stuck with the bottom margin/corners stuck behind the panel.  Then I can't resize them unless I can get the panel minimized, so I just keep it on Auto-hide... except right now, I'm not using Auto-hiding.  Here's my desktop.  It's pretty sparse.  My meatspace desk looks the same... (well, no stars, but you know what I mean...)

[ATTACH=CONFIG]267089[/ATTACH]

---

### Post by howefield on 2016-02-03
> **anotherChris said:**
> For some reason, when I'm using programs, the windows frequently get stuck with the bottom margin/corners stuck behind the panel.  Then I can't resize them unless I can get the panel minimized...

Could try using the resize option in the window title bar menu. Right click on the title bar or click the window menu button to get to it.

---

### Post by anotherChris on 2016-02-03
> **howefield said:**
> Could try using the resize option in the window title bar menu. Right click on the title bar or click the window menu button to get to it.

That's cool, I didn't know about the resize function.  However, I used it once, and now it's broken... Here's what I did...

(1) Usually, I use the Un/Decorate function on windows. So...
(2) I right-clicked on the window border and selected "Use system title and borders" in order to get the window border back.
(3) Right-clicked on window border and selected Resize.
(4) Resized
(5) Selected Un/Decorate again...  Uh-oh!!  Now I don't have the window controls in the upper right corner as usual
(6) Right-clicked on window border again... Double Uh-oh!!!!  Now selecting "Use system title and borders" only restores the window controls, not the system border... (see photo)
[ATTACH=CONFIG]267092[/ATTACH]

 so that...
(7)...if I Right-click on the window border again, it only lets me shut off the system title and borders (see photo)
[ATTACH=CONFIG]267093[/ATTACH]

I can fix this problem if I stop and re-start the program, but that's not a good fix for resizing while typing web comments, or using LirbreOffice or GIMP.

---

### Post by howefield on 2016-02-03
Not sure if it works in Lubuntu but using the Alt + F8 keys works in Ubuntu as a shortcut key to resizing the window, give that a go.

If it doesn't work, there likely is a keyboard shortcut, just need to find out what it is. :)

---

### Post by vasa1 on 2016-02-03
Please post what you have in *~/.config/lxpanel/Lubuntu/panels/panel*. Just the **Global** section will do. I have this:```
# lxpanel <profile> config file. Manually editing is not recommended.
# Use preference dialog in lxpanel to adjust config when you can.

Global {
    edge=bottom
    allign=left
    margin=0
    widthtype=percent
    width=100
    height=24
    transparent=1
    tintcolor=#000000
    alpha=0
    autohide=0
    heightwhenhidden=2
    setdocktype=1
    setpartialstrut=1
    usefontcolor=1
    fontsize=10
    fontcolor=#000000
    usefontsize=0
    background=0
    backgroundfile=/usr/share/lxpanel/images/lubuntu-background.png
    iconsize=24
    loglevel=2
}

```

Also, post the section in your *~/.config/openbox/lubuntu-rc.xml* which looks like this:```
  <!-- You can reserve a portion of your screen where windows will not cover when
     they are maximized, or when they are initially placed.
     Many programs reserve space automatically, but you can use this in other
     cases. -->
  <margins>
    <top>0</top>
    <bottom>0</bottom>
    <left>0</left>
    <right>0</right>
  </margins>
  <dock>
    <position>TopLeft</position>
    <!-- (Top|Bottom)(Left|Right|)|Top|Bottom|Left|Right|Floating -->
    <floatingX>0</floatingX>
    <floatingY>0</floatingY>
    <noStrut>no</noStrut>
    <stacking>Above</stacking>
    <!-- 'Above', 'Normal', or 'Below' -->
    <direction>Vertical</direction>
    <!-- 'Vertical' or 'Horizontal' -->
    <autoHide>no</autoHide>
    <hideDelay>300</hideDelay>
    <!-- in milliseconds (1000 = 1 second) -->
    <showDelay>300</showDelay>
    <!-- in milliseconds (1000 = 1 second) -->
    <moveButton>Middle</moveButton>
    <!-- 'Left', 'Middle', 'Right' -->
  </dock>

```

---

### Post by anotherChris on 2016-02-03
> **vasa1 said:**
> Please post what you have in...

Here it is... (BTW, currently, I have Auto-hiding turned off.)  I'm guessing you are going to suggest modifying hideDelay in the XML file...?


*~/.config/lxpanel/Lubuntu/panels/panel*


```

# lxpanel <profile> config file. Manually editing is not recommended.
# Use preference dialog in lxpanel to adjust config when you can.


Global {
  edge=bottom
  allign=left
  margin=0
  widthtype=percent
  width=100
  height=24
  transparent=1
  tintcolor=#000000
  alpha=0
  setdocktype=1
  setpartialstrut=1
  usefontcolor=1
  fontcolor=#e0d7d7
  background=0
  backgroundfile=/usr/share/lxpanel/images/lubuntu-background.png
  iconsize=24
  usefontsize=1
  fontsize=10
  autohide=0
  heightwhenhidden=5
  align=center
}

```


*~/.config/openbox/lubuntu-rc.xml*


```

<!-- You can reserve a portion of your screen where windows will not cover when
     they are maximized, or when they are initially placed.
     Many programs reserve space automatically, but you can use this in other
     cases. -->
  <margins>
    <top>0</top>
    <bottom>0</bottom>
    <left>0</left>
    <right>0</right>
  </margins>
  <dock>
    <position>TopLeft</position>
    <!-- (Top|Bottom)(Left|Right|)|Top|Bottom|Left|Right|Floating -->
    <floatingX>0</floatingX>
    <floatingY>0</floatingY>
    <noStrut>no</noStrut>
    <stacking>Above</stacking>
    <!-- 'Above', 'Normal', or 'Below' -->
    <direction>Vertical</direction>
    <!-- 'Vertical' or 'Horizontal' -->
    <autoHide>no</autoHide>
    <hideDelay>300</hideDelay>
    <!-- in milliseconds (1000 = 1 second) -->
    <showDelay>300</showDelay>
    <!-- in milliseconds (1000 = 1 second) -->
    <moveButton>Middle</moveButton>
    <!-- 'Left', 'Middle', 'Right' -->
  </dock>

```


By the way, here's a super-nerdy joke...


vasa1, your signature ought to be written, "de gustibus et coloribus non disputandum est".


Get it?  Not funny?  Well, I tried...

> **howefield said:**
> Not sure if it works in Lubuntu but using the Alt + F8 keys works in Ubuntu as a shortcut key to resizing the window, give that a go.

If it doesn't work, there likely is a keyboard shortcut, just need to find out what it is. :)


Okay, in Lubuntu 15.10, it's Alt + space bar and then select "Z".  
Then you get a resizing cursor icon.  
Hold down the left click button and move your mouse/trackpad.  
If anyone wants to try this, the key is to put the cursor at the opposite end of the screen from where you want to move to ***before*** you use the keyboard shortcuts.  For example, say my window somehow got resized off the edge of my screen to the right, I will put my cursor on the right-hand side of the screen so that I can move it to the left.  If you wait to put the cursor in place after you use the keyboard shortcuts, you can accidentally resize your window in a way you didn't intend...

---

### Post by vasa1 on 2016-02-04
Your rc.xml and mine are the same. So nothing to say.

Re. lxpanel,
you have both
  align=center
  allign=left

I have just "allign=left"

I'm not sure that's a good thing but I don't think that that's responsible for the issue you described in the first post here.

In short, I'm out of ideas, never having faced such a problem myself. Plus, I don't use lxpanel except on rare occasions.

---

### Post by anotherChris on 2016-02-04
> **vasa1 said:**
> In short, I'm out of ideas...

Well, thank you for giving it a shot.  I have a question about the attribute called hideDelay...

```
<hideDelay>300</hideDelay>

```
Do you have any idea what that does?  Should I try changing it?

---

### Post by vasa1 on 2016-02-04
> **anotherChris said:**
> Well, thank you for giving it a shot.  I have a question about the attribute called hideDelay...

```
<hideDelay>300</hideDelay>

```
Do you have any idea what that does?  Should I try changing it?

No idea, but there's no harm in trying *but please backup your lubuntu-rc.xml first*.

And just in case, you don't know, after you edit lubuntu-rc.xml, it's advisable to run **openbox --reconfigure** in a terminal. Doing so has two purposes: it tells Openbox to start using the modified lubuntu-rc.xml and it also "parses" the file to check for errors.

---

### Post by anotherChris on 2016-02-06
I tried modifying the hideDelay settings and showDelay settings.  Set to 5000 milliseconds, the panel had the same persistence as set to 300 milliseconds.  

I don't know what these settings are for, but I noticed that there is another that has autohiding set to "no", even though I have it turned on.  Don't know what that's about.

---

### Post by Mirk0 on 2016-05-29
Forgive me for reopening this discussion after several months because the problem became bigger.

Lubuntu 16.04 has the same problem and it is bigger because this is an LTS version, as you know. The automatic hiding doesn't give enough time to interact with some menus, like the one for the Wi-Fi connection.

I guess the automatic hiding time is an intrinsic property of LXPanel and it cannot be modified in */home/<user>/.config/lxpanel/Lubuntu/panels/panel*.

---

### Post by jothro on 2016-06-02
I'm having a similar problem, but kinda reverted. I wanted to made an Unity-like auto-hiding launch-bar on the left side of my monitor, but often when I quickly move my mouse over to the side (e.g. when using the back button in Firefox) I accidentally un-hide the panel and launch a random program, which is very annoying.

So it would be very nice to be able to customize the hide- and show-delay, because there are many different reasons one would like to have that option, as shown in this thread. I think it should be considered for the successor LXQT-Panel, at least.

---

