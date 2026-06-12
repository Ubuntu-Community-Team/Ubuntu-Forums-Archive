---
title: "Removing transparency in terminal"
date: 2010-05-07
forum: Desktop Environments
---

### Post by rperrin on 2010-05-07
By default in Lucid, Gnome Terminal  is transparent.

I was on my new Lucid install[1], in Terminal, typing away on the far side of some sshes, and reading some code, when I noticed how awkward it was to read because the background was showing through. "Fine", I thought, "I know where that setting is, although it's a strange default".

But Terminal's "Edit Profiles->Edit->Background" revealed it was set to "Solid color". In fact, setting it to "Transparent background", and cranking the Shade up to Maximum was one way of removing the transparency.

A little hunting around revealed that "System->Preferences->Appearance->Visual Effects" could be set to None instead of Normal, and that would fix the problem.

So, your choices for a functional terminal are to disable all Compiz eyecandy, or to turn on transparency in order to turn off transparency.

Does this strike anybody else as wrong? Is there another control I've missed?

- Richard

[1] First install on modern hardware in a looong time, so I've missed all this compiz stuff till now.

---

### Post by jonthysell on 2010-05-08
Yeah I agree, this should be a bug. Thanks for the setting transparency to max tip though, now I can use something other than that awful transparent purple.

---

### Post by svk on 2010-05-08
I would like to know if it's possible to *adjust* the transparency in the terminal.  It's actually kind of useful to me, but the default is a little bit too transparent and hard to work with.

---

### Post by KdotJ on 2010-05-08
> **svk said:**
> I would like to know if it's possible to *adjust* the transparency in the terminal.  It's actually kind of useful to me, but the default is a little bit too transparent and hard to work with.

Yeah this can be easily done... by opening a terminal and going to:

Edit > Profile Preferences > Background

There is a slider bar on there which will allow you to adjust the transparency.

I personally like it, I have my terminal black (quite transparent) with white text :p

---

### Post by svk on 2010-05-08
All right, I think I got what I wanted (a slightly less transparent background), but it's so very counter-intuitive!  In order to* decrease* the transparency, I actually had to move the transparency slider in Gnome terminal preferences to the* right* (which is supposed to *increase* transparency!!!).

Here's the original problem that rperrin, the topic starter, was referring to.  When the "Solid color" option is selected in Gnome terminal preferences (with Visual Effects turned on in System->Preferences->Appearance), the background is actually transparent:

[IMG]http://imgur.com/R5pBW.png[/IMG]

When you change the setting in Gnome terminal to "Transparent background", here's what happens when the slider is half way (roughly the same):

[IMG]http://imgur.com/ClpPM.png[/IMG]

When it's all the way at "maximum" transparency, the background actually becomes solid!

[IMG]http://imgur.com/CscYn.png[/IMG]

This is a little bit backwards!  I got what I wanted by moving the slider to about 80%.

---

### Post by floomby on 2010-05-20
I had this as well, although not that transparent, more like a barely noticeable transparent.

---

