---
title: "Trying to use xpad the xbox driver but the stupid notepad thing keeps intercepting"
date: 2013-08-01
forum: Gaming &amp; Leisure
---

### Post by Boingloing on 2013-08-01
I run Lubuntu for 64 bit computers, installed it last week.

I have an Xbox Original -> USB adapter that I ordered for use with my DDR pad. I was having lots of trouble with windows 7 so I got into Linux. Right out of the box, the pad was working in the game, but I couldn't press L + R or U + D at the same time (EVERYONE who has tried to use a DDR pad with a PC is very familiar with this).
I know that xpad comes with Linux, and I know that it has a variable "dpad_to_buttons". I need to set it to 1.

However, every time I open Terminal and try to modify anything with xpad, it thinks I'm talking about xpad, the sticky note software. I just can't modify that value. Can anybody offer suggestions?

---

### Post by slooksterpsv on 2013-08-01
When in terminal type in xpad and press tab it should give you a list of apps. If the name is the same you can change it via:
 update-alternatives --config xpad

---

### Post by Boingloing on 2013-08-06
I tried typing xpad and pressing tab, and I got a list of apps.
xpad is not on that list.

However, when I type xpad, the sticky note thing still comes up. I must be doing something incorrectly.

---

### Post by Ranko Kohime on 2013-08-07
xpad is a kernel driver, and doesn't have an application named "xpad" into which you can place settings.  After some Googling, I was unable to find the location of a settings file, either.

---

### Post by Boingloing on 2013-08-07
well what's the point of having settings, then? >.>
silly xpad

---

### Post by Ranko Kohime on 2013-08-08
After doing a search for "dpad_to_buttons", I came up with a variety of links to the source code for xpad.  So my guess is going to be that you need to make the change in the source code and recompile xpad.

---

### Post by Boingloing on 2013-08-10
all right, I'll try that
thanks

who knew trying to get a controller to work would get me doing so many different things (it's the entire reason I got linux to be honest)

---

