---
title: "ZSNES no sound"
date: 2008-03-21
forum: Gaming &amp; Leisure
---

### Post by NR1224 on 2008-03-21
Im using 8.04 hardy and am getting no sound in the ZSNES emulator. I can see the game and it runs perfectly but i get no sound. All other sounds on my computer work fine, its just he emulator that is giving me trouble. I have also heard that 8.04 has some sound issuses, and if that is causing it any help would be appreciated

---

### Post by acoustibop on 2008-03-21
Do zsnes --help in a terminal, NR1224, and you'll get a list of ZSES' switches, including the various sound formats you can use.  Try each one of these, and see which work; then you can set it as default by editing /.zsnes/zsnesl.cfg where it says "libAO driver to use."

---

### Post by HunterK on 2008-03-21
And when you DO get sound to work, it might be very choppy.  For me, to resolve that, I had to set the sampling rate to 48,000kHz instead of the 41kHz default option.

---

### Post by NR1224 on 2008-03-21
Thanks, i found that the sdl driver worked! i am bit confused on how to make it dafault though. Where is the zsnesl.cfg file located? Thanks again

---

### Post by FranMichaels on 2008-03-22
> **NR1224 said:**
> Thanks, i found that the sdl driver worked! i am bit confused on how to make it dafault though. Where is the zsnesl.cfg file located? Thanks again

Open up a terminal

```
gedit ~/.zsnes/zsnesl.cfg
```

Or you can get to it in nautilus, press ctrl+h or View menu -> Show hidden files. All hiden files beging with .
So there ya go, you zsnes settings and saves etc are in .zsnes

Nice and neat that way :)

---

### Post by nearadyn on 2008-06-14
Yeah, thanks! This worked for me too. I just added the line:
-ad sdl in that config file. I don't know if it matters where you put it, but I put it in the sound section. I'm still new at Ubuntu. I am impressed with this emulator though now that I have sound! It runs the games perfectly with no lag. All I need now is a gamepad type controller that is Ubuntu friendly and it'll be just like playing on the original system! \\:D/

---

### Post by acoustibop on 2008-06-14
That won't work, nearadyn, it's a command line switch.

Either do```
zsnes -ad sdl
```in a terminal, or edit your zsnesl.cfg file so that in the section that reads```
;  ----
; -- Sound --
;  ----

; libAO driver to use. Use zsnes --help to see valid list.
; However "auto" (to automatically pick best one), and "sdl" should
; always be available.
libAoDriver="auto"
```you insert whatever driver you want to use instead of "auto" (keep the inverted commas) - but *not* with the -ad switch.  Do```
zsnes --help
```in a terminal for a list of available drivers.

Either of those methods does the same thing: sets ZSNES to use that driver from then on.

Most USB controllers work fine with Ubuntu; however, if you don't need force feedback controls, don't get a force feedback controller; the force feedback buttons are seen as axes rather than switches in many applications, and this can prevent the controller working properly.

I've been using a Logitech RumblePad 2 (wired) for a few years now, and it's an excellent Playstation style controller.  Works beautifully as soon as it's plugged in, very robust and great build quality.  It also has a particularly nice extra: a "Mode" button that swaps functions between the directional pad and the first analog stick, so that when you're playing a game with digital only directional controls, you can still use the stick as your directional control.

---

### Post by ShadowMKII on 2008-06-14
How come when I do "zsnes --help" I am told that the command is not found? Even if I go "sudo zsnes --help" it does not work.

---

### Post by nearadyn on 2008-06-15
acoustibop,
Thanks for the advice. But you said that what I did couldn't work. It did work! (or at least something worked) Because I didn't have sound before and after doing that, I did. I'm not sure if there wasn't another factor in there, but it does work now. I did, however give your solution a try and took out the line I added, and that too works! Maybe I just got lucky with that...?
I will be getting the gamepad you suggested tomorrow. That will make my mission to beat Super Mario World again much easier!:) I was wondering how to find one that's ubuntu friendly. Next on my shopping list is a printer/scanner that is as well. Computer components and devices all say whether they work with XP and Vista, why can't they say they work with Linux? They'd sell more products to those of us who care about such things.

---

### Post by acoustibop on 2008-06-15
Most HP products work well with Linux, nearadyn; I don't know about combined printer scanners, but I've installed a few HP printers and they've all installed no problem.  See [here]("https://help.ubuntu.com/community/Printers") for the Ubuntu documentation page for installing printers (including all-in-one printers).

I also have an Epson Perfection 1250 scanner - getting on a bit now, but Ubuntu just picks it up and it works fine with XSane.

---

