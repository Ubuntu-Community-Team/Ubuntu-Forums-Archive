---
title: "Can't log into Gmail with Firefox"
date: 2005-05-13
forum: Desktop Environments
---

### Post by klimas on 2005-05-13
It's pretty strange -- when I try to log into Gmail with Firefox (1.0.2-0ubuntu5.2), it gets to the page that says "Loading..." but never gets any further, even if I hit reload. I tried disabling all extensions but it didn't help. And Firefox seems fine otherwise. Anyone else run into this problem?

I found this message on Gmail's help:

[INDENT]There appears to be a problem using Gmail with versions of Firefox that weren't downloaded directly from Mozilla.[/INDENT]

---

### Post by Maestro23 on 2005-05-13
[QUOTE=klimas]It's pretty strange -- when I try to log into Gmail with Firefox (1.0.2-0ubuntu5.2), it gets to the page that says "Loading..." but never gets any further, even if I hit reload. I tried disabling all extensions but it didn't help. And Firefox seems fine otherwise. Anyone else run into this problem?

I found this message on Gmail's help:

[INDENT]There appears to be a problem using Gmail with versions of Firefox that weren't downloaded directly from Mozilla.[/INDENT][/QUOTE]


Just logged in fine to my Gmail account using Firefox 1.0.3 and Kubuntu 5.04  Might try updating your version of FireFox.

---

### Post by klimas on 2005-05-13
Even after I do an apt-get update, I'm still showing 1.0.2 as the latest release... which might be part of the problem. My sources.list is pretty uninteresting, but just in case:

```
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
```

---

### Post by Maestro23 on 2005-05-13
[QUOTE=klimas]Even after I do an apt-get update, I'm still showing 1.0.2 as the latest release... which might be part of the problem. My sources.list is pretty uninteresting, but just in case:

```
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
```[/QUOTE]


When I first set up my system, I followed the **ubuntu guide** and added the extras repositories to my **/etc/apt/sources.list.**  You can find it here, should do the trick:  [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by Declan on 2005-05-13
There must be something curious about gmail.  I can't get into it with Galeon, but I can with Firefox.

Interesting...

Good luck!

---

### Post by DutchLau on 2005-05-13
Isn't Gmail Java based?

Do you have the newest version of Java installed? I had the same problem before, but installing Sun's Java fixed the problem for me.

---

### Post by brickbat on 2005-05-13
This is a known problem with firefox and gmail.  Here is what I did and it worked:

In firefox, Edit/Preference/Privacy then clear History, Cache, and Cookies.

Restart firefox

Gmail to your hearts content.

Then setup Thunderbird with pop access  \\:D/ 

ciao
bb

---

### Post by bored2k on 2005-05-13
I've never seen this bug happen. I quit on using gmail firefox extension, kcheckgmail is much better :D

---

### Post by jeremy on 2005-05-13
I have the same firefox as you, and can log in fine, but it does sometimes take a while and appears to be doing nothing.

---

### Post by tread on 2005-05-13
It happens (partially) with opera too .. the auto complete addresses doesn't work unless the cache is emptied after you log out.

---

### Post by AndEat on 2005-05-14
](*,) I am having the same problem. Whenever I log onto gmail, I just get a blank page that  says 'done' at the bottom and does nothing. I'm updated on everything I can think of...firefox, ubuntu, java. Still I am getting nothing. This occurred after the most recent update of firefox (this week). I am considering rolling back to the previous version until whatever gets sorted out gets sorted out.

Any info on what I am doing wrong or I'm not doing would be appreciated.


thanks.

---

### Post by N'Jal on 2005-05-14
Do you have the don't ask for my password box checked? Coz checking that has caused me to have problem's in the past. On FF1.0 or 1.02 def not the latest version

---

### Post by schneiko on 2005-05-15
I remember having this problem a few weeks ago. I think it was one of my adblock (the plugin) rules that caused the problem. Try disabling anything that blocks things in web pages.

Sorry but I don't remember exactly what caused the problem - but I know could fix it very easily.

---

### Post by klimas on 2005-05-15
So I tried clearing my cache and history, but that didn't work. I tried the 1.0.3 version of Firefox and that didn't work, either. On a hunch I tried making an entirely new profile, and that fixed the problem. I'm guessing it was a problem with leftover settings or somesuch... I've had that profile since the early betas of Firefox, back when I was running another distro.

---

### Post by AndEat on 2005-05-20
ding ding ding  

we have a winner

I disabled Adblock for a bit, and had no problem logging.

-Thanks!

---

