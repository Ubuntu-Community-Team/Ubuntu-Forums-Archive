---
title: "GNU Screen and Midnight Commander"
date: 2006-12-11
forum: Desktop Environments
---

### Post by rustikus on 2006-12-11
Hi,

i have a strange problem with GNU screen.
I use Midnight Commander inside of screen.
The navigation works without problems but when i try to open a file with simply pressing return nothing happens. When i use mc without screen everything is fine.
Does somebody know how to fix this?

Thx

---

### Post by paparucino on 2006-12-11
> **rustikus said:**
> Hi,

The navigation works without problems but when i try to open a file with simply pressing return nothing happens. When i use mc without screen everything is fine.
Does somebody know how to fix this?

Did you check if F9--Command--Edit extension file is the same for "user" and "system wide"? Check /etc/mc/mc.ext for system wide and in /home/your user/.mc/bindings

---

### Post by rustikus on 2006-12-11
> **paparucino said:**
> Did you check if F9--Command--Edit extension file is the same for "user" and "system wide"? Check /etc/mc/mc.ext for system wide and in /home/your user/.mc/bindings

The files are different but i think mc should use the user defined file. Anyway i linked the mc.ext to my user defined file but the problem still remains. Very strange.

EDIT: Even the evince %f or mplayer %f commands does not work anymore. I also could not switch to terminal with "CTRL+o" but i think that's a normal behaviour in a screen session.

---

### Post by paparucino on 2006-12-11
> **rustikus said:**
> 
EDIT: Even the evince %f or mplayer %f commands does not work anymore. I also could not switch to terminal with "CTRL+o" but i think that's a normal behaviour in a screen session.
I read again your initial post and a question arise. :-)
What do you mean with "GNU screen" and "without screen". I made a launch in the panel in this way: [B]/usr/bin/gnome-terminal -e mc 
[/B] and everything is ok.
I tried with a pure xterm and it works.

---

### Post by rustikus on 2006-12-11
> **paparucino said:**
> I read again your initial post and a question arise. :-)
What do you mean with "GNU screen" and "without screen". I made a launch in the panel in this way: [B]/usr/bin/gnome-terminal -e mc 
[/B] and everything is ok.
I tried with a pure xterm and it works.

Ah, ok. I mean i start mc inside of "screen" a multi-terminal emulator. My start command is:
gnome-terminal --geometry 130x50 --window-with-profile=Default -e 'screen -a -O -RR'
and inside of this session i start mc.

---

### Post by paparucino on 2006-12-11
> **rustikus said:**
> Ah, ok. I mean i start mc inside of "screen" a multi-terminal emulator. My start command is:
gnome-terminal --geometry 130x50 --window-with-profile=Default -e 'screen -a -O -RR'
and inside of this session i start mc.
I tried your command, everything is ok for me. What I think is that for some strange reason when run in this condition mc cannot reach the mc.ext file.

---

### Post by rustikus on 2006-12-11
> **paparucino said:**
> I tried your command, everything is ok for me. What I think is that for some strange reason when run in this condition mc cannot reach the mc.ext file.

But why should the command mplayer %f does not work? The style of mc could also be read. Very strange... ](*,)

---

### Post by paparucino on 2006-12-11
> **rustikus said:**
> But why should the command mplayer %f does not work? The style of mc could also be read. Very strange... 
I use vlc instead of mplayer. I changed in mc.ext from vlc to mplayer then played .wmv, mpeg, mpg and avi. The only type of file I cannot play is mp4 :-)

---

### Post by rustikus on 2006-12-11
OK. I have located the problem.
In my config i have defined the following

```

shell                 zsh

```

When i comment this out, everything works as expected.

Thanks for your help.

rustikus

---

### Post by paparucino on 2006-12-11
> **rustikus said:**
> OK. I have located the problem.
Thanks for your help.

I made nothing. :-)

---

### Post by rustikus on 2006-12-11
> **paparucino said:**
> I made nothing. :-)

Thanks to this thread i have solved the problem. ;)

The fact that for you everything works fine have me led to a misconfiguration in my configs. :)

---

