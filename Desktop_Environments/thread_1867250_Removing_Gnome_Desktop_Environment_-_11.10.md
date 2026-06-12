---
title: "Removing Gnome Desktop Environment - 11.10"
date: 2011-10-22
forum: Desktop Environments
---

### Post by linux.girl on 2011-10-22
Hi everyone,

I installed Gnome Desktop Environment with Extra Components via Ubuntu sw center. It is causing me problems, so I want to remove it. I went to sw center again, removed, restarted...but it is still there.

Any idea how I can uninstall it? 

Thanks,

linux.girl

---

### Post by crdlb on 2011-10-22
In what way is it causing problems? Most of GNOME is already installed since it is used by Unity.

---

### Post by linux.girl on 2011-10-22
well, first, it changed the grub background to debian (instead of the purple ubuntu grub, i get a debian one, with a sky and debian logo, etc). it also changed the login in screen - it sounds silly, but I prefered both items the way it was before i installed the gnome desktop environment (which i later uninstalled, but it was of no help, the grub and login are still in this new way).

also, after I rebooted, it gave me some kind of message saying something about options M and S (dont remember what it was), but it repeated itself a few times, quite annoying.

thanks in advance for your help!

linux.girl

---

### Post by linux.girl on 2011-10-22
uh, I just noticed it also blocked my screen saver from working :-(

can anyone help undo the effects of installing the gnome desktop environment? or do i have to completely re-install ubuntu?

thanks again in advance !

---

### Post by Thelinuxgeek on 2011-10-22
Hmmm that's odd. I would just re-install Ubuntu. And why did you install Gnome through the software center? It comes by default with Ubuntu, along with Unity.

---

### Post by stinkeye on 2011-10-22
What was the exact package you installed?

What does this give you when entered in the terminal
```
echo $DESKTOP_SESSION
```

---

### Post by clappboard on 2011-10-22
Can you try running 
```
unity --reset
```
in the terminal?  It's a long shot, but it might be that GNOME screwed with some of the shared settings...  I installed it fine though o.O

> Hmmm that's odd. I would just re-install Ubuntu. And why did you install Gnome through the software center? It comes by default with Ubuntu, along with Unity.

Correct me if I'm wrong, but 11.10 doesn't come with GNOME.  They dropped it after 11.04.  I think the double inclusion in that release was just a kind of transitional phase.

---

### Post by stinkeye on 2011-10-22
> Correct me if I'm wrong, but 11.10 doesn't come with GNOME. They dropped it after 11.04. I think the double inclusion in that release was just a kind of transitional phase.
Gnome is the desktop enviroment that gnome-shell,unity run on.
11.10 uses gnome3 which has dropped the old style panels(gnome2)

---

### Post by clappboard on 2011-10-22
> **stinkeye said:**
> Gnome is the desktop enviroment that gnome-shell,unity run on.
11.10 uses gnome3 which has dropped the old style panels(gnome2)

Okay, yeah.  What I meant by GNOME though was the desktop session; interface, etc.  Not the actual environment.  My mistake for not being clearer.  #-o

---

### Post by linux.girl on 2011-10-23
Hi everyone,

Answering all questions:

When I do: echo desktop session, I get "ubuntu" as result and that is because I am logged in as ubuntu, not as gnome classic, etc. 

The package that installed from software center is called "Gnome Desktop Environment with Extra Components". If you enter the word Gnome in the search box of the sw center, you will see that this is the first result. 

It is cool to have the option of getting different deskto types to log on to, but not at the expense of other stuff that went wrong, so I prefer to give it up. I am trying now unity --reset and it is giving me tons of warnings and errors so I am guessing I will really have to re-install ubuntu :-( (unless anyone has more ideas?)

thanks again,

linux.girl

---

### Post by linux.girl on 2011-10-25
So, I ended up re-installing ubuntu to solve the gnome classic annoyance. It is all good now, only strange thing is that grub doesn't appear before the system loads. I would like to make sure I see grub every time, is there a way to do that? (and btw, I tried to press the shift key just to see it loads at all, and it didnt).

Thanks in advance!

---

