---
title: "Cairo-Dock"
date: 2009-09-28
forum: Desktop Environments
---

### Post by GCkid7 on 2009-09-28
Yesterday I removed cairo-dock (it's bugged) from my system and I ticked for complete removal. 
After re-start all I got was a black screen with text and nothing worked. I don't know why I ticked for complete removal in "synaptick package manager", but I did not except for complete crash down. I did not know how to re-store it.

Is this normal in Ubuntu? should I avoid that particular command?
When should I use that command: "complete removal"?


I am still learning Ubuntu. Thanx to anyone who replies & answers my questions....

---

### Post by redwaldmcmanus on 2009-09-28
no that's not normal, I use complete removal a lot and have never had that.

What package did you remove?
What packages did it say would be removed? <- if you didn't look at this, then it's possible that you've taken out a few vital ones

---

### Post by fabounet on 2009-09-28
you probably removed libcairo ...
try reinstalling it
(and about you're Cairo-Dock problems, did you search [on the wiki]("http://www.cairo-dock.org/ww_page.php?p=Accueil&lang=en") ? Because it really works well.)

---

### Post by GCkid7 on 2009-09-28
> **redwaldmcmanus said:**
> no that's not normal, I use complete removal a lot and have never had that.

What package did you remove?
What packages did it say would be removed? <- if you didn't look at this, then it's possible that you've taken out a few vital ones

I think you are right, I did not know if you remove all of them it will affect the whole OS. Now I have to pay the prize & learn the bitter way.

---

### Post by GCkid7 on 2009-09-28
> **fabounet said:**
> you probably removed libcairo ...
try reinstalling it
(and about you're Cairo-Dock problems, did you search [on the wiki]("http://www.cairo-dock.org/ww_page.php?p=Accueil&lang=en") ? Because it really works well.)

I can't do anything. When I boot the PC, all I got is black screen & text. But I re-install the whole OS.

The problem for me is, I'm still new with Ubuntu & in Synaptic Package Manager does't say what will happened if you perform certain opperation....

---

### Post by Giblet5 on 2009-09-28
> **GCkid7 said:**
> I can't do anything. When I boot the PC, all I got is black screen & text. But I re-install the whole OS.

The problem for me is, I'm still new with Ubuntu & in Synaptic Package Manager does't say what will happened if you perform certain opperation....

Well, you *could* reinstall, but you probably don't *need* to.

You probably just need to reinstall libcairo:

```
Log in.
sudo apt-get install libcairo2 libcairo-perl python-cairo libcairomm-1.0.1 libpixman-1-0 libmono-cairo2.0-cil
sudo /etc/init.d/gdm restart
```

Linux is different from Windows and MacOS in that it doesn't try to second-guess what you intend to do. In other words, if you tell it to do something bad, it will do it because you said to. That can be good and it can be bad. I think it's mostly good.

If you can think of a way to prevent these kinds of issues without making the OS useless, I'll gladly help you implement it.

---

### Post by GCkid7 on 2009-09-28
> **Giblet5 said:**
> Well, you *could* reinstall, but you probably don't *need* to.

You probably just need to reinstall libcairo:

```
Log in.
sudo apt-get install libcairo2 libcairo-perl python-cairo libcairomm-1.0.1 libpixman-1-0 libmono-cairo2.0-cil
sudo /etc/init.d/gdm restart
```

Linux is different from Windows and MacOS in that it doesn't try to second-guess what you intend to do. In other words, if you tell it to do something bad, it will do it because you said to. That can be good and it can be bad. I think it's mostly good.

If you can think of a way to prevent these kinds of issues without making the OS useless, I'll gladly help you implement it.

Yes, you are right, I agree with you. The thing is, from day one I did evrything on my own, I learned the best lessons thru pain, error and trial, and that is killng me. It's not like with Windows where I learned evrything in school and thru short courses. I see potential in Ubuntu, I like the OS. I wish there would be some kind of centre for Linux study in my town like it is for Windows.

---

