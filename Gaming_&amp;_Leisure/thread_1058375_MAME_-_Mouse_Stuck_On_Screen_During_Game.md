---
title: "MAME - Mouse Stuck On Screen During Game"
date: 2009-02-02
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2009-02-02
Hi. Recently I started up MAME on my laptop. I noticed that my mouse was stuck on the screen when I started a game. Does anyone know how to stop this?
Thank you.

---

### Post by FranMichaels on 2009-02-03
Have it launch full screen by default (rather than switching to it by alt + enter)

Or try to whip the mouse to a corner before the icon get's stuck there.

I've figured out the cause mostly, you have onboard intel?

man intel

it's the SW or HW cursor option. Disabling it fixes it, but no acceleration. So you are basically stuck until a newer driver that isn't so lame comes out. I'm personally looking forward to GEM and the next gen intel drivers.

---

### Post by Rytron on 2009-02-03
> **FranMichaels said:**
> Have it launch full screen by default (rather than switching to it by alt + enter)

Or try to whip the mouse to a corner before the icon get's stuck there.

I've figured out the cause mostly, you have onboard intel?

man intel

it's the SW or HW cursor option. Disabling it fixes it, but no acceleration. So you are basically stuck until a newer driver that isn't so lame comes out. I'm personally looking forward to GEM and the next gen intel drivers.

Hello FranMichaels. Acer 5220 laptop. I'll try your advice. Thank you.

---

### Post by Rytron on 2009-02-03
> **FranMichaels said:**
> Have it launch full screen by default (rather than switching to it by alt + enter)

Or try to whip the mouse to a corner before the icon get's stuck there.

I've figured out the cause mostly, you have onboard intel?

man intel

it's the SW or HW cursor option. Disabling it fixes it, but no acceleration. So you are basically stuck until a newer driver that isn't so lame comes out. I'm personally looking forward to GEM and the next gen intel drivers.

How can I disable it? When you say no acceleration, can I still play all the games?

---

### Post by Rytron on 2009-02-04
I disabled the touchpad but there was no change. I like using Gxmame with xmame on my main computer(desktop) but I decided to try a new MAME emulator for my laptop to get past this cursor problem; I went [here]("http://ubuntuforums.org/showthread.php?t=545066"). I settled for SDLmame with Loemu. Everything is purring like a kitten. No more cursor problem.

:popcorn:

---

