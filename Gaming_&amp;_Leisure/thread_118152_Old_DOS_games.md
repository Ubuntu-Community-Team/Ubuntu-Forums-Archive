---
title: "Old DOS games"
date: 2006-01-16
forum: Gaming &amp; Leisure
---

### Post by seshomaru samma on 2006-01-16
Is there a way to run really old DOS games on ubuntu?

---

### Post by gord on 2006-01-16
using a program called [url=http://dosbox.sf.net]dosbox[/ur] you can emulate a dos system, if you have a reasonable system you can run VGA games fine but you'll need a newer one to run SVGA games, some won't run at all. all in all thought it works very well and you can even improve the graphics with graphical fetures :)

---

### Post by BoyOfDestiny on 2006-01-16
[QUOTE=seshomaru samma]Is there a way to run really old DOS games on ubuntu?[/QUOTE]

Yep dosbox is the way to go. I've tested many of my games (age of them being 1981-1995) with a near 100% success rate.

Go for it!

---

### Post by kwaanens on 2006-01-16
How do I write "/" and other characters?

- Ketil

---

### Post by dcer on 2006-01-16
I had the same problem. It's because dosbox assumes an us keyboard. Don't know how to change that. Try the keys near the enter botton (I have there Ž and &#268;) not sure if you need to use shift with them.

---

### Post by kwaanens on 2006-01-16
Found that ctrl+f1 gave me the opportunity to set characters.
Seems a hard way to get it working though...

- Ketil

---

### Post by Perfect Storm on 2006-01-16
You can also:

```

dosbox /where/the/game/is/XXXXXXX.exe

```

[size=1]*Moving the thread to ubuntu game forum*[/size]

---

### Post by seshomaru samma on 2006-01-17
[QUOTE=gord]using a program called [url=http://dosbox.sf.net]dosbox[/ur] you can emulate a dos system, if you have a reasonable system you can run VGA games fine but you'll need a newer one to run SVGA games, some won't run at all. all in all thought it works very well and you can even improve the graphics with graphical fetures :)[/QUOTE]

sorry for the silly question but in the website's download section theres no ubuntu version, should i download the debian version? can i apt-get it?

---

### Post by Perfect Storm on 2006-01-17
You can apt-get it.

```

sudo apt-get install dosbox
```

---

### Post by mayo on 2006-02-08
To get around all those keyboard problems and other dosbox setup hassles,
I created a Tcl frontend called DOSBoxGui for dosbox.

You can get it [here]("http://www.waszumclique.de/dosboxgui/").

It allows you to create profiles for your games, in which you can store game specific settings like the cpu cycles, etc.

---

### Post by kwaanens on 2006-02-08
```
$ ./dosboxgui.tcl
Error in startup script: couldn't read file "./proc_browsers.tcl": no such file or directory
    while executing
"source [file join $libPath proc_browsers.tcl]"
    (file "./dosboxgui.tcl" line 267)
```

- Ketil

---

### Post by kudu on 2006-02-08
If you copy all the dosboxGui files to the .dosbox/dosboxgui folder created when you executed dosboxGui.tcl and run ./dosboxGui.tcl again from that directory it will work properly. Did for me anyway.

kudu...out

---

### Post by kudu on 2006-02-08
I need help!! How do you get this blasted dosbox thingamajigger running ?

I'm trying to run Steel Panthers WW2 v7.1 but when I try to execute it I get "Steel Panthers WW2 needs a CDROM" or something to that effect. But SPWW2 doesn't run with a CD. It's a downloadable free game, no CD about it. So why the heck does it want a CDROM and how do I convince it it doesn't need one ??

Driving me crazy. I've been messing about with the Dosbox wiki pages trying to figure out how to fix it but nothing seems to work.

frustrated kudu...out

Got it fixed...it was an .ini file edit job. Runs, albeit SLOWLY. Have to speed it up now. But it RUNS!!

kudu...out

---

### Post by kwaanens on 2006-02-09
[QUOTE=kudu]If you copy all the dosboxGui files to the .dosbox/dosboxgui folder created when you executed dosboxGui.tcl and run ./dosboxGui.tcl again from that directory it will work properly. Did for me anyway.[/QUOTE]

Of course! Thanks!

- Ketil

---

### Post by kudu on 2006-02-09
Dosbox is pretty cool!

kudu...out

---

