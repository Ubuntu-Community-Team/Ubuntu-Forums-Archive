---
title: "Menus have disappeared"
date: 2008-06-27
forum: Desktop Environments
---

### Post by Tom_ZeCat on 2008-06-27
I have Ubuntu 8.04 and used Envy to get the right driver for my video card.  Everything was working great until I booted up to find that YET AGAIN I was stuck at low resolution, despite Envy. That's why I installed Envy -- so that I could solve the constant problem of Ubuntu getting stuck in low res.  I rebooted and I was back at the correct resolution.  However, now the Ubuntu menus are gone!  Arg!  So frustrating.  Now I can only run something if I put a launcher for it on the desktop or if I can right click to access it.  

How do I get my menus back?

---

### Post by bubba_169 on 2008-06-27
Right click on your desktop and create launcher, in the command field put 'gnome-panel'. Fill in the other fields however you want...

After you create the launcher, click it and you should have your panels back. You might need to edit your sessions to make gnome panel start at startup again!

---

### Post by Tom_ZeCat on 2008-06-27
Uhg, when it rains it pours.  Now the menus are gone and I'm stuck at low res.  When I right click and choose create launcher, nothing comes up.  I probably just don't see it because of the low res.  I'm about ready to just reinstall everything.  

This happened after an update.  Now I'm really wary of updates.

---

### Post by guest1234567 on 2008-06-27
Tom, don't give up yet.  It sounds like I had the same exact problem that you did.  Restarting fixed it, but if that doesn't work try this:

1) When you're in X and you can't do anything, switch over to the 1st virtual terminal [ctrl+alt+F1]

2) Login

3) When you get a command prompt, type 'gnome-terminal --display=:0.0'

4) Logout of your VT session [type 'exit']

4) Switch back to your X session [ctrl+alt+F7]

5) You should see a gnome terminal. Type in 'gnome-panel', and you should get the menu bars back.

This (obviously) assumes you're running gnome.  And it's entirely possible you can just run gnome-panel right from the virtual terminal, but I'm not sure.  Feel free to test it out.

Hope this helps.

---

### Post by Tom_ZeCat on 2008-06-27
Thanks for the help.  I tried your suggestions.  Unfortunately, I still haven't had any luck.  Here's what happened in the terminal.  

I typed: 
> gnome-terminal --display:0.0

It answered: 
> unknown option --display:0.0

And it says to run the "--help" option.  I was pretty sure you meant zeroes in that display command, but it tried it with the letter O, both in upper and lower case just in case.  No luck with that either.  

So I ran the "--help" option.  From reading those help screens, I decided to try this: 
> gnome-terminal --display=DISPLAY

It answered: 
> Cannot open display

From the help screens I also tried: 
> gnome-terminal --show-menubar

It replied: 
> Cannot open display

I appreciate the help even if I haven't had luck yet.  I'm willing to try other stuff.  The fortunate thing is I'm meticulous about backing everything important up.  If I have to I can wipe everything out and try fresh.  I also went with KVMing instead of dual booting.  In other words my Linux PC is a completely separate PC from my Windows XP one.  I can therefore go online to here or do searches even if the Linux PC is completely crashed, even if the crash is hardware related.  

I did notice one thing that I didn't notice before.  I went to download Ubuntu and saw that there's a separate download for 64-bit processors.  This is an Athlon 64 3800.  I'm thinking maybe I need to install the 64 bit version.  I don't think I did before.

---

### Post by guest1234567 on 2008-06-27
No no no...there's a space between '--display' and ':0.0'

gnome-terminal [space] --display [space] :0.0

or you could try

gnome-terminal --display=:0.0

actually come to think of it, it would have been clearer if i wrote it like that the first time around - i edited my original instructions. you can also try typing 'gnome-panel' from the virtual terminal, but i'm not entire sure that will work.

---

### Post by Tom_ZeCat on 2008-06-27
Okay, I got a different response this time.  The command went in with no errors, but it just kind of stayed hung with a plain black screen (with the words I typed before, but plain black after that).  So I hit [scroll lock twice] and then the up arrow to KVM back to my Windows PC and I waited.  I went back and it was still hung on that black screen, so I rebooted with Ctrl+Alt+Delete.  Then all kinds of messages came up.  Ubuntu loaded, and the high res was restored, but I still had no menus.  I tried again, figuring I must have gotten impatient.  Same result as before, except this time when I rebooted, it was back on low res.

I do notice when I'm on the black screen hang, when I hit the up arrow, I get this: 

