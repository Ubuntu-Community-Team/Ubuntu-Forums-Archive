---
title: "Random Text Pastes when typing or clicking"
date: 2009-04-08
forum: General Help
---

### Post by sck007 on 2009-04-08
In Ubuntu, my mouse will randomly click, usually making me type really poorly by moving my cursor, or as in the case of a few seconds ago, delete some of the text I was typing. My keyboard also does similar things. It will copy random text that I have already written, highlighted, or from the URL address, or even random text from a page that I was on, and paste it at random while I'm typing. I can't figure out any pattern as to why it is doing this.  Did not have this problem running XP or Slax.

Using HP DV8100 Laptop
Ubuntu Intrepid 8.10

---

### Post by maheshasolkar on 2009-04-08
I had a similar problem on a Sony Laptop with Synaptics Touchpad. I don't remember how I got there, but I added the following in my /etc/X11/xorg.conf

```
Section "InputDevice"
  Identifier "Synaptics Touchpad"
  Driver "synaptics"
  Option "SendCoreEvents"    "true"
  Option "Device"            "/dev/psaux"
  Option "Protocol"          "auto-dev"
  Option "HorizScrollDelta"  "0"
  Option "RightEdge"         "950"
  Option "MaxTapTime"        "225"
  Option "MaxTapMove"        "160"
  Option "MaxDoubleTapTime"  "225"
  Option "SingleTapTimeout"  "180"
  Option "MinSpeed"          "0.40"
  Option "MaxSpeed"          "0.90"
  Option "AccelFactor"       "0.0060"
[B][COLOR="DarkRed"]  Option "RTCornerButton"    "0"
  Option "RBCornerButton"    "0"[/COLOR][/B]
  Option "SHMConfig"         "on"
EndSection
```

What is important is the highlighted part - it turns off the corner button functions (right-click and paste). You may have to pick the correct Driver and the Device option, as applies to your machine.

---

### Post by sck007 on 2009-04-08
so how do i get there in order to change those settings?

---

### Post by maheshasolkar on 2009-04-09
> **sck007 said:**
> so how do i get there in order to change those settings?

Open the /etc/X11/xorg.conf file with super-user privileges:

```
  gksudo gedit /etc/X11/xorg.conf
```

If you already have the 'InputDevice' section in your xorg.conf, add the highlighted section from my post in it. If you don't have any 'InputDevice' section, add the entire Section from my post in the file. Save the file and exit the editor.

You will have to restart the X server for this to take effect. Save all your data and do the following:

[LIST]
[*]Switch to another TTY by pressing ALT+CTRL+F2
[*]Restart X:

```
  sudo /etc/init.d/gdm restart
```

[/LIST]

Now log back in and see if things are any better.

---

### Post by sck007 on 2009-04-30
k

---

### Post by sck007 on 2009-05-02
fix seemed to work for a little bit, but it has resorted back to its old ways and is still inserting text.  The settings in xorg.conf are the same as your post now.

---

### Post by bak&#305;r on 2011-12-15
This problem is driving me crazy, too. I am fed up with all the irrelevant things that are pasted all of a sudden. I have an acer aspire running 11.10 and the  /etc/X11/xorg.conf file already contains the indicated part. Has anybody come up with any solution?

---

### Post by hakermania on 2011-12-15
This (in your eyes random) text may come up from pushing the middle button of your mouse?
If you're not clicking it, then is it (maybe) very sensitive?

Just some thoughts :/

---

### Post by bak&#305;r on 2011-12-15
I do not understand what you mean exactly by the "middle button" (there are only two), but it is of course not so random. There is a region on touch pad located upper right, just near the scrolling thing, which seems to be a shortcut to "paste".  I cannot disable this function however. It is almost impossible to scroll without touching that!

---

### Post by hakermania on 2011-12-15
> **bak&#305 said:**
> I do not understand what you mean exactly by the "middle button" (there are only two), but it is of course not so random. There is a region on touch pad located upper right, just near the scrolling thing, which seems to be a shortcut to "paste".  I cannot disable this function however. It is almost impossible to scroll without touching that!

Oh, then that's what probably is causing the problem. Ubuntu (and linux in general I think) have a function which saves the text you have selected and can paste it using your mouse wheel (middle button) (screenshot of middle button: [http://tinyurl.com/3w6d8vx](http://tinyurl.com/3w6d8vx))

If you use a touchpad then you should click both buttons simultaneously so as to behave like a middle click.

---

### Post by bak&#305;r on 2011-12-15
It is not something with the simultaneous clicking of buttons, but something with the touchpad itself. I can make it paste by touching that upper right part on purpose. As you also mentioned, it is pasting some previously selected text, which I am struggling to disable. Do you have any idea about how to disable this middle click function anyway? It may still work for me.

By the way, thanks for your time.

---

