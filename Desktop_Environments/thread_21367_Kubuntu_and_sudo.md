---
title: "Kubuntu and sudo"
date: 2005-03-21
forum: Desktop Environments
---

### Post by WimVriend on 2005-03-21
Hi,
When I go to the kde config-centre, and choose a part where I have to fill in my sudo password, then after a while kde is jumping back to the config-centre startscreen. Verry strange, and I dont know how to solve that. Is here somebody who can tell my what to do.
Thx
Wim

---

### Post by bored2k on 2005-03-21
[QUOTE=WimVriend]Hi,
When I go to the kde config-centre, and choose a part where I have to fill in my sudo password, then after a while kde is jumping back to the config-centre startscreen. Verry strange, and I dont know how to solve that. Is here somebody who can tell my what to do.
Thx
Wim[/QUOTE]
 Don't quite understand you, but :
You are running:

1. gksudo kcontrol
2. you input your password
3. goes back to the main screen without taking the password?

That it ?

---

### Post by WimVriend on 2005-03-22
[QUOTE=bored2k]Don't quite understand you, but :
You are running:

1. gksudo kcontrol
2. you input your password
3. goes back to the main screen without taking the password?

That it ?[/QUOTE]

Yes that is exactly what is happening.
I have already installed Kubuntu for the second time, but after a while the same problem is coming back. 
Wim

---

### Post by knappen on 2005-03-22
Yes, that happens to me as well. Tried to setup my wireless network but nothing happened when I entered the password. It just did nothing.

You can type anything as your password and it does not complain about that the password is wrong.

---

### Post by apokryphos on 2005-03-22
You shouldn't be having to do gksdu kcontrol because, (i) there is kdesu, (ii) any parts required to be done as "root" already have an option inside kcontrol. So, that is, you should simply click on "Administrator Mode" (which comes up near the bottom of kcontrol, when doing root stuff; i.e. Login Manager). 

I just tried that now and it works fine.

Also note that you need to enter your own user password, despite it asking for your root password -- that's a known issue, and will be resolved in good time.

---

### Post by knappen on 2005-03-22
Thats what I did as well. Just clicked the Administrator mode but nothing happens.

---

### Post by WimVriend on 2005-03-22
[QUOTE=knappen]Thats what I did as well. Just clicked the Administrator mode but nothing happens.[/QUOTE]

Maybe I have solved the problem.
I was thinking it was my keyboard, so I switch the computer off, changed keyboard and reboot. The problem was still the same. Normally I use the dutch language, but I have it changed to english so that I better can explain what,s happening and what I do. But from that moment the problem was disapeared, now I have the language changed back to dutch and everything is still okay.
Hopefully....................
Wim

---

### Post by knappen on 2005-03-23
I am running kubuntu on a laptop so it could be a problem though :-)

---

### Post by scarecrow on 2005-03-23
[QUOTE=knappen]I am running kubuntu on a laptop so it could be a problem though :-)[/QUOTE]
 More than that- "sudo something" asks for the password, but but "kdesu something" does not! It feels like the WindowsXP "security", right?
Of course this can be changed, but should NOT be the default status of Kubuntu.

---

### Post by knappen on 2005-03-24
[QUOTE=WimVriend]Maybe I have solved the problem.
I was thinking it was my keyboard, so I switch the computer off, changed keyboard and reboot. The problem was still the same. Normally I use the dutch language, but I have it changed to english so that I better can explain what,s happening and what I do. But from that moment the problem was disapeared, now I have the language changed back to dutch and everything is still okay.
Hopefully....................
Wim[/QUOTE]


That actually worked for me as well so there must be a bug in there some where.

---

### Post by misterlizard on 2005-03-27
I've been having a similar problem in the KDE control centre. When I'm asked for the root password after trying administrator mode and type it in, I get told it's incorrect. When I type in my user password it just takes me to the information screen and I still can't change anything.

A workaround was to copy the command line to a Konsole and prefix it with 'sudo', e.g.

sudo kcmshell kdm

And after entering my user password, I can change things. Bit annoying, but seems to work.

---

### Post by rentz on 2005-04-03
I am having this same exact problem, i try to go into administratormode in the kde control center, it accepts password, and sends me to the default kde info screen everytime, nothing seems to fix it, very frustrating

---

### Post by misterlizard on 2005-04-04
I've noticed this problem's recently gone away since I updated all of the packages. There were quite a few KDE packages updated, though I've no idead  which one(s) fixed it though. Also logging in to KDE seems quicker.

---

### Post by wleftwich on 2005-04-15
I ran into the same thing, I coud not get into Administrator Mode in any of the Control Center apps; instead, after entering my password at the prompt, I just got the Welcome to Control Center page.

Reinstalling kcontrol fixed it for me:

sudo apt-get install --reinstall kcontrol

-- Wade Leftwich, Ithaca NY

---

### Post by mbuel76 on 2005-04-20
[QUOTE=wleftwich]I ran into the same thing, I coud not get into Administrator Mode in any of the Control Center apps; instead, after entering my password at the prompt, I just got the Welcome to Control Center page.

Reinstalling kcontrol fixed it for me:

sudo apt-get install --reinstall kcontrol

-- Wade Leftwich, Ithaca NY[/QUOTE]
 I'll have to try that, I'm having the same problem.

UPDATE:

a reinstall fixed the problem!  Kubuntu installing the package wrong during install?

---

### Post by Jofel on 2005-05-07
Weird, but re-installing kcontrol doesn't fix it for me. I will try to change my language and see if it works for me.

Edit:
This is funny. Putting my language at US English fixes this problem. I will leave my system at US English for now and hopefully the Dutch local for kcontrol will be fixed.

---

### Post by sprucio on 2005-05-08
Does anyone have a fix for this? I find this to be quite annoying as well. Perhaps this should be reported as a bug?

---

### Post by recover82 on 2005-05-08
I don't want to beat a dead horse. . but if it helps get a definite solution or a fix in the next release/update it's worth it.  

I'm having the same problem as listed above.  I'm trying to launch kynaptic and it wants me to run as root.  Well i know my freakin' root password because I started another KDE session as root and the password works there.  Very frustrating on a first install of Kubuntu...kinda leaves a sour taste but I'm sure it's only a minor hurdle.

---

### Post by engos on 2005-05-09
same problem :(

---

