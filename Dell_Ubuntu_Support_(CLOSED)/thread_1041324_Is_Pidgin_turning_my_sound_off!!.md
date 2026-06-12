---
title: "Is Pidgin turning my sound off?!?!"
date: 2009-01-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ancalagon82 on 2009-01-16
Okay, so this is the 4th time in 12 hours.  What the heck?!?!


Dell Mini9, Dellbuntu, completely stock except Adblocker and DosBox.


Okay, so I listen to music over Youtube.  Well yesterday I got Pidgin up an running.  After that it seems that every couple hours the sound just turns off.  It never does it when I'm playing music, but seems to do it between times.  I'll go play a new song and and I can see the video but no sound.  It's not on mute, I try fiddling with all the controls, nothing.   Only thing that helps is rebooting.   Oh and when I do this I can close every program fine except Pidgin.  I then just go shuterdown and it takes a good couple minutes.

I wanna say Pidgin has something to do with it, but I've only had this thing since Weds night so who knows.

---

### Post by EXCiD3 on 2009-01-16
I have the same issue sometimes with Rhythmbox where watching a Flash video or something will steal audio control from Rhythmbox where it cannot play any longer. Closing firefox completely sometimes fixes or logging out always does. Sound support in Linux has a ways to go still, but i can wait. :)

---

### Post by Ancalagon82 on 2009-01-16
It did it again!

This isn't just sometime.   This is every hour or two I have to shut down.  BS.  This is a totally stock machine, out of the box 2 days ago, and it's already broke.

---

### Post by Ancalagon82 on 2009-01-16
So I muted Pidgin, and haven't had a problem since.


But now it sucks b/c my eye doesn't catch the icon changing from Green to Orange, and it doesn't flash or anything to get your attention.   

Are there any other messenger programs that do a better job of getting your attention w/out using sound?

---

### Post by ElTimo on 2009-01-16
You can actually make the taskbar flash by adding the "Message Notification" plugin to pidgin. It's already installed, so just enable it in the plugin menu (Tools->Plugins).

Hope this helps.

---

### Post by Ancalagon82 on 2009-01-16
> **ElTimo said:**
> You can actually make the taskbar flash by adding the "Message Notification" plugin to pidgin. It's already installed, so just enable it in the plugin menu (Tools->Plugins).

Hope this helps.

Sweet!  Even better than pings!

---

### Post by ElTimo on 2009-01-16
Glad I could help! I seriously don't know why that plugin isn't enabled by default, but o well.

---

### Post by khc on 2009-01-17
> **Ancalagon82 said:**
> So I muted Pidgin, and haven't had a problem since.

I think that is a bug in gstreamer-pulseaudio, a fix was recently pushed out to fedora, so ubuntu may get that in 9.04.

---

### Post by shiningkenmonster on 2009-01-17
I had that problem too. Go to System > Preferences > Sound

In the Device tab. make everything to use ALSA - Advanced Linux Sound Architecture

It fixed for me. But I have only tested this for a day. Since I have done this yesterday for the first time. This other person said it has fixed for him.

tell me if it has fixed it or not. i hope this help

---

### Post by pormogo on 2009-01-18
^ that fix should work for you. By default ubuntu runs it's sound through the pulse audio sound server, but this seems to break all kinds of stuff (has been since 7.10 for me). 

Unfortunately that's not totally going to fix your problem. Some apps like flash will access sound with pulse audio absolutely (I have no idea how to change it). Sometimes these applications "lock" your sound. You can check by opening a terminal and doing an

lsof | grep -i snd

this should show you all applications that have the sound interface /dev/snd/* accessed. Note that pulse audio/your sound applet will almost always maintain open connections to these devices. If your sound is crashed you will likely see npviewer, firefox, or additional pulse audio forks accessing sound. Just a heads up. Sounds is still the most iffy part of my ubuntu experience. 

If you want to free all of your sound up you just need to restart X (the graphical part of ubuntu) by pressing cntrl+alt+backsapce. Much faster then rebooting.

EDIT: BTW pidgin could be stealing your sound, it has a sound setting outside of the main system settings. There is a chance is doesn't follow default settings and it might be trying to use pulse by default as well.

---

### Post by Klaus 255 on 2010-09-07
I have Ubuntu on my laptop and recently, even if i am simply watching a movie i hear a rising three tones and sometimes they tone descends but it keeps doing that out of no apparent reason.

I read somewhere that it may be something called pidgin but i don't know what that is or why it would/could be making this noise and most important of all how to turn off that constant nuisance .

---

### Post by Klaus 255 on 2010-09-07
Can anyone help?? Please its driving me crazy and its probably an easy fix too

---

