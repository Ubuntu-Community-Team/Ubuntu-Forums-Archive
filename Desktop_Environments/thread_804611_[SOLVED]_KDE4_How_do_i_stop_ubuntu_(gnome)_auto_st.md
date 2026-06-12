---
title: "[SOLVED] KDE4: How do i stop ubuntu (gnome) auto started apps auto starting in KDE4?"
date: 2008-05-23
forum: Desktop Environments
---

### Post by Tomatz on 2008-05-23
How do i stop ubuntu (gnome) auto started apps auto starting in KDE4?

Just installed kde4 in ubuntu gutsy and i am really impressed so far apart from this one problem.

Any ideas?

---

### Post by Tomatz on 2008-05-23
I have seen this question asked several times on the forums but no one has yet posted an answer???

---

### Post by Tomatz on 2008-05-23
Bump!

Sorry moderators. I know i am bumping too early but i would really like to know the answer to this problem.

---

### Post by Zorael on 2008-05-23
Curious. And they haven't somehow been copied into [FONT="Courier New"]~/.kde4/Autostart[/FONT]?

---

### Post by Tomatz on 2008-05-23
> **Zorael said:**
> Curious. And they haven't somehow been copied into [FONT="Courier New"]~/.kde4/Autostart[/FONT]?

I wish it were that simple, they're not in the KDE autostart folder, also if I disable them in Gnome then they still autostart in KDE.

I think the only thing I can do is try to work around the problem.  Like make a script to kill the applications as they start in KDE but that's obviously not ideal.

;)

---

### Post by Zorael on 2008-05-23
Second obvious suspicion; are you starting the same session each time? At least KDE3 is set up to automatically restore the last session. And it's not that far a stretch to imagine it failing to refresh that saved session upon next logout.

Perhaps it's a KDE4 thing, but I don't see why it should/could start Gnome "Session" autostarts.

---

### Post by Tomatz on 2008-05-24
> **Zorael said:**
> Second obvious suspicion; are you starting the same session each time? At least KDE3 is set up to automatically restore the last session. And it's not that far a stretch to imagine it failing to refresh that saved session upon next logout.

Perhaps it's a KDE4 thing, but I don't see why it should/could start Gnome "Session" autostarts.

Nope i switched session restore off. This was the first thing i tried :(

I think the problem may be that i am using gdm instead of kdm to login but i thought the gnome auto started apps ran seperate of gdm.

---

### Post by transgress on 2008-07-14
it is loading .config/autostart as well.  try going to the kde system settings - Advanced - Autostart

---

### Post by Tomatz on 2008-07-14
[edit]

see next page

---

### Post by pluckypigeon on 2008-12-04
> **Tomatz said:**
>  i just created a script to kill the gnome autostarted apps in /usr/bin and symlinked it to ~/.kde4/Autostart.



how is this done may i ask??

---

### Post by Tomatz on 2008-12-05
I have a better fix now :)

The problem is both gnome and kde4 use freedesktops autostart standard. Causing gnome autostart apps to start in kde. 

Thankfully this is easy to fix, all you have to do is add:

```
OnlyShowIn=GNOME
```

or

```
OnlyShowIn=KDE
```

To the **.desktop** files you only want to start in gnome (or kde) in ***~/.config/autostart***


Even better, i have a script to do this for you (as you will probably have quite a few of them).

Just **download the attachment** and **extract the script** from the archive, **make it executable** then **double click it** and select **run in terminal**.

**You will receive no terminal output**


Done

;)

---

