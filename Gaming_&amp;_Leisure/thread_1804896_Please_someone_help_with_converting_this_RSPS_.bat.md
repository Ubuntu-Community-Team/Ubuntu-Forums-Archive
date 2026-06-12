---
title: "Please someone help with converting this RSPS .bat into a Shell Script!"
date: 2011-07-15
forum: Gaming &amp; Leisure
---

### Post by RawrFace on 2011-07-15
Hey,

I have been looking everywhere and even tried writing this shell script my self but almost blew up my computer ahahah I suck and i'd seriously appreciate some help here so can sombody please convert this .bat into a .sh

Here it is: 

@echo off
Title Client
START java -Xmx512m Gui 30 0 lowmem members 32
exit

Thankyou <snip>

---

### Post by RawrFace on 2011-07-15
Bump

---

### Post by hakermania on 2011-07-15
Bumping after AT LEAST 24 hours without reply please!
Please explain the functionality of this strange (for non-window users) BATCH script.
What does it do?

---

### Post by RawrFace on 2011-07-15
It is the equivalent of a .sh on linux... Basically a CMD (terminal equivalent) command...

---

### Post by RawrFace on 2011-07-15
Bump, Please this is urgent!

---

### Post by Elfy on 2011-07-15
Please stop bumping so soon or I will close the thread for 24 hours.

---

### Post by Toz on 2011-07-15
Youtube to the rescue? [http://www.youtube.com/watch?v=R4HfBgrIA1Y]("http://www.youtube.com/watch?v=R4HfBgrIA1Y")

---

### Post by RawrFace on 2011-07-15
Thanks for trying mate but alredy seen that video and it tells you nothing... I have written this so far:

#!/bin/bash
echo Client
java -Xmx512m Gui 30 0 lowmem members 32
exit

That opens the client but then there is that error thats more to do with the server that has a page with yellow text and it has 3 steps for you to try.. I tried all of them nothing worked... :S

This is the error screen: [IMG]http://img862.imageshack.us/img862/9655/clientmessup.png[/IMG]

---

### Post by doorknob60 on 2011-07-15
A lot of times even if you correctly open RSPS'es in Linux, a lot of times they still don't work right and crash (like that). THe only solution I've found is to use Wine, install the windows version of Java, and run wineconsole run.bat on the original .bat file. I have no clue why this happens, but it seems like most RSPS servers do not work on Linux without Wine :(

---

### Post by RawrFace on 2011-07-15
Okay, Could you please give me instructions on how to do that? I alredy have wine installed but IDK about the Java shiz :p

---

### Post by RawrFace on 2011-07-15
NVM Mate got it tyvm everyone for you help, closing thread in a min.

---

### Post by donkyhotay on 2011-07-16
if you got it working it's polite to post the answer in case someone else has the same question later.

---

### Post by HolgerB on 2011-07-17
Amazing how lazy and/or stupid people sometimes seem to be :(

it took me something like 20 seconds googling to find a complete how-to for setting up a RSPS (= Runescape Private Server, for the roughly 80% here in the forum which didn't know ;)) under Linux.

:P

---

### Post by RawrFace on 2011-07-26
> **HolgerB said:**
> Amazing how lazy and/or stupid people sometimes seem to be :(

it took me something like 20 seconds googling to find a complete how-to for setting up a RSPS (= Runescape Private Server, for the roughly 80% here in the forum which didn't know ;)) under Linux.

:P

L2 Read N00B I wasn't asking how to run it i was asking for a SHELL SCRIPT... (GAY)

---

### Post by HolgerB on 2011-07-26
> **RawrFace said:**
> L2 Read N00B I wasn't asking how to run it i was asking for a SHELL SCRIPT... (GAY)
Yayh..you're polite one :P

yezzzz...but in the other post you asked about 
"...Could you please give me instructions on how to do that?"

:popcorn:

---