> ^[[A/QUOTE]

[scroll lock 2X] and the down arrow (which also KVMs me back to the Windows PC) I get: 
[QUOTE]^[[B

---

### Post by guest1234567 on 2008-06-27
> **Tom_ZeCat said:**
> Okay, I got a different response this time.  The command went in with no errors, but it just kind of stayed hung with a plain black screen (with the words I typed before, but plain black after that).

So you typed in

```
gnome-terminal --display=:0.0
```

and it just hung after that?  Hmm.  It's possible that command is for whatever reason staying in the foreground after you run it.  Did you try switching back to your X session after typing it in to see if a terminal window appeared?  You can do this by hitting ctrl+alt+F7.

Your other option is to try typing in

```
gnome-panel
```

instead of the gnome-terminal command to see if that will work.  Remember to switch back to X to see if things worked (ctrl+alt+F7).

If none of that works, sorry, I'm fresh out of answers.  Hopefully someone smarter than me will answer.

---

### Post by Tom_ZeCat on 2008-06-27
Actually, just when we thought we were done, there's some progress.  

Okay, I tried it again and it seemed to hang on the black screen.  However, per your suggestion, I hit Ctrl+Alt+F7, which brought the GUI back.  I noticed a plain white square there -- with no minimizer or maximizer or anything -- liked like a plain white sheet of paper.  So I click on it to see if it does anything.  Turns out I'm able to resize it, at which point it turns into a GUI terminal.  So I type "gnome-panel" and I get: 

> gnome-panel is not currently installed.  You can install it by typing: sudo apt-get install gnome-panel

So I do that.  It installs and then I try typing "gnome-panel."  I do and the menus come back!  Cool, I think we're done.  However, when I close the gnome panel, the menus disappear again.  I do the same thing and the same thing happens.  

I even tried running some progs from the menus.  They worked.  So the situation now is I can use the menus in the GUI as long as I don't close the gnome panel.  Weird.  There must be one more thing to do to keep the menus hanging around.

Edit:
Oh, almost, one more thing.  Should I be concerned that I probably didn't install the 64-bit version of Ubuntu 8.04.  I downloaded it and burned it to a CD, so it's ready to go if I need it.

---

### Post by guest1234567 on 2008-06-27
ah. what's happening is, gnome-panel is a child process of the terminal, so when you kill the terminal (parent process), it's killing the child process too.

instead of:
```
gnome-panel
```

try doing
```
exec gnome-panel
```

which may or may not solve your problem (sorry, wish i knew more).  You also might want to look into setting this up so gnome-panel is automatically run on startup.

on your second point - it depends on what you mean by worried. the OS should work just fine, but you're running a 32 bit OS with a 64 bit CPU. this means it's possible (likely) your hardware isn't being used to its maximum potential unless you install the 64 bit version. once again, it depends on what you mean by 'worried'. Windows XP is a 32 bit OS.  Many people run that on 64 bit CPUs.  It works just fine.  I'm not a hardware guy (or really a software guy for that matter), so I'm not sure exactly how it works.  I don't know if the upper 32 bits aren't used at all, or what.

a little wordier than i wanted to get...but basically, if i were you, i'd just go ahead and install the 64 bit version now, especially if this is already a relatively new install. if you decide not to, it's not a huge deal.

---

### Post by Tom_ZeCat on 2008-06-27
That's what I've decided to do.  I'm installing the 64 bit version of the OS as I type.  I played around with various settings and applications and noticed that the system had become buggy.  Time for a reinstall.  I appreciate your help, and am saving this conversation for future reference.  

What I'd like to find now is an equivalent to the Windows application, Acronis True Image.  I use that on my XP machine so that I can quickly do a fresh OS install any time Windows gets buggy or crashes or if I have a hard drive crash.  Because of it, I was up and running with my OS, my applications, and all my data 4 hours after a hard drive crash.

---

### Post by Tom_ZeCat on 2008-06-28
An update: I reinstalled Ubuntu 8.04, this time using the 64-bit version.  I still had major screen res problems.  I tried installing the proprietary driver.  I tried uninstalling that and using Envy.  Nothing worked.  It either was stuck on low res or it would go in and out of high res.  Finally, I installed Ubuntu 7.10.  Then just the opposite was true.  It was stuck at a ridiculously high res.  However, when I used the legacy version of Envy on it, all was fixed.  I've been able to fix the res to what I want it on, and so far, so good.  Knock on wood.  

I don't think Ubuntu 8.04 is quite ready for some NVIDIA cards.  Gonna stick with 7.10.

---

