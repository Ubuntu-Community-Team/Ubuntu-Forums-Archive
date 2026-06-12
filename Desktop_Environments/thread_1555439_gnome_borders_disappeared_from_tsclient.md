---
title: "gnome borders disappeared from tsclient"
date: 2010-08-18
forum: Desktop Environments
---

### Post by lucastrike on 2010-08-18
I searched for an answer to this problem for two days now, and only after I asked in #ubuntu (which I almost never do because it's so busy that my question is instantly upscrolled) did I find out the simple and undocumented solution. So I'm posting this for posterity and anyone who might make the same dumb mistake I did. 

The problem I experienced was a disappearance of gnome borders from rdesktop through tsclient which had severe consequences on my ability to access remote computers. 

Example image: [http://i37.tinypic.com/2506kch.jpg](http://i37.tinypic.com/2506kch.jpg)

As you can see there are no gnome borders to that paint window (via rdp) and the problem persists even in different resolutions. When in full screen mode, it is impossible to ctrl+alt+enter (or alt+tab, alt+esc, etc., I tried everything) out of the rdp session, it just blinks and stays in the window. I had to start>logout>disconnect just to get back to ubuntu. The only solution that ubuntu-pros offer is to turn off compiz, which I do not have nor have had on my machine. The sticky in this subforum explains:

> Where did my window borders go? - cc7gir

This is a common mistake caused by disabling some plugins in CompizConfig Settings Manager. To fix, open the manager (System > Preferences > CompizConfig Settings Manager) and find the "Window Decorations" plugin. Check the box and you're all set.

Fortunately, the mention of window decoration reminded me of some recent setting I came across. A few minutes of serious brain-scouring led me to the tsclient performance tab with a big fat check on "Hide window manager's decorations." I checked it two days ago thinking it would remove weird glowy-ness or whatever from the remote OS, allowing for faster communication and less lag; unknowingly, it just removes gnome's border from the window and ruins your whole remote access experience. I just unchecked it and connected, boom problem fixed. 

I hope search engines index this mother so some inkling of the problem becomes searchable for others who check that stupid box. Other info: I'm on lucid LTS or something, and I don't know if you can hack me with the info in that screenshot but please don't because I have sensitive material in ~/.pswds like my SSN, bank PIN, DOB, and medical records. 

with love,

lucas

---

### Post by dan_8791 on 2011-03-18
I too thought that that option hid the Windows(TM) window manager decorations and would never have remembered clicking it if not for this post

You legend!

---

