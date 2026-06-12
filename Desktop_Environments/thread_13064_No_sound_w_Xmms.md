---
title: "No sound w/ Xmms"
date: 2005-01-28
forum: Desktop Environments
---

### Post by bombrill on 2005-01-28
Hi all, 

I guess my sound card is working properly as I have sound when I start up my ubuntu. The thing is that I can't play any file in xmms. Nothing happens when I double-click.. 

I you have any idea.. 

Thx

bombrill

---

### Post by Perfect Storm on 2005-01-28
Did you follow the ubuntuguide? You can find it at 'HOWTO'-board.

I'm not at my Ubuntu machine at the moment, but it's properly you need to setup digital sound for XMMS to play music CDs. 
Open XMMS
press <ctrl>+<p> there should be a plugin called audio-something. Mark it and press the configure button. Then choose Digital output.

I hope I said the right thing, as I said I'm at work on win machine :P

---

### Post by Perfect Storm on 2005-01-28
Okay I got my hands on a linux machine at my work.

Here it is:

Open Xmms
<ctrl>+<p>
Under the 'Audio I/O Plugins' there's a file called 'CD audio Player 1.2.10 Click and choose the 'configure' button. Under 'play mode' choose 'Digital audio extraction'.

---

### Post by bombrill on 2005-01-29
Actually, I was speaking about playing mp3.. :o) but that's interesting too: here's the behavior of my machine :
When I put an audio, first, the OS detects it and launch CD player. So, I tried to play the cd with cd player... And nothing is happening again !? when I press on the play button.. nothing's moving.. 'guess it's the same problem.

---

### Post by Perfect Storm on 2005-01-29
Do you have **libmikmod2** installed?

---

### Post by bombrill on 2005-01-30
Yep... i have it installed...

---

### Post by bombrill on 2005-01-31
Still no idea ?  ](*,)

---

### Post by nocturn on 2005-01-31
[QUOTE=bombrill]Still no idea ?  ](*,)[/QUOTE]

If you have audio in other programs, try this

Make sure you are using esd (the sound daemon).
Install the xmms esd plugin

Choose esd as sound output.

Also, check the mixer to see is some channels are muted or the volume is turned down.

---

### Post by bombrill on 2005-01-31
I don't know what happened... I tried one of the many combination between the output plugin and the destination.. and it works finally..
Thx a lot !  =D> 

Bombrill

---

