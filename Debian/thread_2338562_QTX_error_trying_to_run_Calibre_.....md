---
title: "QT/X error trying to run Calibre ...."
date: 2016-09-29
forum: Debian
---

### Post by jethro-uk on 2016-09-29
For no reason I can think of, I can't run Calibre.I get :xxxxx@xxxxxxxxxxx:/mnt/NewRAID/Misc$ calibrefailed to get the current screen resourcesQXcbConnection: XCB error: 172 (Unknown), sequence: 163, resource id: 150, major code: 149 (Unknown), minor code: 20The X11 connection broke: I/O error (code 1)XIO:  fatal IO error 0 (Success) on X server ":50.0"      after 368 requests (368 known processed) with 0 events remaining.I am connecting in via X2Go and have been for 5 years. I always upgrade when advised.Anyone any suggestions, please. Dr. Google seems to hint this is a known bug - but there is no fix ????Is this a QT error, or an X error ? And - more importantly - what do I need to do to start fixing it ?Sorry for **** formatting - I have tried a few times, but this is the way it has to be.

---

### Post by TheFu on 2016-09-30
Have you tried using ssh X-forwarding? That works here. I don't run calibre over the WAN, so don't have x2go setup on that box.

Yep - ```
ssh -X c-server calibre &

```is working here.  Calibre is in the PATH on the remote box.
Run it from a terminal and use "code tags" to post any errors if it doesn't work.

---

### Post by jethro-uk on 2016-10-03
> **TheFu said:**
> Have you tried using ssh X-forwarding? That works here. I don't run calibre over the WAN, so don't have x2go setup on that box.Yep - ```
ssh -X c-server calibre &
```is working here.  Calibre is in the PATH on the remote box.Run it from a terminal and use "code tags" to post any errors if it doesn't work.Thanks for he hint - bear in mind I'm not au fair with X ...So I open up an ssh terminal session and type```
ssh -X c-server calibre &
``` ? But what do I run on my remote (Windows) box to view the output ?

---

### Post by TheFu on 2016-10-03
Using **ssh -X** requires an X-server. Windows doesn't have an X-server. 
Some background: [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)  that might be helpful. 

There are lots of options, but **x2go** is actually the best solution if you have to use Windows. Do you have the complete font packages install?  Just guessing here. No idea if that is it or not (probably not). Would get more eyes if the #0 post  used code tags (could edit it). Too hard to read as it is now.  Which DE are you running?  I use openbox, no DE.

Never heard "au fair" and google didn't explain it to me.

I use x2go (from Linux and Windows clients) to connect to a Linux desktop.  Then use that Linux desktop to connect into other systems, like my calibre server (it does plex, kodi, NFS, and a few other things too).  It is running 14.04 server. Version of calibre is, let me check, v1.25.

---

### Post by jethro-uk on 2016-10-03
> **TheFu said:**
> Using **ssh -X** requires an X-server. Windows doesn't have an X-server. Some background: [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)  that might be helpful. There are lots of options, but **x2go** is actually the best solution if you have to use Windows. Do you have the complete font packages install?  Just guessing here. No idea if that is it or not (probably not). Would get more eyes if the #0 post  used code tags (could edit it). Too hard to read as it is now.  Which DE are you running?  I use openbox, no DE.Never heard "au fair" and google didn't explain it to me.I use x2go (from Linux and Windows clients) to connect to a Linux desktop.  Then use that Linux desktop to connect into other systems, like my calibre server (it does plex, kodi, NFS, and a few other things too).  It is running 14.04 server. Version of calibre is, let me check, v1.25.Sorry "au fait" means "familiar with" if you're a poncy UK speaker like me :) I'm quite used to Linux (having cut my teeth on Unix on a PDP-11 in the 80s). But I'm not really familiar with X beyond the fact it's a GUI package of some sorts.The thing is Calibre WORKED when I ran it using X2Go to connect into my Debian box. It has worked for 6 years. Then something has happened behind my back to cause this error.Just for context, I am typing this into an X2Go session on my server which I connect to from Windows 7.I did try to format the first post, but having joined Ubuntu Forums in 2008, I find the revamp a bit ****, to be honest. I did have a hell of a posting history - including some unique work on PolicyKit (I know it was unique because a couple of people mailed me to say thanks).Anyway, I'll have to dig further :( Many thanks for taking the time to reply - best wishes !

---

### Post by TheFu on 2016-10-03
Another option, if you have sufficient bandwidth, is to load up virtualbox on Win7 and load a tiny Linux distro with an X/Server, then use the **ssh -X** method.  Which is heavier x2go or running a tiny VM?  Hard to say.  Just a thought. Might not be useful.

