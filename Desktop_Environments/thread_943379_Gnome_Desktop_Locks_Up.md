---
title: "Gnome Desktop Locks Up"
date: 2008-10-10
forum: Desktop Environments
---

### Post by john_gault on 2008-10-10
Hello. I have switched over to ubuntu from XP and I have found it exceptional except that the desktop freezes for no reason. I will use it for a while surfing or browsing the menus and the the window that is open will not close or minimize. The menu bar continues working for a few more seconds then seizes up and none of the force application quit keystrokes work. The only thing I can do is hit the reset button. I do not experience this problem with KDE or with XP, has anyone else experienced this problem?

---

### Post by Toet on 2008-10-10
You could try a mem check from the grub menu to see if your memory is ok. I've experienced this some time and it turned out to be bad memory.

You can also try, if the memory is ok, to temporarily turn off visual effects to see if that helps to find the problem.

---

### Post by saravanan.2407 on 2008-10-10
I also have a somewhat similar problem.
For me sometimes after login into gnome, my desktop will be shown black with no icons. Only the panel will work. I cant even do a right click in the desktop.

---

### Post by john_gault on 2008-10-10
> **Toet said:**
> You could try a mem check from the grub menu to see if your memory is ok. I've experienced this some time and it turned out to be bad memory.

You can also try, if the memory is ok, to temporarily turn off visual effects to see if that helps to find the problem.


I have just upgraded the power supply and changed the memory sticks as well and changed the visual effects. It still happens.  I would go to KDE but I would lose a program I need.

---

### Post by siick on 2008-10-17
I have the same problem too!!
My gnome desktop is locked up! I can't choose an icon an move it, i can't drag & drop, i can't change my wallpaper. In fact everything change (icon movement and wallpaper changing) after killing X.
help please.

---

### Post by theduffman on 2008-10-18
(dell inspiron 9100 / 1gig ram / ati mobility 9800)
I had a 'gnome only' lockup problem once too, but it was only while i used firefox or thunderbird, it would lockup completely, apart from the mouse, but locked so bad i had to power off.  Installin the ati 3d driver fixed it.   Strange bug, but fixed..

---

### Post by siick on 2008-10-18
I've got gnome too. Bug isn't fix for me! I've reinstalled gnome and compiz but problem is still here.

---

### Post by siick on 2008-10-22
Little up............ :)

---

### Post by siick on 2008-11-10
OK, the problem is Nvidia driver but i'm not sure....
When twinview is enable, the problem is here, but with one screen without twinview, all is ok.

[https://answers.edge.launchpad.net/ubuntu/+source/nautilus/+question/48844](https://answers.edge.launchpad.net/ubuntu/+source/nautilus/+question/48844)

---

### Post by poiuyt23 on 2008-11-12
Same problem.  Doesn't exist in Debian or XP on this machine.  Want to use Ubuntu for the ease of use.  Googled and have not found an answer.  

Observations:
Only ever used gnome, so I dunno if KDE would do it.  
Seems to happen more often if firefox is open.
USB mouse is the first thing to go - the machine will still respond to pressing caps lock / num lock and light up the keyboard
Can't ctrl-alt-Fx to tty to kill processes - if I do the machine totally locks up.  
Can't ctrl-alt-backspace to kill Xserver - machine locks up as above.  

Thoughts on how to troubleshoot? Used Linux for a long time but new to having problems so I have no ideas where to begin looking.  

Thanks!

---

### Post by poiuyt23 on 2008-11-12
Oh - sorry - should mention using 8.10 - custom AMD 64 machine - 1 gig of ram and nvidia 7800 agp graphics card with nvidia drivers.

---

### Post by poiuyt23 on 2008-11-14
More observations...
Sometimes when I start X/Gnome (not sure which) my screen goes black and my keyboard goes unresponsive.  Believe this is part of my troubles as the shift-lock key does not light up the LED on my keyboard and I can not ALT-Fx to a text screen.  

Thanks!

---

### Post by siick on 2008-11-25
Same problem with intrepid....

---

### Post by cygnis1 on 2008-12-02
I have the same problem.  Everything works, then I click on the calendar/clock on the upper right panel.  Nothing happens,and by nothing I mean nothing.I can't access applications, places, or sytem.  I can minimize my windows, but after that I cant maximize them.they shutdown button on the upper right does nothing.  I have to do a control alt delete to get the shutdown menu, and then it doesn't work.  I have to do a hard reboot.  If I  don't touch the calendar/clock I have no  problems.
Cygnis1

---

### Post by klotz on 2008-12-18
> **cygnis1 said:**
> I have the same problem.  Everything works, then I click on the calendar/clock on the upper right panel.  Nothing happens,and by nothing I mean nothing.I can't access applications, places, or sytem.  I can minimize my windows, but after that I cant maximize them.they shutdown button on the upper right does nothing.  I have to do a control alt delete to get the shutdown menu, and then it doesn't work.  I have to do a hard reboot.  If I  don't touch the calendar/clock I have no  problems.
Cygnis1

This has started happening to me too with Ubunty Hardy LTS.
If I click on Adjust Date/Time or click on Time Settings, I get a hard crash and reboot.  I have to reboot into a gnome safe session and remove the date applet and then log in with a regular gnome session.

I see reports of this behavior back in 2006, but they are marked solved.
They seem to be related to the evolution calendar plugin.
This one is related to time settings.

If anyone can find a non-closed bug in launchpad, please post it here and we can all vote on it.

Folks in this thread who are not having the specific problem with the time widget, this isn't about that, so please stay here.

---

### Post by 62chevy on 2008-12-18
I too have had the black screen but believe two things may be causing it. 
  1. internet explorer 6 installed by ie4linux. That's what I get for 
     playing with windows.

  2. Screen Resolution. Changing to a resolution higher than 1024 X 768 
     froze the screen.

I stopped playing with ie6 and tried crossover linux and that solved that problem. Not sure I want to pay 40 bucks to play with ie6.

Keep my screen resolution at 1024 X 768 till I couldn't take it any more and decided to risk it all. This time I was able to change the refresh rate and have been fine for about a week now.

I'm running Ubuntu 8.10 on a Dell Dimension 2350 every thing onboard.


My partition with Debian Testing did the same with Screen Resolution.

---

### Post by bluemax7 on 2008-12-21
I have a winfast AMDK6 mother board with an onboard 
silicon graphics video. In the Bios I have the shared memory size as
large as it can go.

I have shut off all of the power modulation, CPU frequency modultation, and 
things like that.

I am have the following three problems, and I bielieve them to 
be seperate issues..

1. If I open an Xterm window and then close it.. any windows from now
on have corrupted sections.. hard to explain.. but when you move 
the window it becomes invisible and does nopt redraw correctly..

If I change the screen resolution.. sometimes I can get the problem to go away

2. Sometimes when scrolling with the mouse.. a window of text.. say a webpage.. will only update at the bottom.. but the rest of the text will
stay the same.. The file folder viewer does the same thing


3. The desktop freezes.. no ctrl-alt-backspace or alt f1 or asything can bring me out of it..

Does anyone know if the Desktop has a mode that is like a debug mode ..?

none of the logs System.. Xorg anything complains that there has been a problem.. I find that very off that some kind of error is not generated if the Kernel is monitoring the Desktop...

- Brett Werner

---

### Post by helmut_ibm on 2009-03-23
Hi.

I have got a similar problem (Ubuntu 7.10) in GNOME. Turning off the fancy 3D effects eliminated this problem. System->Preferences->Appearance.

Then at the Visual Effects Tab select 'None'.

Seemed to be a problem of the graphics driver. But I can live without the transparent effects.

---

