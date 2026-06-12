---
title: "How to use DCOP in a GNOME environment"
date: 2009-09-02
forum: Desktop Environments
---

### Post by Clordio on 2009-09-02
Hey guys, tried searching and couldn't find an answer.

I'm trying to write a command or script in KAlarm to make amarok play at a certain time. It seems the only solution would be to go through DCOP but I can't figure out how to access it.

I know it is in my /usr/bin/ folder but I am unsure of how I can write a script or command to make use of its "amarok player void play()" command.

Thank you for the help friends.

PS
I've done a bit of programming in the past but scripts make no sense to me. Any tutes you guys could point me to to brush up on scripts would be appreciated!

---

### Post by Clordio on 2009-09-02
Bump for those who just got off work

---

### Post by quill3033 on 2009-12-29
Hi, 
I don't know how to use DCOP (Don't really know what that is) in gnome but I do have gnome and I do get Kalarm to open Amarok and play a particular file. 

I open kalarm, go to New Alarm and select Command (in Action where the options are Text, File, Command or Email)

Then I just write 

amarok '/home/username/foldername/songname'

Username and foldername and songname you have to replace with your own, of course. And yes   '/home/username/foldername/songname' must be in inverted commas (single).

When I am too lazy I just open a terminal and type amarok and then I open the file manager and go to the song file and grab it with the mouse and drop it in the terminal window right next to amarok and press return. If it works, then I copy that text onto a text file and then copy and paste onto the kalarm command window. I have a text file with a few different commands for songs that I like to play. 
You can then also try your alarm by pressing the Try button on the alarm dialogue box and if your song starts to play then you know it will work once you save it. Occasionally I just have to include "ENTER" in the kalarm command, if it hasn't worked. 

I have also used KAlarm to open Rhythmbox and vlc and again just done it first in a terminal window to see if it works and then copied the command onto the KAlarm command window. 

I use it to wake up in the mornings - with Rhythmbox the great thing is that it continues to play other songs in my library if it is set to random playing mode - so I wake up to music. Haven't yet worked that out in Amarok because I mostly use it if I only want one song and also mostly use it for listening to online radios - amazing collection.

Hope this helps. 

Similarly if I want to clean the house to music I start playing rhythmbox or whatever file and then create an alarm with kalarm for the time I need to stop and do something else - so that kalarm shuts down the music and  I am warned. Again with rhythmbox I just write in the command

killall rhythmbox
killall amarokapp (don't know why but I noticed that only saying "killall amarok" didn't do the trick and when I started amarok from the terminal it seemed to call itself amarokapp... 

I also use it to start and stop heaps of programs like ktorrent etc. 


Word of caution - my only problem with kalarm in gnome is that it tends to crash the first time I start it in a session or when I get it to start at login/startup. I suspect that has a bit to do with the fact that I have heaps of alarms going at once and it goes a bit mad trying to open them all if I've had the pc off for a while. Otherwise it is fantastic and once opened (after like 7 crashes in a row) it works like a charm. Still looking for the solution to that one but haven't been able to find it. ...
Occasionally I just open a Terminal window when it is crashing and type 'killall kalarm' (no inverted commas necessary) and then start it again. 
Hope this helps/makes sense. If not just ask. I'll do my best to explain it better.
Maybe someone will know why kalarm crashes...

---