BTW, I do run x2go on Win7 myself. There is some odd artifacts from time to time and I haven't patched my Win7 machine since Feb (when MSFT really became nasty with their tracking demands).  It doesn't get used on the internet. No browser. No email. Basically, it is used for about 3 things daily and nothing else. I'm just waiting for those 3 things to be possible under Linux to be able to flush Windows completely.
[B]
Could the issue be that calibre is running on a 16.04.1 system with a newer, incompatible X-client?[/B]  Which version of Ubuntu are you using?  I get the xfce, but which release?

I don't know anything about PolicyKit. Never needed to know what it does.  That's a good thing. 
Wish systemd were like that.

---

### Post by jethro-uk on 2016-10-03
Or install Calibre on Windows and dump Debian ?[br]As I have previously said, I have changed nothing on purpose. If an update has borked things, it's possible. Because I don't run Calibre every day, it's hard to pinpoint it.My X2Go client is as up to date as possible - v4.0.5.2 (Qt 4.8.6). From Synaptic, xfce4 is 4.8.0.3 - as up to date as Wheezy wants. All the Qt4 modules in Synaptic appear to be 4.4.8.2+dfsg-11 (whatever that means).```
failed to get the current screen resourcesThe X11 connection broke: I/O error (code 1)XIO:  fatal IO error 0 (Success) on X server ":50.0"      after 368 requests (368 known processed) with 0 events remaining.You have new mail in /var/mail/jason
```p.s. HTF can I get this ****** forum to accept line breaks ??????????

---

### Post by TheFu on 2016-10-03
I use code tags and select/paste using the x-buffer all the time. Works.

I don't have xfce here. select/paste:
```
$ dpkg -l|grep qtcore
ii  libqtcore4:amd64                      4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1       amd64        Qt 4 core module
ii  qtcore4-l10n                          4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1       all          Qt 4 core module translations

```
Paste worked perfectly.  I use xterms, not gnome-terminal or any of the other "terminals." Don't remember any issues doing this in x2go sessions either.  Are you using Windows to post content from Unix here?  I haven't used Windows that way in a very long time, but if you select/paste from putty, I bet it will work.

---

### Post by howefield on 2016-10-03
Moved to the "*Debian*" forum.

---

### Post by QLee on 2016-10-03
> **jethro-uk said:**
> ...You have new mail in /var/mail/jason
Does the referred to mail just repeat the already shown info for the error or is there anything else included that might help you troubleshoot?
> **jethro-uk said:**
> p.s. HTF can I get this ****** forum to accept line breaks ??????????
To me this statement indicates frustration. Not surprising if you have been working on this problem for 4 days or more but I know how difficult frustration makes effective troubleshooting.

I enter line breaks with the carriage return key (I'm old school, so I mean enter key), does it work any differently for you if you choose "advanced reply".

Something that confuses me is why you are asking on Ubuntu Forums. Your question seems to be about accessing a Debian box from a Windows box. You might find more people to give answers on a Debian forum. If you choose to go that route, give information like a link to what you found with "Dr. Google", someone trying to help you might like to review what you found. Tell if you are using a standard Wheezy or a Wheezy with backports available or anything non-standard for a Wheezy install?

That's all I can offer, good luck.

---

### Post by jethro-uk on 2016-10-04
> **QLee said:**
> Does the referred to mail just repeat the already shown info for the error or is there anything else included that might help you troubleshoot?To me this statement indicates frustration. Not surprising if you have been working on this problem for 4 days or more but I know how difficult frustration makes effective troubleshooting.I enter line breaks with the carriage return key (I'm old school, so I mean enter key), does it work any differently for you if you choose "advanced reply".Something that confuses me is why you are asking on Ubuntu Forums. Your question seems to be about accessing a Debian box from a Windows box. You might find more people to give answers on a Debian forum. If you choose to go that route, give information like a link to what you found with "Dr. Google", someone trying to help you might like to review what you found. Tell if you are using a standard Wheezy or a Wheezy with backports available or anything non-standard for a Wheezy install?That's all I can offer, good luck.The message about mail can be ignored. I've had that since I set the box up.I have also posted on Debian forums, and had no replies.This is a standard Debian install - I haven't backported anything.Googling the  error messages doesn't seem to reveal a theme - certainly no "Aha !"I've been using the "Enter£" key too :) -the text looks OK in the edit box, but as soon as the forum gets a hold of it, it ruins it - *and* the previous posters text ?!?Anyway, it's looking like the better bet is to switch to Windows for Calibre.Funny, I dumped Ubuntu in 2011 because I had an error no one could fix either (I still get notifications from the thread to this day).

---

### Post by jethro-uk on 2016-10-04
p.s. I created a new user, and logged in as that and still got the error running calibre.

---

