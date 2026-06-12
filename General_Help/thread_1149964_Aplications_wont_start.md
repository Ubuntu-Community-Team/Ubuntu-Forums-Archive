---
title: "Aplications wont start"
date: 2009-05-05
forum: General Help
---

### Post by stanhalen on 2009-05-05
I downloaded a few games and when I try to start them nothing happens. Help please.

---

### Post by Michael.Godawski on 2009-05-05
hi,

where did you downloaded the games? How did you installed them?

---

### Post by stanhalen on 2009-05-05
I downloaded from ad remove applications at the bottom of the applications its tux racer and it shows up on games but it does not start

---

### Post by ddrichardson on 2009-05-05
Run it from a terminal, you'll get some feedback as to why its bombing.

---

### Post by akoskm on 2009-05-05
> **stanhalen said:**
> I downloaded from ad remove applications at the bottom of the applications its tux racer and it shows up on games but it does not start

Try to start it from gnome-terminal, and post here the error messages.

---

### Post by stanhalen on 2009-05-05
does anyone know what the command line is i dont know how that works with more than one word

---

### Post by akoskm on 2009-05-05
> **stanhalen said:**
> does anyone know what the command line is i dont know how that works with more than one word

Applications > Accessories > Terminal.
Type:
```

tuxracer

```

---

### Post by stanhalen on 2009-05-05
naw man its extreme tux racer

---

### Post by akoskm on 2009-05-05
> **stanhalen said:**
> naw man its extreme tux racer
```

extreme\ tux\ racer

```

---

### Post by stanhalen on 2009-05-05
blank@blank-laptop:~$ extreme\ tux\ racer
bash: extreme tux racer: command not found

---

### Post by akoskm on 2009-05-05
> **stanhalen said:**
> blank@blank-laptop:~$ extreme\ tux\ racer
bash: extreme tux racer: command not found
Are you really sure that Extreme Tux Racer's executable is called *extreme tux racer*?
Type:
```

locate tuxracer | grep /usr

```
The executable is probably under /usr/bin.

---

### Post by ddrichardson on 2009-05-05
Its in /usr/games/etracer so```
etracer
```

---

### Post by stanhalen on 2009-05-05
blank@blank-laptop:~$ etracer
Extreme TuxRacer SVN Development --  [http://www.extremetuxracer.com](http://www.extremetuxracer.com) 
(c) 2007 The ETRacer team
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
ETRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for details.

*** etracer error: Couldn't initialize video: Couldn't find matching GLX visual (Resource temporarily unavailable)

---

### Post by akoskm on 2009-05-06
> **stanhalen said:**
> blank@blank-laptop:~$ etracer
Extreme TuxRacer SVN Development --  [http://www.extremetuxracer.com](http://www.extremetuxracer.com) 
(c) 2007 The ETRacer team
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
ETRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for details.

*** etracer error: Couldn't initialize video: Couldn't find matching GLX visual (Resource temporarily unavailable)

Do you have video drivers installed?

---

### Post by ddrichardson on 2009-05-06
Can you post the output from```
glxinfo | grep "render"
```And can you try running it with sudo:```
sudo etracer
```

---

