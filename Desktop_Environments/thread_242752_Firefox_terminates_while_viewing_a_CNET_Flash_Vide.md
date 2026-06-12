---
title: "Firefox terminates while viewing a CNET Flash Video page"
date: 2006-08-24
forum: Desktop Environments
---

### Post by funchords on 2006-08-24
Site URL: [http://news.com.com/1606-2_3-6108950.html?part=rss&tag=6108950&subj=news]("http://news.com.com/1606-2_3-6108950.html?part=rss&tag=6108950&subj=news")

Firefox version: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.5) Gecko/20060731 Ubuntu/dapper-security Firefox/1.5.0.5

Of note: 

The CNET video player shows a 15 second commercial in the window, which seems to play fine as the second counter decreases.  When the second counter reaches zero, Firefox terminates without any errors on the screen, in /var/log/messages, or in dmesg.  

The behavior is the same in Safe Mode (firefox -safe-mode) which disables all plugins.

Visiting the page [www.macromedia.com](www.macromedia.com) as well as viewing another page with Flash content seems to work fine.

Please help:

1.  Does the page work for you?

2.  Do you know how to fix it? :)

---

### Post by paddy1978 on 2006-08-24
Hi,

Just tried it:

1. Crashed my Firefox too (running 1.5.0.5 on Kubuntu Dapper)! In Konqueror it crashed the first time but not the second time, strangely. In IE6 (running on linux with Wine) it seemed to work OK.

2. No idea how to fix it unfortunately! I'm guessing it's some problem with the linux plug-in, as IE played it ok....

---

### Post by funchords on 2006-08-24
Can anyone else confirm this behavior -- or provide input? 

Thanks

---

### Post by jimbob on 2006-08-24
I get the sound but not the video (same on Foxnews.com which used to work fine).

I ran into this recently on Foxnews.com and after searching for a while found that they had upgraded to Flashplayer 9 which doesn't have a Linux version yet although they have comitted to releasing one (someday).

I am fighting back by looking at Cnn for now.

EDIT: Cnet uses Flashplayer 8 so that's why they don't work either.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by StayPuft on 2006-08-24
When I try to view any flash at all Firefox terminates with no warning, error, or log message. I've tried installling flash through Automatix, synaptic, and directly from the macromedia website. 

Has anyone else encountered this? Does anyone have a solution or help? Thanks in advance.

---

### Post by funchords on 2006-08-24
Thanks Paddy & Jim.   Two is enough for me.  

StayPuft -- hope you find help with that issue.  I can see Flash, just not on that particular page (and, presumably, others like it).

---

### Post by fozner on 2006-08-28
I am using 32 bit mplayer, mplayer plug-in and 32 bit firefox, greasemonkey and the cnn friendly video script: [http://vlajbert.blogspot.com/](http://vlajbert.blogspot.com/)

All works fine.  I'm using Fedora Core 5_64 so I installed via yumex --forcei386 option.  Your distro will be different but the results should be identical. \\:D/

---

