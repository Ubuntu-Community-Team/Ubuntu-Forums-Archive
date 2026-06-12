---
title: "Trying to find a look."
date: 2010-11-29
forum: Desktop Environments
---

### Post by KeitaroCoS on 2010-11-29
Hello everyone, I've decided to go and install ubuntu on my old as heck laptop.  So far so good, but there's one thing that I'm looking for, a minimalistic desktop environment that looks like the old school terminals.  For more of an idea on what I'm talking about, here's an image supplied via 4chan's /g/ section.

[img]http://sadpanda.us/images/293495-BEJM44Z.png

The user also posted a link to the ncmpcpp config which which can be found [here](http://pastebin.com/C5L56rBG).

My question is what I need to get my desktop to start looking like this.

Many thanks, and much love,
KeitaroCoS

---

### Post by roguebuck on 2010-11-29
looks like an alternate window manager (alternate to gnome or kde anyways)

look [here]("http://xwinman.org/")

fwir, these are the most popular: openbox:

[http://openbox.org/wiki/Main_Page](http://openbox.org/wiki/Main_Page)

and fluxbox:
[URL="http://www.fluxbox.org/"]
http://www.fluxbox.org/[/URL]

---

### Post by KeitaroCoS on 2010-11-29
Thanks for the reply, I went looking around with those two in mind and found that it was, indeed, fluxbox.  So does this mean that I'd have to change my linux distro to use it?  The few things that I've seen that include are all Arch linux.

---

### Post by m_duck on 2010-11-29
The window manager in the screenshot is DWM. It's a tiling window manager, though in the screen shot is in floating mode (><>).

[DWM]("http://dwm.suckless.org")

---

### Post by akand074 on 2010-11-29
Believe it or not, Fluxbox is actually in the ubuntu repositories.

```
sudo apt-get install fluxbox
```

Then you can choose either gnome or fluxbox before you login. If you want just fluxbox for sure then you can just uninstall gnome after.

---

### Post by KeitaroCoS on 2010-11-29
I just found that you can install dwm via apt-get.  The only problem is that when when I select DWM from the sessions, it only shows the the top bar, making logging out impossible.  I also couldn't do anything else (open new windows, programs, etc.).

---

### Post by akand074 on 2010-11-29
> **KeitaroCoS said:**
> I just found that you can install dwm via apt-get.  The only problem is that when when I select DWM from the sessions, it only shows the the top bar, making logging out impossible.  I also couldn't do anything else (open new windows, programs, etc.).

Perhaps that's its default, you can't write click and add to panel like in gnome? I've never used it so I'm unsure of how it works. There may also be Ubuntu based operating systems out there with it installed by default. There are so many customized Ubuntu systems out there its ridiculous. You might find one with that window manager by default.

---

### Post by bvc on 2010-11-29
> **KeitaroCoS said:**
> So does this mean that I'd have to change my linux distro to use it?No. There's many to choose from. Not all available by default but all should be available via apt-get. It's just a matter of finding a repository.
I don't know if all these are still developed.
[http://xwinman.org/](http://xwinman.org/)

---

### Post by m_duck on 2010-11-29
> **KeitaroCoS said:**
> The only problem is that when when I select DWM from the sessions, it only shows the the top bar, making logging out impossible.  I also couldn't do anything else (open new windows, programs, etc.).

Yeah, being a tiler its very keyboard driven, the most useful bind being **Mod1 + Shift + Return** to open an xterm window by default (Mod1 being the left Alt key). If you also install dmenu, that brings a run dialog type function with tab completion upon **Alt + p**.

There is a short tutorial [here](http://dwm.suckless.org/tutorial) which basically outlines what I said.

What could be considered a downside to DWM is that to modify it (change colours / keybinds etc), one must edit its source code and recompile. Having said that, this is not as scary as it sounds!

If you were more interested in the floating WMs then I would suggest Openbox as it is my personal preference over fluxbox though both are good. I would imagine you could use something like dzen2 to emulate the top bar from the screenshot you posted, or you could use a more typical panel such as tint2.

---

