---
title: "Firefox crashes constantly on 8.10"
date: 2009-03-31
forum: General Help
---

### Post by Andos on 2009-03-31
I have a frustrating problem since upgrading to Ubuntu 8.10 a few months ago.  I get frequent crashes with Firefox 3 which never happened on 8.04 or below.  There are two kinds of crash which occur.

1) The screen goes grey and Firefox stops responding.  Sometimes it recovers, sometimes I have to use System monitor to kill it and restart it.  CPU usage is normally 50% ( I have a dual core laptop)

2) the screen goes grey and the entire system stops responding. The process monitor won't even load, all I can do is hold down Ctrl-Alt-Backspace for 20-30 seconds until X restarts.

This normally happens while on websites using Flash, though not always.  I've tried reinstalling firefox and flash but it hasn't fixed it.  Can anyone suggest what I need to look into?  Thanks for any help!

---

### Post by Andos on 2009-04-06
I have found a site (link below) which causes this to happen every time I open it in firefox 3.08 on Ubuntu.  I can open it in Firefox 3.08 in Windows with no problem.  I'd really appreciate any help as I'm getting really frustrated and have no idea what else to try!

[https://store.canon-europe.com/servlet/SecureControllerServlet?Action=DisplayPage&Locale=en_GB&id=HomePage&SiteID=canoncon](https://store.canon-europe.com/servlet/SecureControllerServlet?Action=DisplayPage&Locale=en_GB&id=HomePage&SiteID=canoncon)

---

### Post by TheLions on 2009-04-06
site is working with me....

I'm using 
Ubuntu 8.10 x64
Firefox3.6apre1
Shockwave Flash 10.0 r22

try install newest flash if you ain't already, also check if alpha version is working...

flash:[http://labs.adobe.com/downloads/](http://labs.adobe.com/downloads/)
Firefox(Minefield):[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/)
(just unpack it and run script named firefox)

---

### Post by Yashiro on 2009-04-06
So un-install all Flash related software and test out your theory.

---

### Post by Andos on 2009-04-06
Thanks for the replies.  I tried removing flash, and then running the latest alpha of firefox but this didn't resolve the problem.  I also tried 3.08 in safe mode with all extensions disabled and that didn't fix it either.  I'm really stuck now!

---

### Post by LowSky on 2009-04-06
What plugins are you using..

Try deleting your profile from your /home folder it will reset firefox (also deletes your bookmarks so back those up before deleting the profile
 the file is in  /home/*username*/.mozilla

---

### Post by Andos on 2009-04-06
Tried removing the profile, that hasn't worked either!  normally I use Ad block plus, stumbleupon, greasemonkey, downthemall and foxmarks

---

### Post by Andos on 2009-04-06
Well, I've now tried Epiphany and Opera and the same thing happened so that rules out Firefox!  Must be some kind of OS issue, maybe I'll try a clean install when I have time :(

---

### Post by TheLions on 2009-04-06
try temporally removing java...

---

### Post by Andos on 2009-04-06
Removed the Sun JRE and disabled javascript in about:config - still no joy, the site example I gave still makes the browser freeze!

---

### Post by blazingnikons on 2009-04-06
I, too, have repeartedly encountered this problem. At first, flash proved a huge headache.  Then, java and flash were messy, but differently than before. Now, after an update a week or so ago, Firefox locks up and crashes as described above. It seems as though amd64 Intrepid and Firefox just won't ever work well with each other...

---

