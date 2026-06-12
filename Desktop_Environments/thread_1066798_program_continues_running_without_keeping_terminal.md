---
title: "program continues running without keeping terminal open?"
date: 2009-02-11
forum: Desktop Environments
---

### Post by hatten on 2009-02-11
If i use the command "Transmission", transmission will start and everything. But is there an option or similar that continues having it running "in the background" so that i don't need to have a terminal open for every program i use.
"man Transmission" didn't help me.

---

### Post by howefield on 2009-02-11
Open it from the menu option.

Applications > Internet > Transmission Bittorrent Client

Or use the run box, press ALT + F2 and type transmission


Or have I misunderstood ?

---

### Post by lykwydchykyn on 2009-02-11
If you append a "&" to the end of the command line, it will run in the background.  If you prepend it with the command "nohup", it will continue to run if the terminal is closed.  So you'd want to do like this:

```

nohup Transmission &

```

If you forget to use "nohup" before launching a command, you can find the process id and disown it like this:
```

disown 1111

```
Where 1111 is the process id of the process you want to disown.

If you forget the &, you can hit ctrl-z to suspend the process, then "bg" to cause it to continue in the background.

---

### Post by hatten on 2009-02-11
> **lykwydchykyn said:**
> If you append a "&" to the end of the command line, it will run in the background.  If you prepend it with the command "nohup", it will continue to run if the terminal is closed.  So you'd want to do like this:

```

nohup Transmission &

```

If you forget to use "nohup" before launching a command, you can find the process id and disown it like this:
```

disown 1111

```
Where 1111 is the process id of the process you want to disown.

If you forget the &, you can hit ctrl-z to suspend the process, then "bg" to cause it to continue in the background.
perfect, thanks:popcorn:

---

### Post by hatten on 2009-02-11
how do i find the ID of a program?

---

### Post by howefield on 2009-02-11
System > Administration > System Monitor

5th column in the processes tab.

---

### Post by hatten on 2009-02-11
and in the terminal?

---

### Post by howefield on 2009-02-11
Try pidof program, eg

```
pidof pidgin
```


man pidof

---

### Post by lykwydchykyn on 2009-02-11
You can get a full list of processes with their id's using:
 ps -e

---

### Post by jpeddicord on 2009-02-12
This thread or post has been moved from the Desktop Effects & Customization forum as the posted content is considered off-topic.

Desktop Effects & Customization is a forum for discussing:
[LIST]
[*]Compositing managers such as Compiz
[*]Themes (window themes, widget themes, backgrounds, etc)
[*]Appearance preferences
[/LIST]
Your post did not fit any of these categories, so it has been moved.

Common types of off-topic threads include:
[LIST]
[*]GNOME/KDE/XFCE help in general
[*]Hardware problems not directly related to compositing
[/LIST]

Thanks,
Jacob

---

### Post by hatten on 2009-02-13
Oh thanks, i was not entirely sure where to put it. I'll be sure to remember it until next time =)

---

