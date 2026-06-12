---
title: "Restarting Directly into Windows"
date: 2008-12-07
forum: General Help
---

### Post by Arukas on 2008-12-07
I brought this up a while back, and I don't like recycling old threads (6 months ago)  Plus, I using Ubuntu a lot more now.  

I do my best, not to use windows, I have Wine, VMware, DosBox.  That there's just some thing I have to boot into windows for,regardless. (typically 3d graphics stuff)

Is there a script/command I can run, that will boot up into windows on the next boot only, so I don't have to wait for it?  Or is there other solutions.

---

### Post by taurus on 2008-12-07
Why don't you set the default in /boot/grub/menu.lst to point to your windows and set the timeout to 5 seconds.  So if you don't do anything in 5 seconds (or whatever seconds you want to set) when you turn on your machine, it will automatically boot windows.

---

### Post by Arukas on 2008-12-07
Because, when I turn on my computer, I want it to start in ubuntu.  Plus, if windows restarts on its own, I want it to boot into ubuntu.

---

### Post by dkulchenko on 2008-12-07
Then set the default to ubuntu, add the timeout of 5 seconds, and then if you want to boot into windows, at boot, just scroll down the list and choose Windows.

---

### Post by baeksu on 2008-12-07
> **Arukas said:**
> Because, when I turn on my computer, I want it to start in ubuntu.  Plus, if windows restarts on its own, I want it to boot into ubuntu.

Have you looked at [grub-reboot](http://wiki.debian.org/GrubReboot)?

---

### Post by eBoxNet on 2008-12-07
I think thats not possible,
It looks like you are saying that you need your os after the shutdown to edit your boot loader..

Thats how i get it :

Make windows just a bit before shutdown to edit your loader and make ubuntu 1st option with 0 timer and just before ubuntu halts to edit your loader and make windows the 1st option with 0 timer like a loop.

i think that can't be done.

(i hope i am not writing stupidities :D )

---

### Post by Arukas on 2008-12-08
> **baeksu said:**
> Have you looked at [grub-reboot](http://wiki.debian.org/GrubReboot)?

That's exactly what I want to do! However, KDE has a thing for it.  Does Ubuntu Gnome have a feature like that?  Or will I have to load  KDE desktop?

---

### Post by soro2005 on 2008-12-08
You right-click on a Panel, enter "custom application launcher" and "grub-reboot [number of WinXP]" --> There you have a button. Or you define a terminal alias. Not really much of a separate feature needed, is there?

---

### Post by Arukas on 2008-12-08
Apparently, you haven't tried you own advice out.  Have you actually done this?  I'm guessing not, since your idea don't work.  I'm looking for effective information.  KDE has a feature, and apparently gnome don't.

---

### Post by russo.mic on 2008-12-08
Why don't you make 2 grub menu config files, then write a script to switch in between them?

---

### Post by mdurham on 2008-12-08
> **Arukas said:**
> Apparently, you haven't tried you own advice out.  Have you actually done this?  I'm guessing not, since your idea don't work.  I'm looking for effective information.  KDE has a feature, and apparently gnome don't.

Why didn't it work, what exactly did you do?

---

### Post by Arukas on 2008-12-08
I did exactly what was stated.  Have you done it, and got it to work?  I'm convinced it was a snide remark, and it wasn't tried.  


Think about it, if I swamp, boot files, when I restart windows, it will not automatically start back into Ubuntu the next start up.

---

### Post by soro2005 on 2008-12-08
> **Arukas said:**
> I did exactly what was stated.  Have you done it, and got it to work?  I'm convinced it was a snide remark, and it wasn't tried. 

It was not a snide remark. Sorry if you got the impression I wanted to give you foul advice. And yes, I have set up quantities of custom launchers, for myself and for other people. If you can run the command in a terminal, but cannot launch it with the custom launcher, then it would, indeed, be easier to assist if you could answer mdurham's question.

The "Gnome way" is to be lean and not have arcane features that one or two percent of the user base might ever be interested in. The custom launcher is one of the many ways that exist to make a bash command available for instant access. You can also define a bash-alias, bind it to a keyboard shortcut, make it available to Gnome Do, etc. etc. I doubt you will be able to use the KDE tool in Gnome. After all, it's in the logout screen. But if you are more one who gets upset about lack of features than one who savours leanness and dialogs stripped down to their bare necessities, than you are perhaphs more of a KDE type anyway.

Before you take this as another snide remark: Linus Torvalds used to have a strong dislike for Gnome.

---

### Post by Arukas on 2008-12-08
I've seen grub-reboot or a grub program in action before.  You could do a one time boot into another OS without babysitting the start screen.  

You'll have to pardon me.  I mistook your reply, I thought you was trying to offer me cheap substitute.   

It requires a sudo command is the problem.


But you are right, KDE might be better for me.  The main reason I use gnome its the ubuntu standard.

---

### Post by soro2005 on 2008-12-08
> **Arukas said:**
> It requires a sudo command is the problem.

Oh, I could have figured. You can prepend your command in your custom launcher with sudo or gksu. You will be prompted for the password, of course.

You should definitely give KDE a spin. Having said that, I still prefer my Gnome.

---

### Post by Arukas on 2008-12-08
I prefer gnome myself.  I don't like the windows feel.  

So why would KDE have a function that gnome wouldn't?  This is something usefull on dual boot machines.

---

### Post by soro2005 on 2008-12-08
> **Arukas said:**
> So why would KDE have a function that gnome wouldn't?  This is something usefull on dual boot machines.

(1) Because nobody has found the need to write up something external.
(2) Because, by design principle, Gnome doesn't contain stuff that's useful only in marginal situations like this. Of course, you will say that this is not a marginal situation. But (1) to some degree attests to (2).

---

### Post by Arukas on 2008-12-08
I think they found the reason, it seems more like people forgot and they don't like remembering.

---

