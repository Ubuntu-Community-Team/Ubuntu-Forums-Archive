---
title: "Cairo Clock Adjustment"
date: 2007-04-12
forum: Desktop Effects &amp; Customization
---

### Post by ZERO_SHIFT on 2007-04-12
I installed Cairo Clock which is SOO much better than the older one that I used to use in Desklets.

However I was wondering how can I make the Clock stick to the same position when I restart my computer? I used to have my older desklet clock work at the same place when I restart my PC.

One more thing, how do I get the Cairo Calender??

Thanks in Advance

---

### Post by reclusivemonkey on 2007-04-12
From the cairo-clock man page; 

-x, --xposition X
              The  initial  x-position  of  the  top-left window-corner of the
              clock will be X.

-y, --yposition Y
              The initial y-position of  the  top-left  window-corner  of  the
              clock will be Y.

---

### Post by ZERO_SHIFT on 2007-04-12
How do exactly get to the man page?

Thanks

---

### Post by reclusivemonkey on 2007-04-13
> **ZERO_SHIFT said:**
> How do exactly get to the man page?

Thanks

```

man cairo-clock

```

You can use man *program name* for just about any program on you computer.

---

### Post by ZERO_SHIFT on 2007-04-15
I am sorry but what do i do once I open the man file. I can only read it but how can i change the postion of the clock to the top right corner through the command line?

Thank you

---

### Post by reclusivemonkey on 2007-04-15
> **ZERO_SHIFT said:**
> I am sorry but what do i do once I open the man file. I can only read it but how can i change the postion of the clock to the top right corner through the command line?

Thank you

See my second post in this thread?!

Hmm, you seem to be struggling with this, I am not quite sure why. Is it the starting of a command with flags, or the x/y positioning of an application?

If you are launching this from a terminal, you can use

```

cairo-clock -x 5 -y 800

```

to place your clock in the bottom right corner of the screen. X is the position from the right, Y is the position from the top. Adjust these values as you need to for your screen/preferences. Add it to your "Sessions" and it will start every time you log in.

I'm not aware of any cairo-calendar.

---

### Post by ZERO_SHIFT on 2007-04-16
Thanks it working now, however was wondering how can I set the clock so that appears in all the workspaces and have the seconds hand too by default without the need do the settings whenever I restart the pc again.

Thanks

---

### Post by eentonig on 2007-04-16
The Cairo clock that starts by default, is only starting because you told your computer to start it during boot. And to do that, you entered the command somewhere in a menu. Just change that command with the positioning parameters.

---

### Post by sk8dork on 2007-05-02
> **ZERO_SHIFT said:**
> Thanks it working now, however was wondering how can I set the clock so that appears in all the workspaces and have the seconds hand too by default without the need do the settings whenever I restart the pc again.

Thanks

i have this command in my startup (i use fluxbox but it won't be any different for you really)
```
cairo-clock -x 1472 -y 0 -w 128 -g 128 -s -d -i -e -t radium
```
there i want it to be in the top right hand corner at size 128, so i subtracted 128 from 1600 (my resolution width) and -y 0 means it will start at the very top edge. these parameters should be explained in 'man cairo-clock. for some reason, calling cairo-clock without any parameters and exiting, it will preserve all settings but the position. but if you put any parameters it will only use those parameters and clear out any setting you don't have set in the parameters.

---

### Post by chm0d on 2008-01-25
Zero_Shift I use fluxbox myself and I haven't been able to get cairo clock running.  I have xcompmgr and all depencies installed without problems but yet when I still try to run cairo it tells me i need to be running a composite manager, but xcomp is running.

Rich

---

### Post by ZERO_SHIFT on 2008-01-25
> **chm0d said:**
> Zero_Shift I use fluxbox myself and I haven't been able to get cairo clock running.  I have xcompmgr and all depencies installed without problems but yet when I still try to run cairo it tells me i need to be running a composite manager, but xcomp is running.

Rich

Are you running either XGL/AIGLX ? if not then that might be the issue.

I dont think however that you will need Compiz running.

I would suggest trying to install XGL.

---

### Post by frozenjim on 2008-02-09
I installed cairo-clock and then compiz.  works great.  Maybe compiz will help you?

Problem sometimes only that clock won't retain it's settings.  I find that you need to delete .cairo-clockrc once in a while for your settings to stick.

---

