---
title: "text mode windows?"
date: 2011-02-08
forum: Desktop Environments
---

### Post by zanzes on 2011-02-08
hey guys 
im on ubuntu 10 10 and i was thinking
is there a way to run a fullscreen text mode at login (something like ctrl+alt+F1)
but still be able to have windows popup on top of that
so that i can still use commands like display *.png or firefox or something

i have bin trying to find something like this but i cant find any

---

### Post by mcduck on 2011-02-08
That sounds like you might want to try one of the tiling window managers, like Ion, Awesome or i3... :)

[http://i3.zekjur.net/screenshots/i3-1.png]("http://i3.zekjur.net/screenshots/i3-1.png")

---

### Post by w3rt on 2011-02-08
I suggest i3 too, by far the best solution imo

---

### Post by zanzes on 2011-02-08
interesting I'll take a look at it

---

### Post by zanzes on 2011-02-09
thx i am gonna use i3 from now on 


however Its not exactly what i was looking for
they all have some background and the terminal in a window
i would like something where the background is the standard black fullscreen terminal
and the windows opening on top of that 
is there some way to do this?

---

### Post by nothingspecial on 2011-02-09
> **zanzes said:**
> hey guys 
im on ubuntu 10 10 and i was thinking
is there a way to run a fullscreen text mode at login (something like ctrl+alt+F1)
but still be able to have windows popup on top of that
so that i can still use commands like display *.png or firefox or something

i have bin trying to find something like this but i cant find any

Yeah, you need to use the framebuffer.

You have to give yourself permission to use it first, by making a udev rule.

Be aware before you do this that I am unsure which is safer from a security view.

Option one, make yourself the owner of the framebuffer with limited permissions for everyone else.
```

sudo nano /etc/udev/my-rules.d/framebuffer.rules
```

Then put a line in it like this
```

KERNEL=="fb0",  OWNER="user", MODE="0640"
```

change user for your username

option two, keep root as the owner but elevate the permissions for users

first add yourself to the video group

```
sudo usermod -a -G video user
```

then put this line in the same file as above

```

KERNEL=="fb0",  OWNER="root", MODE="0660"
```

Then use your tty consoles as normal

install mplayer and fbi

to watch videos use mplayer, to view images use fbi. You can use links2 -g for a web browser ans see pictures in it, or use elinks and set fbi to view images.

Install gpm so you can use your mouse/trackpad.

There`s tons of other stuff you can do with just the framebuffer eg fbgrab to make a screenshot.

One thing to bear in mind is that fbi will not work with terminal multiplexers such as screen or dvtm, if you like using those you will have to switch to a different tty to view images.

---

### Post by zanzes on 2011-02-09
thx but when i try to run programes like firefox i get:
error: no display specified

did i miss something?

---

### Post by nothingspecial on 2011-02-09
> **zanzes said:**
> thx but when i try to run programes like firefox i get:
error: no display specified

did i miss something?

Yep, you can't run gui programs in the console. Use links2 -g or elinks instead.

---

### Post by zanzes on 2011-02-09
> **nothingspecial said:**
> Yep, you can't run gui programs in the console. Use links2 -g or elinks instead.

oh okay you just quoted my post where i asked how to do that so i thought you were showing me how to do that :)

---

### Post by zanzes on 2011-02-09
maby i should be more specific

i am looking for something where the terminal IS the background 
but with a window manager or something 
so that programes stil can open on top of that

NO background image
NO menu bar
nothing

but able to open programes

---

### Post by mcduck on 2011-02-09
The closest you are going to get to that *is* using one of the minimal tiling window managers, like the ones I suggested. To have a window, you need to have a window manager. And window managers simply don't get more minimal as those.

Many of them do support floating windows. And if you want to, you are of course free to use only one terminal window in the background.

---

### Post by nothingspecial on 2011-02-09
Ah, sorry, I thought you wanted to use the ttys but view stuff.

In that case, assuming you are running  compiz and gnome-terminal

autohide your panel

in the window decoration thing in compiz put a rule

```
!title=^user@box
```

change user@box for your user and computer name, basically, the thing that is displayed in the top bar when you open a terminal.

Then in your terminal preferences, in the general tab uncheck "show menubar", set a black background in the background tab, and in the scrolling tab select scrollbar is disabled.

Either fullscreen it when it`s opened, or you will have to set the geometry for your system

Then you get this, if that`s what you mean[ATTACH]183089[/ATTACH]

---

### Post by zanzes on 2011-02-09
that is exactly what i meant  thx :D

but its still only a terminal covering the gnome desktop so it still has a lot of stuff running

also is there a way to it without compiz? cos i find that stuff like that  uses more resources than id like to see from a computer doing nothing

maybe it would be simplest to do a clean debian install with no desktop and go from there?

---

### Post by nothingspecial on 2011-02-09
Zanzes mate,

I don`t know what to say???

Come on, you either want X or you don`t.

---

### Post by tgm4883 on 2011-02-09
X is required to run graphical programs like Firefox. You can't launch firefox without it.

You could remove both panels then make the terminal your background. I haven't looked though these instructions, so i'm unsure if it uses compiz or not.

[http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop](http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop)

---

### Post by zanzes on 2011-02-10
yeah i know i just dont understand why it x cant run invisibly in the background and only be used to open programs?

---

### Post by agonc on 2011-02-10
how to install that i3 thing?

---

### Post by zanzes on 2011-02-10
> **agonc said:**
> how to install that i3 thing?


sudo apt-get install i3
config info at [https://wiki.archlinux.org/index.php/I3#Configuration](https://wiki.archlinux.org/index.php/I3#Configuration)

---

### Post by tgm4883 on 2011-02-10
> **zanzes said:**
> yeah i know i just dont understand why it x cant run invisibly in the background and only be used to open programs?

You don't make any sense.


> why it x cant run invisibly in the background and only be used to open programs?

> that is exactly what i meant thx 

**but its still only a terminal covering the gnome desktop so it still has a lot of stuff running**

also is there a way to it without compiz? cos i find that stuff like that uses more resources than id like to see from a computer doing nothing

maybe it would be simplest to do a clean debian install with no desktop and go from there?

So do you want X to run in the background or not?


The first question has already been answered.

> yeah i know i just dont understand why it x cant run invisibly in the background and only be used to open programs?

If the machine starts up in command line mode, it has nowhere to draw windows. You are basically in single application mode (You can only have 1 foreground process at a time.) If you wanted to launch firefox from command line only mode, it wouldn't have anywhere to draw the window, so it would have to start X.

 Your ONLY option is to run X and have a terminal application in some form of full screen mode.

---

