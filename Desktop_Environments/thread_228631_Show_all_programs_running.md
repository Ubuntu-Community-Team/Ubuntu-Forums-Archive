---
title: "Show all programs running"
date: 2006-08-03
forum: Desktop Environments
---

### Post by geovino on 2006-08-03
How do you show all programs running? 

Everytime Streamtuner freezes I can do a xkill to Xmms but it freezes everything because some other processes are running and you don't know what they are. So I end up restarting the computer which I should not have to do. 

Any clues?

---

### Post by redbull_monsta on 2006-08-03
sudo ps -ef < shows everything
or
sudo ps -fp | grep streamtuner < to just get id for streamtuner

by looking at the pid (process id) and ppid (parent process id) you will be able to see all processes spawned by the application too

---

### Post by endfx on 2006-08-03
Open a terminal and type:
ps aux

If you want to find a particular program that is running do a:
ps aux | grep program
e.g. ps aux | grep xmms

Now you kill the process that is causing you trouble:
kill PID

You get the pid from the ps command above.

If the program really won't die try this:
kill -9 PID

---

### Post by geovino on 2006-08-03
> **endfx said:**
> Open a terminal and type:
ps aux

If you want to find a particular program that is running do a:
ps aux | grep program
e.g. ps aux | grep xmms

Now you kill the process that is causing you trouble:
kill PID

You get the pid from the ps command above.

If the program really won't die try this:
kill -9 PID

What is the command line for killing xmms? or streamtuner? 

Is there a way to configure streamtuner and xmms so they play together without crashing?

---

### Post by h00s on 2006-08-03
> **geovino said:**
> What is the command line for killing xmms? or streamtuner? 
Type 'ps -A' to list processes (to find application process id) and then 'kill [process_id]'.

> Is there a way to configure streamtuner and xmms so they play together without crashing?

I have experienced crashing xmms with and without using streamtuner. Now I'm using bmp and it's working fine. Afcourse, it works with streamtuner too. Maybe you should try bmp too ;)

---

### Post by geovino on 2006-08-04
Thanks, I installed beep. How do I change the preferences in Streamtuner to use beep instead of xmms?

---

### Post by moma on 2006-08-04
Beep instead of Xmms in Streamtuner
You can change it in [preferences dialog...]("http://home.online.no/~osmoma//tmp/streamtuner2.png")

$ sudo apt-get install beep-media-player
And make Sreamtuner to launch: [COLOR="DarkSlateGray"]beep-media-player[/COLOR]

You need to kinda double click in the Streamtuner's preferences, command field to edit it.

If you're unenlightened about the diff between xmms and beep.
beep-media-player has a modern GTK 2 user interface. While xmms is based on the lousy, old fashioned horrible GTK 1.

But wait till Xmms2 reaches v1.0 ! 
It gonna blow out the others.
[http://en.wikipedia.org/wiki/XMMS2]("http://en.wikipedia.org/wiki/XMMS2")

---

### Post by geovino on 2006-08-04
I did that. I changed xmms to beep-media-player. But it says error: check   for correct output plugin. Isn't that beep-media-player? Beep opens and tries to play, but it won't play.

---

### Post by h00s on 2006-08-05
Hmmm, I have now checked my preferences in streamtuner and for playing stream is set to xmms :confused: but it plays in beep

I don't get it :???:

Edit:
Here's the thing.
If you don't have running bmp or xmms, it's start xmms and plays strem in it. But, if you first run beep and then tune to station in streamtuner, it plays in beep. A bit weird...

---

### Post by geovino on 2006-08-05
After installing some gstreamer files Beep is now working with Streamtuner and so far has not crashed on any live stream. :)

---

