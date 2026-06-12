---
title: "Gtk icons for Fluxbox?"
date: 2009-04-29
forum: Desktop Environments
---

### Post by pw_f100_220 on 2009-04-29
Hey, while in Fluxbox, my gnome applications look amazingly better in Jaunty than they did in Intrepid.  However, I was wondering if it was possible to choose the icon scheme Fluxbox uses.  I have a custom scheme installed in Gnome that looks great, but I don't know how to enable it in Fluxbox.

Any ideas?  this is Flux's big visual flaw...on my system.  Is it possible to fix?

---

### Post by kerry_s on 2009-04-29
install lxappearance to customize the appearance of gtk2 programs.

**sudo apt-get install lxappearance**

---

### Post by pw_f100_220 on 2009-04-29
i tried lxappearance and it worked for window themes but the icons wouldn't change.  not even in the preveiw.  the icon sets i installed were listed, but nothing happened

---

### Post by kerry_s on 2009-04-29
can you do a pic for me, i'm not sure what icons your talking about?

i'm going to assume you still have gnome, so i'll give the command for that.
in fluxbox, in terminal:

**gnome-panel-screenshot**

or for delay, so you can open a menu or what ever:
**gnome-panel-screenshot --delay 5**

i'm going to assume you already know how to use gimp or what ever paint program you use. 

i use mtpaint, Example:

---

### Post by pw_f100_220 on 2009-04-29
Here is Fluxbox.  lxappearance is opened with black-white_2-Style icons highlighted, not showing anything in the preview...and of course nothing happens when I apply.

And Gnome with that icon theme selected.  Nautilus gives the best example, but gedit also shows it.

---

### Post by kerry_s on 2009-04-29
alright try this:

first delete the ~/.gtkrc-2.0 that lxappearance created. in fact you can get rid of lxappearance, since you have gnome will use the gnome parts.

now in terminal:
gnome-settings-daemon &

if it works add it to your ~/.fluxbox/startup
hopefully you should get exactly what you have in gnome because you'll be using the gnome mechanism.

---

### Post by pw_f100_220 on 2009-04-29
worked like a charm!  will gnome-settings-daemon affect fluxbox in any other ways that i'll probably discover later?

thanks!

---

### Post by kerry_s on 2009-04-29
> **pw_f100_220 said:**
> worked like a charm!  will gnome-settings-daemon affect fluxbox in any other ways that i'll probably discover later?

thanks!

nah, it's just a extra process. from your screenshot i don't think your really concerned with low resource, so you'll be fine.
i only have 450mhz 256mb ram, for me every bit counts, i'd rather run ugly then have a extra process. :lolflag:

---

### Post by pw_f100_220 on 2009-04-30
yeah, i like to keep it as shiny as possible while still being able to consider my system overkill...minimalistic and efficient...but still shiny

---

### Post by pw_f100_220 on 2009-04-30
one more question:  do I have to go into gnome to change the icons?

---

### Post by kerry_s on 2009-04-30
> **pw_f100_220 said:**
> one more question:  do I have to go into gnome to change the icons?

nope, you can just call up the program. in fact i think gnome still has the control center which you can use in fluxbox.
in a terminal or alt+f2:
**gnome-control-center**

if it works you can just add it to your fluxbox menu.

---

### Post by pw_f100_220 on 2009-04-30
sweet, works great.  i kinda feel bad since i'm practically using gnome.  i just like the functions of fluxbox, especially keybindings and style customization.

thanks!

---

### Post by kerry_s on 2009-05-01
no big, it's linux, use what you like. i mix programs all the time, i have both gnome and xfce4 programs on my jwm setup, i try and stay away from the kde stuff though. :lolflag:

---

### Post by Anzan on 2009-05-01
gtkchtheme is good to have as well.

---

