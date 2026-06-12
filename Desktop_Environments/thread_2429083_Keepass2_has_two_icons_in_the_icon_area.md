---
title: "Keepass2 has two icons in the icon area"
date: 2019-10-13
forum: Desktop Environments
---

### Post by Paddy Landau on 2019-10-13
I don't know if I'm posting this in the right place.

Yesterday, I upgraded Lubuntu from 16.04 to 18.04. Keepass2 didn't work until I installed Mono.

Now, however, whenever Keepass2 starts, it creates two icons in the icon area (see screenshot). They both work identically and for the same instance.

I don't know how to fix that (there should be just the one icon), or even where to ask for help.

Can you advise me, please?

---

### Post by cruzer001 on 2019-10-14
Check /usr/share/applications for two instances of keepass2

---

### Post by Paddy Landau on 2019-10-15
> **cruzer001 said:**
> Check /usr/share/applications for two instances of keepass2
Thanks for the suggestion. There is only one instance there, named [FONT=lucida console]keepass2.desktop[/FONT].
I've also searched my home folder, and there is no [FONT=lucida console].desktop[/FONT] file for keepass.

---

### Post by cruzer001 on 2019-10-15
I cannot reproduce this in Gnome_18.04.

Maybe purge and reinstall.

Can't think of anything else.  Good luck

---

### Post by Paddy Landau on 2019-10-15
I am guessing that I should purge not only KeePass but also Mono. I tried to do this, but I wasn't sure that I managed everything.

I'll try this tomorrow, thank you for the suggestion.

---

### Post by #&amp;thj^% on 2019-10-15
Paddy have you tried with "**xprop WM_CLASS**" then clicking the second Icon  "**Keepass2**"
Add the class as the value of StartupWMClass in the .desktop file. For example, "**StartupWMClass=Keepass2**
Save the ".desktop file", close the application and re-open it. There should now only be 1 icon.

---

### Post by Paddy Landau on 2019-10-15
> **1fallen said:**
> Paddy have you tried with "**xprop WM_CLASS**" then clicking the second Icon  "**Keepass2**"
Add the class as the value of StartupWMClass in the .desktop file. For example, "**StartupWMClass=Keepass2**
Save the ".desktop file", close the application and re-open it. There should now only be 1 icon.
Thanks for your reply. Unfortunately, both icons return the same thing, which is the LX panel:
```
$ xprop WM_CLASSWM_CLASS(STRING) = "panel", "lxpanel"
```
So, that's a bust, unless you have another idea.

I have still to try purging and reinstalling, which I'll do tomorrow.

---

### Post by #&amp;thj^% on 2019-10-15
> **Paddy Landau said:**
> Thanks for your reply. Unfortunately, both icons return the same thing, which is the LX panel:
```
$ xprop WM_CLASSWM_CLASS(STRING) = "panel", "lxpanel"
```
So, that's a bust, unless you have another idea.

I have still to try purging and reinstalling, which I'll do tomorrow.

Whoops wrong input, "panel" try launching Keepass2 to find the correct App value.
EDIT: My return is:
```
xprop WM_CLASS
WM_CLASS(STRING) = "keepass2", "KeePass2"

```
Give that a Try.

---

### Post by Paddy Landau on 2019-10-15
Thanks, I get the same result as you.

I have added the line to the file keepass2.desktop. I tried once with keepass2 and once with KeePass2. Neither solved the problem.

So, I was wondering…

The app is started automatically through a script when I log in. I guess that this skips the .desktop file, doesn't it?

Anyway, in my tests, I started KeePass2 through the menu; using the command line; and opening the desktop file from Nautilus. Unfortunately, none of those solved the problem.

I don't know if I made it clear, but having two icons doesn't seem to affect the app in any way. It still works perfectly correctly. It's just odd to have two icons.

---

### Post by #&amp;thj^% on 2019-10-15
> **Paddy Landau said:**
> 
The app is started automatically through a script when I log in. I guess that this skips the .desktop file, doesn't it?


Is it script? Or just adding KeePass2 to the startup Apps.
If indeed it is script maybe have a look there. (This to me sounds like a race condition)
Is there a real need to have KeePass in the Tray?
> **Paddy Landau said:**
> 

I don't know if I made it clear, but having two icons doesn't seem to affect the app in any way. It still works perfectly correctly. It's just odd to have two icons.
Yep that was clear to me, and like you I'm not a fan of double Icons.
Nautilus is not something I can help with, Nemo, Caja Thunar, Double Commander, Dolphin and Ranger are the only File Manager's I'll use.

---

### Post by mc4man on 2019-10-16
what happens with this from cli,  1, 2 or no nothing?
```
mono-sgen /usr/lib/keepass2/KeePass.exe
```

---

### Post by Paddy Landau on 2019-10-17
> **1fallen said:**
> Is it script? Or just adding KeePass2 to the startup Apps.
A script. However, it also happens if I start it manually from the terminal.

I've had a close look at the script, and it doesn't start KeePass2 twice.
> **mc4man said:**
> what happens with this from cli,  1, 2 or no nothing?
```
mono-sgen /usr/lib/keepass2/KeePass.exe
```
Exactly the same — two icons.

I'm going to purge and reinstall now. I'll let you know what happens.

---

### Post by VMC on 2019-10-17
I use keepassx because it doesn't install mono and its a bit smaller install size. I only have one icon. I'll try keepass2 and see if it happens to me.

edit: installed keepass2 and I don't have those two icons on my panel. Only one, but I'm using eoan 19.10
edit2: I just saw where you have some script involved. I don't. Just the icon.

---

### Post by Paddy Landau on 2019-10-17
> **VMC said:**
> I use keepassx because it doesn't install mono and its a bit smaller install size.
KeePassX hasn't been updated since February 2016. Its version is still 2.0.2. That is a security problem. As nice as it would be to have a native app, we need up-to-date packages for security; KeePass2 was updated just last month, and its version is 2.43.
_______________________

This finally worked…

I purged both Mono and KeePass2; removed their repositories; re-added their repositories according to instructions (in case something was corrupted in the upgrade from 16.04 to 18.04); and reinstalled both Mono and KeePass2.

I now have just the one icon.

The upgrade from 16.04 to 18.04 had also messed up the font, but it's now fine. So, I suspect that Mono — or, rather, the installation of Mono — was the culprit.

Whew!

Thank you all for your help and advice. :)

---

### Post by howefield on 2019-10-17
> **Paddy Landau said:**
> KeePassX hasn't been updated since February 2016. Its version is still 2.0.2. 

Not an endorsement but just for info, [KeepassXC]("https://keepassxc.org/") is in the repositories, version 2.4.3.

---

### Post by Paddy Landau on 2019-10-17
> **howefield said:**
> Not an endorsement but just for info, [KeepassXC]("https://keepassxc.org/") is in the repositories, version 2.4.3.
Thank you. I'll have a good look!

**EDIT:** I like KeePassXC very much. Unfortunately, it lacks an important feature: a [Quick Unlock]("https://steveshank.com/cgi-bin/article.pl?aid=732"). This means that every time I have to use it, not just when I first open it, I have to fill in my full password. That's too much. I shall continue using KeePass2 until KeePassXC provides Quick Unlock.

---

