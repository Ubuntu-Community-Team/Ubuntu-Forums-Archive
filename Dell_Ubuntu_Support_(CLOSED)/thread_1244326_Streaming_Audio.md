---
title: "Streaming Audio"
date: 2009-08-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cybermoose on 2009-08-19
I've recently upgraded my Inspiron 15n from Ubuntu 8.10 to 9.04.  All went fine & everything seems to work, except that I'm having some trouble streaming audio from radio stations. When I click on the station's link to "listen live now" I'm asked to search for a suitable plug-in (MMSH or MMS [Microsoft Media Server] protocol source). Each time I do so I get an error stating "no packages with the requested plugins found."

So, I'm a little confused.  What do I need to do in order to be able to stream live audio from radio stations?

Thanks in advance for any & all help.

---

### Post by sarath_it on 2009-08-19
Try VLC. It should work. 

If you want to run from mplayer, you might need to install gstreamer0.10-plugins-bad

[http://appnr.com/package/gstreamer0.10-plugins-bad](http://appnr.com/package/gstreamer0.10-plugins-bad)

---

### Post by cybermoose on 2009-08-19
[SIZE=2]That did the job...thanks very much![/SIZE]

---

### Post by decopeland on 2009-08-26
VLC works but I get a message "Waiting for video" when listening to audio stream.  I suppose that is better than nothing.

---

### Post by sarath_it on 2009-08-26
VLC gives you more info than that, go to Tools > Messages, and set verbosity level 2 and stop-play again. it will detail everything it does

---

