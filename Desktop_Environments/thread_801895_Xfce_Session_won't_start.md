---
title: "Xfce Session won't start"
date: 2008-05-21
forum: Desktop Environments
---

### Post by dbbolton on 2008-05-21
I installed Xfce by installing the 'xfce4' package on Ubuntu 8.04. When I choose the Xfce session from GDM and login, I just get a blank screen with the mouse pointer. I can't right click or anything. I just have to press ctrl+alt+backspace to get back to GDM. However, sometimes the session seems to load normally. Does anyone know what could be causing this?

Here is my /usr/share/xsessions/xfce4.desktop file:

```

[Desktop Entry]
Encoding=UTF-8
# The names/descriptions should really be better
Name=Xfce Session
Name[fr]=Session Xfce
Name[et]=Xfce 4 sessioon
Name[fi]=Xfce 4 -istunto
Name[he]=Xfce 4
Name[ko]=Xfce 4 &#49464;&#49496;
Name[nl]=Xfce 4 Sessie
Name[ru]=&#1057;&#1077;&#1072;&#1085;&#1089; Xfce 4
Name[zh_TW]=Xfce 4 &#24037;&#20316;&#38542;&#27573;
Comment=Use this session to run Xfce as your desktop environment
Comment[et]=kasuta seda sessiooni, et Xfce käivituks sinu töökeskkonnana
Comment[fi]=Valitse tämä istunto käyttääksesi Xfce:tä työpöytäympäristönäsi
Comment[fr]=Sélectionner cette session pour utiliser Xfce comme environnment graphique
Comment[he]=&#1492;&#1513;&#1514;&#1502;&#1513; &#1489;&#1494;&#1492; &#1499;&#1491;&#1497; &#1500;&#1492;&#1508;&#1506;&#1497;&#1500; &#1488;&#1514; Xfce &#1499;&#1513;&#1493;&#1500;&#1495;&#1503; &#1492;&#1506;&#1493;&#1489;&#1491;&#1492; &#1513;&#1500;&#1498;
Comment[ko]=&#49324;&#50857;&#51088; &#45936;&#49828;&#53356;&#53457; &#54872;&#44221;&#51004;&#47196; Xfce&#47484; &#51060;&#50857;&#54633;&#45768;&#45796;.
Comment[nl]=Deze optie start de Xfce 4 Desktop Environment
Comment[ru]=&#1047;&#1072;&#1087;&#1091;&#1089;&#1082;&#1072;&#1077;&#1090; &#1088;&#1072;&#1073;&#1086;&#1095;&#1091;&#1102; &#1089;&#1088;&#1077;&#1076;&#1091; Xfce 
Comment[zh_TW]=&#20351;&#29992;&#36889;&#20491;&#24037;&#20316;&#38542;&#27573;&#36617;&#20837; Xfce 4 &#20316;&#28858;&#24744;&#30340;&#26700;&#38754;&#29872;&#22659;
Exec=startxfce4
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=xfce-utils

```

---

### Post by HunterSBuntu on 2008-05-21
I'm having the same problem.  

I don't have solution to offer unfortuntaly.

There are a few threads with people having this problem but no one has posted any explanation of what could be causing it yet as far as I can see.

---

### Post by geoff123 on 2008-05-21
I noticed the same thing and it only happens occasionally.  When it does, I an Ctrl-alt-backspace and then try again which usually works on the second try.

---

### Post by dbbolton on 2008-05-21
Perhaps a bug report should be filed, although I suspect that this problem has to do with the Hardy packages and not Xfce itself.

---

### Post by ninjabob7 on 2008-05-22
Same problem. I installed xubuntu-desktop, and it worked fine for a while. Now it only works occasionally. I get a blank "XFCE blue" screen with the mouse pointer.
In my case, I can still run XFCE by choosing the Failsafe Terminal session and running xfce4-session, but it's getting very annoying. I don't even know where to start diagnosing.

---

### Post by raskolnikov_kr on 2008-05-23
> **geoff123 said:**
> I noticed the same thing and it only happens occasionally.  When it does, I an Ctrl-alt-backspace and then try again which usually works on the second try.

I same problerom too.
I use Ctrl-Alt-Backspace and try again twice, then i in xfce4.
what can i do?
i think how reinstall gdm.
somebody tell me 
how to reinstall gdm.
or how to kill gdm, then use xdm or slim.

---

