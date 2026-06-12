---
title: "Bizarre: GnomeBaker won't load!"
date: 2006-08-19
forum: Desktop Environments
---

### Post by kline on 2006-08-19
Usually things on Ubuntu just-work.  Tonight I'm trying to start GnomeBaker to see what it's all about, and it fails to load.  On the bottom it says that it is starting up, but then zip.    Anybody know what's happening?

---

### Post by scxtt on 2006-08-19
try running it from a terminal, you should be able to see what's making it error out ...

---

### Post by kline on 2006-08-19
> **scxtt said:**
> try running it from a terminal, you should be able to see what's making it error out ...

Good one.   I didn't start anything prior to the GnmeBaker, certainly nothing in the
Accessibility menu.  But was put to stderr:
[INDENT]
GTK Accessibility Module initialized

GThread-ERROR **: GThread system may only be initialized once.
aborting...
Abort[/INDENT]

Any ideas??

---

### Post by scxtt on 2006-08-19
i'm using KDE now and never saw that error in my Gnome using days, what do you get if you do a **ps -ef | grep -i gthread**?

---

### Post by kline on 2006-08-19
> **scxtt said:**
> i'm using KDE now and never saw that error in my Gnome using days, what do you get if you do a **ps -ef | grep -i gthread**?


Hm.  no threads.  Is there supposed to be a gthrea in the process list?

[INDENT]
root@localhost:/etc/apt# ps -ef|gr -i gthread
101:root      7261  5774  0 00:22 pts/0    00:00:00 grep -n -i gthread
root@localhost:/etc/apt#[/INDENT]


FWIW, there is this strangeness: the tiny red rectangle is showing and says there is an errr with apt-get.  But I don't find anything.   Even a totally new re-init (aka "reboot":) doesn't help.

---

### Post by scxtt on 2006-08-19
are you using the latest version of GnomeBaker?

an **aptitude show gnomebaker** should be able to tell you.

---

### Post by kline on 2006-08-19
Package: gnomebaker
New: yes
State: installed
Automatically installed: no
Version: 0.5.1-0ubuntu1
Priority: optional
Section: gnome

---

### Post by scxtt on 2006-08-19
all the info i see for that error just says to make sure the latest version is installed ... i did use GnomeBaker a few times when using Gnome - worked great (even was able to blank a CD-RW that nothing else could (k3b, Windows, PowerISO)) ...

all i can think is that it doesn't like your burner, but that's not a solution :(

---

### Post by kline on 2006-08-19
Last week I was haing trouble getting evolution working correctly; I finally did, but before I got things working (using gnome-editor) I installed sylpheed.  It will not eveen exec.....    This really is strange.  

And I keep getting logged out of this forum for some reason.   

--What didI do to the computer gods!

I'll try de/re-installing gnomebaker...

thanks much for your help.....

gary

---

### Post by kline on 2006-08-19
Well, still at it.  I did a complete removal an reinstall.  Now, from the cmd line I get part of the grapphic.   From the mouse-click I see part of the graphic for about 0.1sec.

Accoring to   the error output I am missing "libgail-gnome".  So:: is there any rational means of downloading all/any missing gnome libraries (and other _stuff_)?

I have some audio CD's that I want to copy wholesale.  That is why GnomeBAker looked like a good place to start.   **1)**, is this the right program to copy an audio CD and if not, **2)**, is there such a beast?  Oh, and 3), id everything-KDE already here?  do I have to apt-get kde or whatever.   ----***Sorry ***for these dumb questions, but this is the first time I've ever tried to copy a CD; make a backup copy.

[INDENT](gnomebaker:5549): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible

** (gnomebaker:5549): CRITICAL **: failed to create temp 13

(gnomebaker:5549): Gtk-WARNING **: gtkwidget.c:4221: widget not within a GtkWindow
*** glibc detected *** double free or corruption (out): 0x08157798 ***

[/INDENT]

---

### Post by kswnsn on 2006-10-10
If you are/have run KDE, and selected a certain GTK style under the KDE control center, you will have a ~/.gtkrc-2.0 file that will prevent certain GNOME apps from running. First rename this file to see if it clears the issue, and if so, try a different theme. I was using "Glider" but changed to "Human" to correct this issue.

---

### Post by weird_c00kie on 2006-10-13
i'm having problems with GnomeBaker as well, though they're not quite the same as other people's....

my gnomebaker loads, but... well, you can look at the screenshot

that's all it gives me
just bits and pieces of the window.

how do i fix that? i'm still very new to ubuntu and linux, so don't assume any knowledge on my behalf :p


the only way to exit gnomebaker once i try to start it up is by force quitting


thanks in advance for any help



*edit*

for the record, i tried uninstalling and reinstalling it and i've made sure it's the most recent version if that makes any difference to your suggestions

---

