---
title: "Compiz blackness in windows"
date: 2007-06-25
forum: Desktop Effects &amp; Customization
---

### Post by brunovalentino on 2007-06-25
My computer is a laptop Presario F500, with NVIDIA Go 6150, with ubuntu installed by adding "noapic irqpoll noirqdebug" when starting the live cd.
I then installed the nvidia driver with Envy, and then compiz fusion by using one of the guides.

The thing is, using compiz fusion, my windows were all black. I tried to solve it by adding --indirect-rendering when initializing compiz (compiz --replace --indirect-rendering). Problem was solved, but after a few windows are opened, the horrible black reappears. And sometimes it is possible to get around by resizing the window (pretty smaller than maximize)

Is there any relationship between what I had to add in order to start ubuntu and the black windows? Because I cant get to solve this.

---

### Post by Alex&amp;Linux on 2007-06-25
Looks like the same problem experienced using beryl with nvidia drivers.
Ive had to resize and minimize windows to allow draw.
A fix of sorts for me was to change the rendering path to "copy" from "automatic".
Not sure if this sort of advise can apply to compiz though.

---

### Post by c.dric on 2007-06-26
same problem here with nvidia ... 
without --indirect-rendering i could not open more than 3-4 windows ... with it i can open up to 6 windows ...

not perfect but better :|

---

### Post by Beatbreaker on 2007-07-11
ok i'm having the same problem - but i don't understand what you guys are talking about

how do i enable --indirect-rendering if that is the solution?

---

### Post by psyopper on 2007-07-11
When you launch compiz-fusion your command should be 

```

compiz --replace -indirect-rendering

```

If you are using Emerald Theme Manager you would add 

```

& emerald --replace

```

to the end of the command

---

### Post by Beatbreaker on 2007-07-14
> **psyopper said:**
> When you launch compiz-fusion your command should be 

```

compiz --replace -indirect-rendering

```

If you are using Emerald Theme Manager you would add 

```

& emerald --replace

```

to the end of the command

my connand in "sessions" at the moment is 

```
compiz --replace -c emerald &
```

how would i make that one line?  i remember the simple command "& emerald --replace" did not work for me

---