### Post by geoff123 on 2008-05-24
Looks like this has already been reported as a bug..
[https://bugs.launchpad.net/ubuntu/+bug/221657](https://bugs.launchpad.net/ubuntu/+bug/221657)

---

### Post by yaztromo on 2008-05-29
I just installed xubuntu-desktop and it did work a few times. Now I'm having the same problem and occaisonally gnome does it too.

---

### Post by yaztromo on 2008-05-29
Actually, just been thinking. Would just doing a fresh install of xubuntu get round the problem. Sounds like you guys all installed xubuntu after you install ubuntu?

---

### Post by dbbolton on 2008-05-29
> **yaztromo said:**
> Actually, just been thinking. Would just doing a fresh install of xubuntu get round the problem. Sounds like you guys all installed xubuntu after you install ubuntu?
I didn't install xubuntu or the 'xubuntu-desktop' package. I installed the 'xfce4' package, and I have tried purging it, then reinstalling it, to no avail.

---

### Post by ninjabob7 on 2008-06-02
> **yaztromo said:**
> Actually, just been thinking. Would just doing a fresh install of xubuntu get round the problem. Sounds like you guys all installed xubuntu after you install ubuntu?

For me, this wouldn't work. This computer has 3 users, and I'm the only one that uses XFCE. Yes, I guess I could install Xubuntu and then ubuntu-desktop over that, but that's a lot of work.

Is anyone else using the NVIDIA proprietary driver? I'm wondering if this might be related to that. I also noticed recently that glx isn't working anymore, but it has the same problem without XFCE running.

It seems like it works from a cold start but not otherwise, but I haven't tested that yet.

---

### Post by yaztromo on 2008-06-03
> **ninjabob7 said:**
> For me, this wouldn't work. This computer has 3 users, and I'm the only one that uses XFCE. Yes, I guess I could install Xubuntu and then ubuntu-desktop over that, but that's a lot of work.

Is anyone else using the NVIDIA proprietary driver? I'm wondering if this might be related to that. I also noticed recently that glx isn't working anymore, but it has the same problem without XFCE running.

It seems like it works from a cold start but not otherwise, but I haven't tested that yet.

I'm using the Intel graphics driver so I don't think it's driver related. Also it isn't reproducible every time since another machine I have has installed the xubuntu-desktop package and it works okay.

When I get chance I will reinstall the affected machine afresh and see if that helps. Would really like to stop using Gnome.

---

### Post by ninjabob7 on 2008-06-14
Found a workaround! In /usr/share/xsessions/xfce4.desktop, change
```
Exec=startxfce4
```
to
```
Exec=xfce4-session
```
This means the bug is either in startxfce4 or the default settings (the config file does not exist on my system.)

---

### Post by Michael%S on 2008-06-15
Thank you! I was starting to think of a clean install and was just about to open a thread of my own when I saw this. Works like a charm, so far. :D

---

### Post by ninjabob7 on 2008-06-25
We could still use a real solution for this. With my workaround, the wallpaper sometimes does not come up. This isn't too big of a deal for me, since I don't have any desktop icons, but seems to indicate that there is a difference between startxfce4 and xfce4-session which may be important.

---

### Post by xerodeth on 2008-10-01
so not sure if anyone still needs help with this... but this is what works for me.  in your home dir there should be a folder called .cache, go into that folder and delete the sessions folder and the xfce4.  i removed both these folders and the desktop came back as well as wallpaper.

---

### Post by tuvw962 on 2008-10-02
[wow gold](http://www.mmoinn.com)The local District Judge had given the defendant a lecture on the evils of drink. But in view of the fact that this was the first time the man had been drunk and incapable, the case was dismissed on payment of ten shillings costs."Now don't let me ever see your face again," said the Justice sternly as the defendant turned to go. "I'm afraid I can't promise that, sir," said the released man. "And why not?""Because I'm the barman at your regular pub!" [world of warcraft gold](http://www.mmoinn.com/) [warhammer gold](http://www.gold-warhammer.com/) [wow power leveling](http://www.mmoinn.com/mmoinn_pl/)[http://www.mmoinn.com](http://www.mmoinn.com/)

---

### Post by wag2639 on 2009-10-04
> **xerodeth said:**
> so not sure if anyone still needs help with this... but this is what works for me.  in your home dir there should be a folder called .cache, go into that folder and delete the sessions folder and the xfce4.  i removed both these folders and the desktop came back as well as wallpaper.

Thanks this worked.

---

### Post by micmath on 2009-10-05
> **xerodeth said:**
> so not sure if anyone still needs help with this... but this is what works for me.  in your home dir there should be a folder called .cache, go into that folder and delete the sessions folder and the xfce4.  i removed both these folders and the desktop came back as well as wallpaper.

I can confirm that this does fix the problem for me too. Many thanks!

---

