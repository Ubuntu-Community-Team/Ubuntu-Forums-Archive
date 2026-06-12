---
title: "Gusty hangs a while using the exit button"
date: 2007-10-28
forum: Desktop Environments
---

### Post by Gabriele Ribichini on 2007-10-28
Hi all,
I installed Gusty on my desktop and I found a problem when closing the system.
Clicking on the red ON/OFF button or System->Exit.. the system seems to hang for a minute or two. No window appear, no input is taken in consideration but mouse and keyboard seem to be alive.
It behaves like having a transparent window covering the whole monitor.

After a minute or two the system goes back in a normal behavior showing the dialog to choose how I want to exit.

I noticed the Suspend and Hibernate buttons are not shown..
This happens any first time i click after booting !!

If I cancel the window, and then click exit button again.. it works as expected without any delay.
From the second time on, Suspend and Hibernate buttons are available, even if not working properly.

It seems to me the system is looking for ACPI capability at first, to show/hide the available functionalities.. and this take time.

This is really annoying, any suggestion ?

thanks
- gabriele

---

### Post by carlos1992 on 2007-10-28
Hey the same just happened to me like two or 3 times, and i don't have an idea of how to fix it, HELP

---

### Post by denham2010 on 2007-10-28
Hi,

I had a similar problem. Clicking the shutdown button did notning for a while, although I did have normal functionality otherwise.

I found the problem is to do with certain applets that utilise pydcop to talk to amarok.

I had Media Control on my awn bar, and the Now Playing screenlet running (both use pydcop to talk to amarok).

The problem is, if these applets are started before amarok is started, neither can locate the instance of amarok that is running, and somehow, this "locks up" the shutdown button.

When I kill the Media Control and Now Playing applets, the shutdown options suddenly pops up on my screen.

I now ensure that amarok is running before the applets are started and I no longer have the problem.

I can only assume that pydcop ends up in an infinite loop looking for amarok if it is called before amarok is started.

I can only suggest, if you have something running that is looking for an instance of amarok, that you kill that process and see if it makes a difference.

---

### Post by carlos1992 on 2007-10-28
Dude i doubt thats the problem, you know why i hace the problem and i don't even have Amarok, so it most be something else.
It happens when i close all the apps, i'll try to let it rest for about 1 minute (not running apps 4 1 min.) and see if that's the problem too little RAM, (i only have 256 MB really need some more RAM)

---

### Post by Gabriele Ribichini on 2007-10-29
Well, I have some more RAM (512MB).. but no luck.
Even I don't have Amarok installed, mine is a fresh install ! The only files I've keeped from Feisty are the ones in home.
To me it seems something related to ACPI feature.
The first time (when hanging) it is not showing suspend and hibernate buttons, while the other times it doesn't hang but it shows all the buttons.

ciao
- gabriele

---

### Post by kailden on 2007-10-29
ack...I have this problem too.. It only happens the first time I try system->exit from gnome...if I cancel and try again...much quicker...

---

### Post by kailden on 2007-10-29
I even killed off all my .gnome .gnome2 .gconf directories to reset to the default gnome and it still happens.  Old kernels, still happens.

---

### Post by kailden on 2007-10-29
I got it working here.  I found out that I couldn't run gnome-power-manager.

So I tried to run it in a console, and it couldn't find /usr/lib/libwnck-1.so-18.

I made a symbolic link as follows:
[FONT="Courier New"]
sudo ln -s /usr/lib/libwnck-1.so.22 /usr/lib/libwnck-1.so.18[/FONT]

and made sure that gnome-power-manager was running in my gnome session, 

(System->Preferences->Sessions  and check Power Manager)

and now there is no hang.

Does it work for you?

---

### Post by Gabriele Ribichini on 2007-10-30
thanks kailden.
I was able to run gnome-power-manager but it was not included in my session list.
adding it to the list solved the problem.

ciao
- gabriele

---

### Post by dannystaple on 2008-03-15
I am still seeing this in Gutsy.. I realise there is not long until we see Hardy. The workaround suggested does not appear to have worked. Was this ever filed by anybody as a defect (bug)?

When I run ldd `which gnome-power-manager`, it is referencing libwnck-1.so.22 directly, not via libwnck-1.so.18, so this may be down to something else.

The machine I am seeing this on (and only one, others are fine) is not running amarok. The delay tends to be about 3-5 minutes, however, sometimes there is no delay at all. Running a second time may show no delay, but running a third will.

If nobody is aware of a defect number for this then I shall raise one.

---

### Post by unutbu on 2008-03-15
Just before you want to shut down, run this:
```

sudo ifconfig eth0 down

```

Replace eth0 with whatever interface you use to connect to the internet.
Then try shutting down. If there is no more pause, then I think you can safely assume the long delay has something to do with a network connection being left in a broken state.

I know this is not a very satisfactory solution to the problem, but if it works for you, at least you'll know (vaguely) why it was happening.

---

