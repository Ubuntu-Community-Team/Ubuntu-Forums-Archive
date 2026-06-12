---
title: "Selected region screenshot"
date: 2005-05-21
forum: Desktop Environments
---

### Post by Woocash on 2005-05-21
I'm looking for an application, to take a screenshot of selected region.

Is there anything that could suit me ?

---

### Post by dekoi on 2005-05-21
You can do it in ksnapshot. 
Take a screenshot, then "capture mode" as REGION, then you get crosshairs and can pick the area you want to focus on.

But in the time it took you to post the question you could have taken a screenshot and edited it to what you wanted to show in KolourPaint. ie the *long* way :smile:

---

### Post by Xian on 2005-05-21
[QUOTE=Woocash]I'm looking for an application, to take a screenshot of selected region.[/QUOTE]
In Gnome you can issue the command below.
It will take a screenie of a focused window (in this case with a timed delay).

```
gnome-panel-screenshot --window --delay=3
```
If you have KDE installed you can run ksnapshot.
It will allow you to draw a region of the screen to be captured.

---

### Post by fdoving on 2005-05-21
Hi.

I use 'scrot' to take screenshots  It's a simple commandline tool.

To take a screenshot of the whole screen
# scrot

To select a window to take a sceenshot of
# scrot -s
click the window you'd like a shot of and voila.


scrot is available from the universe repository.
If you haven't enabled universe you can find instructions to do so at: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)


- Frode

---

### Post by Bob D. on 2005-05-21
And of course there is the old standby 'ALT+PrintScreen' keys on the keyboard to take a screenshot of a window and 'PrintScreen' key for the entire desktop.

No additional software or command line typing needed. :)

A screen capture tool akin to SnagIt (Windows) would be nice, but I've yet to find it.

Bob

---

### Post by YourSurrogateGod on 2005-05-21
[QUOTE=fdoving]Hi.

I use 'scrot' to take screenshots  It's a simple commandline tool.

To take a screenshot of the whole screen
# scrot

To select a window to take a sceenshot of
# scrot -s
click the window you'd like a shot of and voila.


scrot is available from the universe repository.
If you haven't enabled universe you can find instructions to do so at: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)


- Frode[/QUOTE]
I've enabled universe, but I can't use scrot. It says that scrot is not found...
```
$ scrot
bash: scrot: command not found
$ man scrot
No manual entry for scrot
```

---

### Post by fdoving on 2005-05-22
[QUOTE=YourSurrogateGod]I've enabled universe, but I can't use scrot. It says that scrot is not found...
```
$ scrot
bash: scrot: command not found
$ man scrot
No manual entry for scrot
```[/QUOTE]
 you'll have to install it first.


'sudo apt-get update'
'sudo apt-get install scrot'

- Frode

---

### Post by YourSurrogateGod on 2005-05-25
[QUOTE=fdoving]you'll have to install it first.


'sudo apt-get update'
'sudo apt-get install scrot'

- Frode[/QUOTE]
I tried to mess around with it and it didn't work, here's what I did...
```
andrew@andrew-ubuntu-comp:~$ scrot ’%Y-%m-%d_$wx$h.png’ -e ’mv $f ~/Desktop/MyDocuments’
giblib warning: unrecognised option /home/andrew/Desktop/MyDocuments’

giblib error: Saving to file ’2005-05-25_.png’ failed
```

---

### Post by rsk on 2006-06-17
I'm curious if anyone had any luck here with finding something similar to Snagit but on linux? It's not just the "current window" capture that is so slick, you can mouse over individually "Square" regions and it will highlight and optionally grab those out to a file for you, nice to drill down to just a popup menu or something like a panel in about 2 seconds, then annotate it and save it.

---

### Post by kevingc on 2007-01-25
I used to be able to screenshot regions by holding down alt (or a nearby key) and dragging a translucent blue box across the screen (ubuntu 6.10), but for some reason I can't do it anymore. Any suggestions?

---

### Post by ComplexNumber on 2007-01-25
i use something called Desktop-data-Manager. here is a screenshot of a selected using (using another instance of DDM to take it).

---

