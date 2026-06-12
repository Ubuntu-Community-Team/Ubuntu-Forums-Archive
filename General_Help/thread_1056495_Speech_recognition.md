---
title: "Speech recognition"
date: 2009-01-31
forum: General Help
---

### Post by z.s.tar.gz on 2009-01-31
Where is linux at with speech?
The latest news I can find is from 2005.

---

### Post by gettinoriginal on 2009-02-01
This one is in beginning stages, but only for desktop control
[http://packages.ubuntu.com/intrepid/gnome-voice-control](http://packages.ubuntu.com/intrepid/gnome-voice-control)

Here is one that is commercial, but has a linux release:
[http://www.voiceware.co.kr/english/products/ez.html#](http://www.voiceware.co.kr/english/products/ez.html#)

---

### Post by z.s.tar.gz on 2009-02-06
gnome voice control looks good
thanks! just wanted to know

---

### Post by NuttyMonk on 2009-02-07
Can the gnome voice control be used to do other things such as dictate text into open office word processor?

Has anyone used the xvoice package?

[http://www.zachary.com/s/xvoice](http://www.zachary.com/s/xvoice)

Cheers

NM

---

### Post by rvk on 2009-08-21
Not yet, for something like that it is necessary that many people submit speech at VoxForge. Without enough speech it would not make any sense to add dictation to gnome-voice-control. That would only lead to frustration among those who use it.

It's not so much adding more functionality that's a problem in this field, but collecting enough copyright free speech to train the software with. If you want to help out, go to VoxForge and submit (preferably a couple of hours) of speech and tell other people to do the same.

---

### Post by Mariane on 2009-09-06
Why can't they just record something on the radio? Or if they are afraid that someone would check they can use a text to speech system. And please don't tell me we have none of these, I remember having one on windows 3.1. They get the thing to read something which is in the public domain and record that. 

As for the commercial one mentioned above, it's not for linux pc, it's only for linux servers. 

There is a list here:
[http://tldp.org/HOWTO/Speech-Recognition-HOWTO/software.html](http://tldp.org/HOWTO/Speech-Recognition-HOWTO/software.html)

Some links don't work, many say "This software is primarily for developers". It's like Julius, HTK and all that, it takes days to get the things to differentiate between 2 words. 

I mean, why so many things for developpers and not a single developped application that you can run without having to train the damned thing, to give it a langage model, to teach it grammar or whatever not... ??? 

Mariane

---

### Post by luisuebel on 2009-09-06
There is  a big reason to don't have free speech recognizers available: cost!!!
Speech databases cost a fortune to built, validate and organize.

I build a Brazilian speech database and I can tell you that took me many months, hundreds of speakers and cost a lot. All good American English databases are paid (usually from LDC) and cost a lot. There are very few speech database for dictation in other language. Usually are from companies that work with speech recognition, synthesis or so on.

This Brazilian Portuguese speech database that I mention has more than one thousand hours of speech. There are more than 3 papers saying that should built a speech database with over one thousand speakers, but no one did. Why? Cost money and time. It is easier to write a paper than build a  speech database. Same for text.

My PhD supervisor told me "Paper accepts everything!!!".


Luis Uebel ([www.asrlabs.com](www.asrlabs.com))

---

### Post by Mariane on 2009-09-07
I'm sure it takes ages, but can you please tell me 

- Why not use speech from whatever available source (eg TV) instead of asking people to record themselves specifically for that? 

- Once the system is trained, there is no way it can be "reverse engineered" to get from the speech recognition to the original speech data. So what is preventing someone with access to a big database from training a speech recognition system and putting online even without the training data? 

Mariane

---

