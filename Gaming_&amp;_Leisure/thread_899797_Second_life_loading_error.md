---
title: "Second life loading error"
date: 2008-08-24
forum: Gaming &amp; Leisure
---

### Post by rwslippey on 2008-08-24
I have been trying to get this running for about a week now... and I kind of new to ubuntu... 

I installed second life from the apt-get installer... and I can run the game however it comes up and has a steady loading screen but never acctually loads...

It just sits their with their sybol spinning saying loading...   

my computer never freezes or anything crazy it just never loads. I have asked on the second life forum and their kind of lost as to what it could be...

anyone have any ideas


running ubuntu 8.04

---

### Post by cathuria on 2008-08-24
I am having the same problem running on Hardy-64 . . . although the log-in screen never loads, you can still log in as normal.
This was okay with the old viewer, but with the new (1.20), most of the Search functions are web-based (?), anyhow, they have a browser-like interface and they, too, remain black-screen and never load, making searching in the new viewer effectively non-functional.

I'm guessing it has something to do with SL's web-style connections -- but don't really have a clue as to how to fix it yet.

---

### Post by rwslippey on 2008-08-25
I forgot to mention I am also running 64...


you had said that you are still able to log in ... unfortunatly attempting to log in gives me another page with terms and conditions of use that says loading and never loads...  is their a way i can get an older version as the only version i have found is a beta... possibly an older version will work???

---

### Post by Perfect Storm on 2008-08-25
Start it up via the terminal; check for output.

---

### Post by rwslippey on 2008-08-25
their were a few things here the cought my eye...

not exactly sure what to do with them... I'd past the whole return but it is pretty long...

heres some of the stuff that stood out...

Warning: Did not register secondlife:// handler with KDE: Directory /home/robert/.kde/share/services does not exist.


2008-08-25T13:29:04Z INFO: anotherInstanceRunning: Checking marker file for lock...

2008-08-25T13:29:04Z INFO: anotherInstanceRunning: Marker file isn't locked.

2008-08-25T13:29:04Z INFO: initMarkerFile: Checking marker file for lock...

2008-08-25T13:29:04Z WARNING: ll_apr_warn_status: APR: No such file or directory

2008-08-25T13:29:04Z WARNING: ll_apr_warn_status: APR: No such file or directory

2008-08-25T13:29:04Z WARNING: ll_apr_warn_status: APR: No such file or directory

2008-08-25T13:29:04Z INFO: anotherInstanceRunning: Checking marker file for lock...

2008-08-25T13:29:04Z INFO: anotherInstanceRunning: Marker file isn't locked.




their was alot more that came back in the terminal but they were the erros that I saw....  again not sure what to do with that though... If I made any comment at all I'd probobly get laughed at...

---

### Post by cathuria on 2008-08-25
There is this discussion of the same problem on the SL forum:
[http://forums.secondlife.com/showthread.php?t=278046](http://forums.secondlife.com/showthread.php?t=278046)

A lot of that went over my Linux-head (at least at my current Linux-height :) ) -- but seems to suggest a serious incompatibility with the Mozilla lib in a 64-bit environment.  I really don't think I want to jump through all those chroot-hoops to solve the problem -- I may just wait for a while to see if the code in either the viewer or the mozlib is improved.

---

