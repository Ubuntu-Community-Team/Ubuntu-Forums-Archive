---
title: "I messed up remix 10.04"
date: 2010-07-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Denton Larson on 2010-07-05
Hi Everybody

Well I messed up remix 10.04 on my Dell 10, I know my bad. 

I was looking around and figured I could put in HardwareSupportComponentsVideoCardsPoulsbo

located in [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#lucid](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#lucid)

That is my bad, do you know how to get back my Dell mini 10? 
this is whet I put in

sudo add-apt-repository ppa:gma500/ppa && sudo apt-get update

sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d poulsbo-config

I then restarted my my mini 10 and it now has a white screen, this is what I get. It said Netbook launcher, not respondeing

Any idea as to what to do? I am green to Ubuntu, sorry.

Denton Larson

---

### Post by mikewhatever on 2010-07-05
You can use the netbook remix without the netbook launcher. Not as pretty, but does the same. Press alt+f2 and type 'killall netbook-launcher' without the quotes. Hit enter.
Add the Main Menu applet to the panel and disable the netbook launcher from loading in the startup application.

---

### Post by Denton Larson on 2010-07-08
I got it solved with Jeff WE0A helping me.

It is GREAT!

Denton Larson

Solved

---

### Post by fatface on 2010-07-09
> **Denton Larson said:**
> **I got it solved with Jeff WE0A helping me**.

It is GREAT!

Denton Larson

Solved

How?

---

### Post by Denton Larson on 2010-07-09
> **fatface said:**
> How?

Well he said I had to select Ubuntu Netbook Edition 2D rather 
than Ubuntu Netbook Edition.

He saw that before. He does not work with Ubuntu just something he has seen'

When I got home I erased sudo add-apt-repository ppa:gma500/ppa && sudo apt-get update

and it is fine for now.

I just will do something else!:D

Denton Larson

---

