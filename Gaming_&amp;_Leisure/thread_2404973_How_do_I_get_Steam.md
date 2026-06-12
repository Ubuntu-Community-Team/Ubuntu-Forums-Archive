---
title: "How do I get Steam?"
date: 2018-10-30
forum: Gaming &amp; Leisure
---

### Post by blindbeholder on 2018-10-30
I connected this computer to the internet for the first time, and Immediately updated the software to latest version and downloaded a steam installer (that didn't work) followed by another from steam's website (which worked... at first). The thing was, steam was not appearing as an app, and I couldn't find anyway to make a desktop access for it. After I went and got my preferred browser working, and turned off my computer (It was midnight), I came back the next day to find that the weird function steam was having (appearing as a small icon on my header directly left of the network button), was no longer present, and it still was not in my applications list and the other installers I have tried do not work (because as far as I can tell, the launch button on the app store does nothing).

How do I both install and keep steam on my Ubuntu Gnome?

---

### Post by Bashing-om on 2018-10-30
blindbeholder; Hello :)

Welcome to the forum in general and to linux in particular.

This is ubuntu ! and the first place to look for software is in the software repository. Steam is there :)
fire up a terminal - cause I am terminally minded. and the terminal is universal across all distributions -  and run:
```

apt list steam

```
OH, it is there in the repo ...
More info about the package:
```

apt show steam

```

Like what you see ? Want to install that version ( there are other means to obtain) from the repo ?
then:
```

sudo apt install steam

```
on a fully updated system.
Now as you have other "steams" installed I can accept there is going to be conflicts and difficulties. We can try and work through them.

[INDENT][INDENT]simple as falling our of bed wide awake
[/INDENT][/INDENT]

---

### Post by oldrocker99 on 2018-10-30
That's **exactly** how to install Steam. 

Frankly I didn't know apt list or apt show. You learn, even after 10 1/2 years of Linux usage, something new every day. At my age, 70, I always have new things to learn.

---

### Post by blindbeholder on 2018-10-30
It's fun typing those commands into the terminal and getting information that tells me that the program exists on my computer and is just out of reach somewhere in the dark corners of- Can I just launch the program I installed, at all? I already knew that it was installed, the problem lies in actually being able to USE it. The only time it ever launched on this computer was completely randomly and of its own volition 20 or so minutes after installing.

---

### Post by blindbeholder on 2018-10-30
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
I typed "steam" into the terminal, which, booted it up, updated it, and shut it down.
Retyped, it turned on, decided it was up to date, and turned off
and then on
It's now acting like this is my first time using it here.
I'm not going to put a solved tag until I know this is actually working, but it might be?

---

### Post by oldrocker99 on 2018-10-31
Good luck. Next time, definitely install Steam from the repositories.

---

