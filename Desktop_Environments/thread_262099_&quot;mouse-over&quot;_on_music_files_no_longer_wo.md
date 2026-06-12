---
title: "&quot;mouse-over&quot; on music files no longer working..."
date: 2006-09-21
forum: Desktop Environments
---

### Post by puppy on 2006-09-21
Hi, everyone, when I initially installed my system, 'mousing-over' music files in a folder and letting it stay there for a moment or two cause them to start playing (without loading some external application as far as I can tell) but for some reason they no longer do so.

The only thing I can think that might have caused this problem is that I recently installed Kaffeine (for its easy-to-set-up Digital TV properties) and from that point on whenever I clicked on an audio file on a webpage it would load and play it in Kaffiene, or a kaffeine plugin in the webpage. This isn't at all what I wanted so I changed all mp3 files to open with amarok instead... I'm using Ubuntu btw (not Kubuntu) but I just prefer that music application to the Gnome alternatives.

Does anyone know what I can do to get mouse-over music playback back again? I thought it was a really nifty feature

---

### Post by jd65pl on 2006-09-21
There is a property in nautilus which enables mouse over music previews could you check if it is enabled.

open nautilus
goto *EDIT > PREFERENCES*
Select the preview tab
Check the setting for sound files

Thanks

J

---

### Post by puppy on 2006-09-21
Thanks for the quick reply - I'm on a old windoze box at work at the moment, but I'll report back later. 

Just out of interest, how is the system actually playing the files without (visibly) loading a music app? Is it some nautilus plugin or something? I'm just intrigued by the mechanics of it. It's a very attractive feature, and exactly the kind of thing that gets Windows-using friends of mine interested when they look at my machine... I'd love to be able to explain it to them.

---

### Post by jd65pl on 2006-09-21
I think it uses a command line music player to run them, not sure which one tho.

J

---

### Post by puppy on 2006-09-21
That didn't work - in fact it was already set in Nautilus - any other suggestions as to why mouse-over no longer works on audio files??

---

### Post by mgmiller on 2006-09-21
try installing (or reinstalling or completely uninstalling and reinstalling) either mgp123 or mpg321.  I have mpg321 installed in my dapper box and the mouse over works for mp3's, but not for ogg.

---

### Post by puppy on 2006-09-22
Wonderful :D 

Installing mpg321 (which wasn't installed) fixed it - mouse-over now works on mp3 files in nautilus.

Many thanks, you're a :KS

---

