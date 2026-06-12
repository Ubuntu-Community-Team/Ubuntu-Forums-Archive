---
title: "Movement of files on GUI using terminal"
date: 2014-06-04
forum: Desktop Environments
---

### Post by Garett_Miller on 2014-06-04
Hello,

I am currently working on making a program allowing the user to move files between monitors or devices using the gaze tracking program opengazer. How can I use the terminal to see which files are currently open, which is in front(viewable), or move the files on the GUI(probably using some coordinate system. Any help would be greatly appreciated! Even if it's just a place to start my search.

Thank you!

---

### Post by papibe on 2014-06-04
Hi Garett_Miller. Welcome to the forum ):P

The command 'lsof' list all open files, but its output could be overwhelming.

If the files you want to move are open by opengazer, you could filter the output to an specific PID. For instance:

To get the opengazer's pid:
```
$ ps aux | grep opengazer
user     **[COLOR="#FF0000"]2307[/COLOR]**  1.7  7.3 1095968 291404 ?      Sl   09:26   3:22 /usr/bin/opengazer
```
and then:
```
lsof -p **[COLOR="#FF0000"]2307[/COLOR]**
```
Alternatively, you could just run:
```
lsof -p $(pidof opengazer)
```
(assuming 'opengazer' is the actual name of the service running).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Garett_Miller on 2014-06-04
Thank you! That's exactly what i was looking for! Do you know by any chance know anything about moving things in the GUI using the terminal? For example, moving a file from one monitor to another? 

Thanks again

---

### Post by papibe on 2014-06-05
> **Garett_Miller said:**
> For example, moving a file from one monitor to another?
I'm not sure what you mean by that.

My guess is you're talking about video feeds? Like to move a live feed that is playing in one monitor to another one?

If you give more details, or an example we may come out with some ideas.

Regards.

---

### Post by tgalati4 on 2014-06-05
You want to get familiar with *xinput*.

```
xinput --list
man xinput
```

You will be working with what is called a "super-desktop", a coordinate system that includes both monitors.  So 800x600 and 800x600 displays would have a super-desktop of 1600x1200 pixels.  Now you have to determine orientation of those displays--side-by-side or corner-to-corner or overlapped.  Then using the correct coordinates within that super-desktop you can correctly pick and place files from one monitor to the next.

---

