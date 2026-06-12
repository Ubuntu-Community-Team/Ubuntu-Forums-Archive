---
title: "Automate a pppd internet connection"
date: 2009-03-31
forum: General Help
---

### Post by UbuKunubi on 2009-03-31
Hello,
I've been attempting to do this for several days now, and my searches have raised more questions than I hoped to have answered..

My internet connection is over my mobile phone (3 skypephone) which serves me well, but I need to automate the connection and disconnection to the internet.

Basically I use my laptop for doing my normal day-to-day computing (Ubuntu Hardy), and an old desktop which, amongst over tasks, is connected to security sensors at my home.
To give this system some teeth (i.e. email any webcam captures, use a the skype4py API to call my on skype, etc) I need to use a second phone (pre-configured).
I thought I had this nailed down, but no.
Making the connection is very simple, in either python or in the terminal, BUT my problem is sending Ctrl+c to the terminal.

So is there a way I've overlooked to make a timed connection via pppd?
OR have i missed a Ubuntu automation tool that would allow keystrokes to be sent to the Terminal? I tried to install xdotool, but that went pair shape...(w.i.p.)

as in:
event ---> send "pppd call gprs"----->wait for 30 seconds (or program to complete)---> send Ctrl+c

Thanks in advance,
Ubu

---

