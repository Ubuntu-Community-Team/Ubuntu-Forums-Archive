---
title: "epiphany cookie handling"
date: 2005-11-13
forum: Desktop Environments
---

### Post by arnieboy on 2005-11-13
I find epiphany a lot faster than firefox and all the mozilla plugins work on it as well. but the only issue I have with it is its rather rudimentary cookie handling.
there are only 3 options:
a) accept all cookies
b) accept cookies from  sites u visit
c) reject all cookies
Generally most modern browsers have a lot more advanced cookie handling than this in which u can select which sites u want to accept cookies from and to accept or to reject third party cookies and lots of other options.
I used the 2nd option in epiphany and soon found junk cookies from zedo.com and advertising.net (both are renowned for spy cookies). I wonder if therez is an external cookie handling extension for epiphany which overrides this rather crude   feature.

---

### Post by SickTwist on 2005-11-13
I may be mistaken but I *think* I remember reading that Epiphany cookies are only stored for the session. So even if it saves every cookie, they are all deleted when the program is closed. If that is the case then storing them does little harm.

Could anyone verify that this is correct?

---

### Post by aysiu on 2005-11-13
Well, whether they are harmful or not is irrelevant. For some users, it's more of a privacy/clutter issue. I like to add certain sites (like Boston.com) to my blocked cookies list even if I'm visiting the site because it allows me to visit several pages without subscribing to the site. Firefox lets you create whitelists, blacklists, and choose how long you want to keep cookies or whether you should be asked every time.

---

### Post by arnieboy on 2005-11-13
[QUOTE=SickTwist]I may be mistaken but I *think* I remember reading that Epiphany cookies are only stored for the session. So even if it saves every cookie, they are all deleted when the program is closed. If that is the case then storing them does little harm.

Could anyone verify that this is correct?[/QUOTE]
yeah u are mistaken. epiphany has no concept of session cookies. it just accepts all first and third party cookies from the site which u visit and keeps them till they decide to expire by themselves (thats for the second option on my first post). I decided against using  epiphany long back cuz of this same crudeness in design... after all these months, seemingly no progress has been made on this front.
I still dont understand why my firefox keeps crashing on flash sites. I have tried every possible way to make it work .. even epiphany uses the firefox plugins and works flawlessly on flash sites. this problem with firefox only exists on my breezy installation. it works without a glitch on hoary. thats the only reason why i decided to try out epiphany but now am back on firefox cuz of this cookie issue.

---

### Post by arnieboy on 2005-11-13
[QUOTE=aysiu]Well, whether they are harmful or not is irrelevant. For some users, it's more of a privacy/clutter issue. I like to add certain sites (like Boston.com) to my blocked cookies list even if I'm visiting the site because it allows me to visit several pages without subscribing to the site. Firefox lets you create whitelists, blacklists, and choose how long you want to keep cookies or whether you should be asked every time.[/QUOTE]
Precisely the point I was trying to make aysiu.. I fail to realize why the makers of epiphany ignored this rather crucial feature.

---

### Post by aysiu on 2005-11-13
[QUOTE=arnieboy]
I still dont understand why my firefox keeps crashing on flash sites. I have tried every possible way to make it work .. even epiphany uses the firefox plugins and works flawlessly on flash sites. this problem with firefox only exists on my breezy installation. it works without a glitch on hoary. thats the only reason why i decided to try out epiphany but now am back on firefox cuz of this cookie issue.[/QUOTE] Are you using 1.5 from Mozilla or the 1.0.7 from Ubuntu? I tried using 1.5 and symlinking my plugins folder to /usr/lib/mozilla-firefox/plugins (plugins didn't work) and /usr/lib/mozilla/plugins (Firefox crashed on Flash sites). So, I'm back on 1.0.7.

---

### Post by arnieboy on 2005-11-13
[QUOTE=aysiu]Are you using 1.5 from Mozilla or the 1.0.7 from Ubuntu? I tried using 1.5 and symlinking my plugins folder to /usr/lib/mozilla-firefox/plugins (plugins didn't work) and /usr/lib/mozilla/plugins (Firefox crashed on Flash sites). So, I'm back on 1.0.7.[/QUOTE]
I am using 1.0.7 aysiu. most plugins will not work if u make symlinks. java and flash will work (in fact for java u need to make a symlink, a copy of the file wont work). however for mplayer, acroread etc, u need to make copies to your plugins folder.
however in my case for some strange reason which beats me completely, flash refuses to work on firefox 1.0.7
try out [www.flashfunpages.com](www.flashfunpages.com) for example.
is that working for u?

---

### Post by Hairy_Palms on 2005-11-13
hmmm i tried that site, it works for me, how did you install flash, was it from the repos or was it using firefox inbuilt plugin installer? i installed flash through firefox, and it works fine with no crashes but when i used the repo one it crashed every now and again,

---

### Post by aysiu on 2005-11-13
[QUOTE=arnieboy]
try out [www.flashfunpages.com](www.flashfunpages.com) for example.
is that working for u?[/QUOTE] Yes, it appears to be.

---

### Post by aysiu on 2005-11-13
[QUOTE=Hairy_Palms]i installed flash through firefox, and it works fine with no crashes but when i used the repo one it crashed every now and again,[/QUOTE] That's funny--I installed it through the repositories (flashplugin-nonfree).

---

### Post by arnieboy on 2005-11-13
[QUOTE=aysiu]Yes, it appears to be.[/QUOTE]
yeah the page is opening for me as well.. but whats happening when u are clicking on any of the links on the top? (like humor, love, christian) etc? are u getting sound and movie both?

---

### Post by aysiu on 2005-11-13
[QUOTE=arnieboy]yeah the page is opening for me as well.. but whats happening when u are clicking on any of the links on the top? (like humor, love, christian) etc? are u getting sound and movie both?[/QUOTE] Yeah. I know that doesn't help you, but it's working for me.

---

### Post by arnieboy on 2005-11-13
[QUOTE=aysiu]Yeah. I know that doesn't help you, but it's working for me.[/QUOTE]
alright after hours of research and head banging, herez how I solved the firefox flash problem:
```
sudo gedit /etc/mozilla-firefox/mozilla-firefoxrc

```and **change**
[PHP]FIREFOX_DSP="auto"[/PHP]
to
[PHP]FIREFOX_DSP="arts"[/PHP]
Even if u find an empty file or dont find any **FIREFOX_DSP="auto" **just type 
[PHP]FIREFOX_DSP="arts"[/PHP]
and save and exit.
now close all firefox windows and restart firefox and check any flash site.

EDIT: This also works with firefox 1.5RC2

---

