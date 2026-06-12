---
title: "[SOLVED] Change lineup of dual display"
date: 2007-07-23
forum: Desktop Effects &amp; Customization
---

### Post by andrewsawyer on 2007-07-23
All,

I have a twin screen setup on my laptop using Xinerama with a TFT output at 1280x1024 and the laptop display at 1024x768.  This works fine, with one annoying issue that I'm hoping someone might be able to 'fix'.

When you look at my displays, they are lined up with the monitor on the left and the laptop on the right, and all is lined up by the top pixels:

   +------------------------+ +-----------------+
    |,,,,,,,,,,,,,,,,,,,,,,,,,,|  |,,,,,,,,,,,,,,,,,,,|
    |,,,,,,,,,,,,,,,,,,,,,,,,,,|  |,,,,,,,,,,,,,,,,,,,|
    |,,,,,,,,,,,,,,,,,,,,,,,,,,|  |,,,,,,,,,,,,,,,,,,,|
    |,,,,,,,,,,,,,,,,,,,,,,,,,,|  +-----------------+
    +------------------------+

The problem is, I don't want to sit my laptop on top of a stack of books to bring it up to the right lever (so that when you move the mouse across screen, it lines up).  What I would like, would be to have xorg.conf 'fixed' to line the monitors up by the bottom pixels as below:

   +------------------------+
    |,,,,,,,,,,,,,,,,,,,,,,,,,,| +-----------------+
    |,,,,,,,,,,,,,,,,,,,,,,,,,,|  |,,,,,,,,,,,,,,,,,,,|
    |,,,,,,,,,,,,,,,,,,,,,,,,,,|  |,,,,,,,,,,,,,,,,,,,|
    |,,,,,,,,,,,,,,,,,,,,,,,,,,|  |,,,,,,,,,,,,,,,,,,,|
    +------------------------++-----------------+

Does anyone know how I might be able to do this?  I'm not at the computer at the moment, so can't provide a xorg.conf right now, but can if needed.  I would assume however (if this is possible) that it would just be a generic one liner added in somewhere.

Thank you in advance,

Andy

---

### Post by shavenlunatic on 2007-07-23
can't you just click and drag the monitor around in the nvidia display settings?

---

### Post by andrewsawyer on 2007-07-23
I am using Xinerama on an Intel i810 chipset - not an nVidia chipset.  Otherwise yes - I could.

---

### Post by Soybean on 2007-07-23
I don't remember the exact method, and I'm using TwinView now, so I can't check... but if you post your xorg.conf, someone should be able to tell you what needs to be changed. :)

---

### Post by MrHippocampus on 2007-07-23
Without seeing your xorg.conf I cant be sure if this will work, but it *should*.

your existing xorg.conf will have a line in ServerLayout saying something like:

```

Screen "Screen 1" Rightof "Screen 2"

```

Instead of saying Rightof/Leftof you can position the top left corner of the second display relative to the top left corner of the first display (Coordinates work with x increasing left to right and y increasing top to bottom).

```

    Screen "Screen 1"
    Screen "Screen 2" Relative "Screen 1" 1280 256

```

That will place the second screen 1280 pixels across and 256 pixels down from the top left of the first screen, hopefully that should work.

---

### Post by andrewsawyer on 2007-07-23
Thank you!

Now I see it written I remember it!  Thank you all for your help.

Andy

---

