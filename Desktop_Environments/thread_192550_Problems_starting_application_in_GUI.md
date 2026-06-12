---
title: "Problems starting application in GUI"
date: 2006-06-08
forum: Desktop Environments
---

### Post by steverippl on 2006-06-08
Hi,

Recently setup a 5.10 installation to act as a mail proxy/spam filter using assp & sendmail. It's on a fairly standard, older P4, everthing was working fine after the initial install.  Needless to say there's been lots of tinkering with various configurations to get sendmail working, which it does now. We also set up VNC as it's on a predominantly windows network (not my choice :wink: ). Now I don't know if we're overloading things, but now the Gnome desktop is becoming really unresponsive. I can try to open apps (*any* apps) and the wheel spins, stops, and nothing has happened. I logout of the session and go back in and it's a bit better, but still not everything comes up straight away (or at all). I can still get to tty1 and do things on the command line. I have to say I had noticed similar behaviour on my 5.10 kubuntu box at home, but never as bad and I'd always assumed kubuntu 5.10 was just a bit buggy. But I need the ubuntu box at work to stand up! Any thoughts?

---

### Post by steverippl on 2006-06-10
Well, I don't know exactly what's causing it, but it seems to have something to do with the network settings!! It seems as though if the dns is not correctly configured when ubuntu boots up and tries to configure the network the os can seemingly grinds to a bit of a halt. Gnome is coming up ok, but as I said, is being very unresponsive. Once we changed the dns correctly suddenly the os was happy and functioning better. Why does the os freak out if the dns is incorrect, like I can't get the terminal up in the gui or 'run as' just spins its wheels and does nothing? All this went away once we changed the dns. I think the similar issue I have with kubuntu at home may also be dns relate, because the dsl modem my isp gave me seems designed for windows and has a hard time seeing linux. I can browse ok on the kubuntu box but I can't bring up the netwotk connections box in the gui (so I edit the config files manually). Is this known behaviour? I know we're onto the next release now but I'm only just figuring this out now! Does 6.06 behave better?

---

