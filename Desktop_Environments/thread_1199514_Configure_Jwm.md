---
title: "Configure Jwm?"
date: 2009-06-29
forum: Desktop Environments
---

### Post by DracoNyon on 2009-06-29
I am a uber stupid when it comes to linux. I just installed the jwm window manager(I think) and I got it to run in session to pick from there. But nothing shows up when I got to it pretty much just "start" button that when I click it has like 4 option and 2 are useless. Then there are workspace icons next to it. That is it. I need to know how to configure everything so it looks exactly like the pupply linux 4.2.1 version. I need it to look like that. I am a complete idiot so you are going to need to use really stupid talk. So I know nothing about the terminal besides the "sudo apt-get install [blankd]" Can someone give a complete indepth guide on how to do it. I looked on his site but I was completely confused. Help please, and thanks.

PS. running Ubuntu 9.04 if that helps.

---

### Post by kerry_s on 2009-06-29
run> **sudo update-menus**
in the terminal.

---

### Post by DracoNyon on 2009-06-29
the terminal when I am in the jwm session?
Because if that is the case I can't get a terminal to pop up when I am jwm

---

### Post by kerry_s on 2009-06-29
> **DracoNyon said:**
> the terminal when I am in the jwm session?
Because if that is the case I can't get a terminal to pop up when I am jwm

any terminal, fail safe session, even in 1 of the ctrl+alt+f# will work.
you installed jwm on top of gnome right?

so log in to gnome, open the terminal and run the command.

---

### Post by DracoNyon on 2009-06-29
> **kerry_s said:**
> 
you installed jwm on top of gnome right?


Not quite sure, when I click the sessions tab jwm in under gnome.
besides I tried "sudo update-menus" and I got an error saying it doesn't exit or something like that.

---

### Post by kerry_s on 2009-06-29
> **DracoNyon said:**
> Not quite sure, when I click the sessions tab jwm in under gnome.
besides I tried "sudo update-menus" and I got an error saying it doesn't exit or something like that.

thats funny it should have been installed with jwm.
try this:
[B]sudo apt-get install menu
sudo update-menus[/B]

---

### Post by DracoNyon on 2009-06-29
that sort of worked. Now I can actually use programs, it shows me a list of what is installed. However, it still does not look like the one from puppy linux. Also another problem is the internet. I can detect my card but there isn't a network configure app for it to find a network. So um.... Help again.

---

### Post by kerry_s on 2009-06-29
now you need to tweak the jwmrc to your liking.
copy the /etc/jwm/jwmrc to your home folder as .jwmrc.
or in terminal:
**cat /etc/jwm/jwmrc > ~/.jwmrc**

then just open that with a text editor and tweak away. puppy has special programs created just for puppy, so you going to have to find alternatives.

i usually use jwm, but i'm currently only using xfce4. 
you might be able to find some of my jwmrc's around here if you look.

oh, the network app> **sudo apt-get install wicd**

---

