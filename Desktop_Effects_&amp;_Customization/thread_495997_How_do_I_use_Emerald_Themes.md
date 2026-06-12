---
title: "How do I use Emerald Themes?"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by rex27 on 2007-07-08
I can't work out how to use themes on emerald...i open emerald theme manager, select the theme and can't work out what to do next. Is there a button i'm supposed to press or something? Or is there something else wrong? Please make your answer absolutely fool proof...it might be that step that i'm missing...thank you!

---

### Post by digital_exhaust on 2007-07-08
I would like the answer to this as well.... I am having the same problem. 

I'm on 7.04 with Compiz-Fusion installed....

---

### Post by tgm4883 on 2007-07-08
Are you starting compiz fusion with
```
compiz --replace -c emerald &
```

---

### Post by DeathOnJuice on 2007-07-08
Right-click the Beryl icon in the top right, go to Select Window Decorator, and pick Emerald.

---

### Post by kpolice on 2007-07-08
It is a bug that has never been fixed eventhough it was present with beryl and it is still present with the emerald version for compiz. 

If you don't want to reload compiz, if you run it with compiz but the same applies to beryl, execute emerald --replace

---

### Post by sdowney717 on 2007-08-14
finally you told me what to do.
click on the theme
then open a terminal and type emerald --replace

this seems to be an obvious big bug, why dont they fix it?

---

### Post by numbah_one's on 2007-12-08
i seem to be having tons of problems with awn,compiz and now emerald..what should i do?
is there any way to fix this?

spiniker@spiniker-laptop:~$ compiz --replace -c emerald &
[1] 9294
spiniker@spiniker-laptop:~$ Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
metacity: Unknown option -c
spiniker@spiniker-laptop:~$

---

### Post by dseybert on 2007-12-10
It's not working for me. I get this:

doug@dougs-laptop:~$ emerald -- replace
emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"

Any ideas?

---

### Post by uberMongo on 2007-12-10
I'm having lots of problems with emerald to. 
I get no error at all, but when I replace the manager every window border and shadow disapears.
I tried everything I could find in this forum and also searched google for a solution but nothing so far.

If my conf helps here it is: ubuntu feisty fawn with compiz fusion running on a P4 3.2GHz, 2Gb ram and a XFX 7950GT 512Mb.

---

### Post by nikRbokR on 2007-12-23
Well, I was having some trouble with emerald.  Did a quick google search and came up with this link: [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion).

It is pretty easy from there.  Then, use the  ```
emerald --replace
``` after Alt+F2 (as said in an earlier post).

You can find more themes on the Beryl site.
Good luck!

---

### Post by The New Guy on 2008-01-26
I ran the code and now the theme is clear and the only thing that I can see are the buttons, and I don't know how to put a normal theme back one it? Help please!

---

### Post by rhc on 2008-01-26
> **The New Guy said:**
> I ran the code and now the theme is clear and the only thing that I can see are the buttons, and I don't know how to put a normal theme back one it? Help please!

Can you tell more?
Go system>preferences>emerald theme manager and choose skin?
What s your problem

---

### Post by The New Guy on 2008-01-26
Well I did and when u click on one is supposed to change it automatically right? well mine does not and I don't know how to change it.

---

### Post by rhc on 2008-01-26
If you are clicking something,then it means you downloaded emerald themes from somewhere,
Click one of them and then make 
ctrl+alt+backspace.
It ll change.

---

### Post by The New Guy on 2008-01-26
It worked, htanks man, so everytime I want to change the theme thats what Im going to have to do?. Would you happen to know why this is happen?

---

### Post by BuntuFreak on 2008-01-26
I installed emerald. I see "Emerald Theme Manager" under Preferences menu. But I don't see the theme active.

So I guessed emerald is having problem running. I looked at my "Sessions". compiz is running, emerald is not. So I went to Terminal and typed 'emerald' at the command prompt. I get this error.

[COLOR="Blue"]emerald: Could not acquire decoration manager selection o[/COLOR]

Anyone know what's going on?

---

### Post by rhc on 2008-01-26
type > emerald --replace.

---

### Post by BuntuFreak on 2008-01-26
I okay I tried emerald --replace

Did not receive any errors. But didn't do anything either.

Thoughts?

---

### Post by rhc on 2008-01-26
Go emerald theme manager.
Select a different engine from themse.
BTW are you restarting your session after emerald.
Select one then ctrl+alt+backspace.
Log on again.

---

### Post by BuntuFreak on 2008-01-26
Yes, I selected a different theme.

And yes, I logged off and on again.

I also restarted my machine.

It simply doesn't work.

Forget the emerald themes for a moment. I can't even get compiz to "see" emerald. My window decorations are gone. Another thread said "emerald" in the command prompt for "Window Decorations" in the Compiz Settings Manager will fix my problem.

I just cannot connect Compiz with Emerald at this point. And I know I'm not the only one with this exact issue. The biggest problem is Emerald will not work without Compiz. And as soon as I enable Compiz, my Terminal goes blank. So the best I can do is keep Compiz disabled, start the Terminal, then enable Compiz. I immediately lose window decorations, but at least my existing Terminal window continues to post characters I type (new ones of course will not). So in that Terminal window, I typed emerald --replace.

I have exactly 6 hair left on my head...I counted !!!

Any other ideas?

---

### Post by Rome.konig on 2008-02-04
go into compiz settings manager under applications/preferences/advance desktop

then go to windows decoration and in the command line type in  "emerald-theme-manager -i"   without ("")   this should enable windows decoration with the use or emerald.  i hoped this worked for you:)

---

### Post by SoberWarlock on 2008-02-04
Make sure the file is named .emerald

---

### Post by Dave2009 on 2008-03-01
> **uberMongo said:**
> I'm having lots of problems with emerald to. 
I get no error at all, but when I replace the manager every window border and shadow disapears.
I tried everything I could find in this forum and also searched google for a solution but nothing so far.

If my conf helps here it is: ubuntu feisty fawn with compiz fusion running on a P4 3.2GHz, 2Gb ram and a XFX 7950GT 512Mb.

I am getting the exact same problem as ubermongo, my title bar completely dissappears on all of my windows, 

Anyone know how to fix this?

---

### Post by stevehof on 2008-03-01
I had the same problem but fixed it by going to:

System > Preferences > Appearance > Visual Effects

And make sure its normal or above, if normal doesn't work try Extra. From then on i got theme changes a just the click of a button

---

### Post by shawngee on 2008-06-09
well i cant get this to work either myself.

I am on Ubuntu 8.04 with emerald installed and i was trying to use a emerald theme by hardy.  I have read this whole post when i type emerald --replace it just reboots my pc and nothing changes. In the emerald theme manager when i highlight the theme it does nothing and when i hit ctrl+backspace+alt it reboots the pc. 

When i try to change the visual effects it gives me a error saying it cant do it and doesnt change.

This sucks lol
Shawn

---

### Post by tgm4883 on 2008-06-09
> **shawngee said:**
> well i cant get this to work either myself.

I am on Ubuntu 8.04 with emerald installed and i was trying to use a emerald theme by hardy.  I have read this whole post when i type emerald --replace it just reboots my pc and nothing changes. In the emerald theme manager when i highlight the theme it does nothing and when i hit **_ctrl+backspace+alt_** it reboots the pc. 

When i try to change the visual effects it gives me a error saying it cant do it and doesnt change.

This sucks lol
Shawn

Your new and I'll give you the benefit of the doubt, but ctrl+backspace+alt restarts X, not your whole PC.  Is the same thing happening when you do emerald --replace or is it actually your whole system restarting.

---

### Post by rev01ut10n on 2008-07-23
ok the command  emerald --replace worked for me but once i close the terminal all the decorations go away.... am i missing something?

---

### Post by tgm4883 on 2008-07-23
> **rev01ut10n said:**
> ok the command  emerald --replace worked for me but once i close the terminal all the decorations go away.... am i missing something?

don't run it from a terminal, hit alt-F2 and run it there

---

### Post by billgoldberg on 2008-07-23
> **rev01ut10n said:**
> ok the command  emerald --replace worked for me but once i close the terminal all the decorations go away.... am i missing something?

use alt+f2 to use the command.

Or better add the command to "system -> preferences -> sessions", that way it will start when you boot up your pc.

---

### Post by overdrank on 2008-07-23
As billgoldberg has summed it up I would like to point to the [[COLOR="DarkRed"]FAQ's[/COLOR]](http://ubuntuforums.org/showthread.php?t=809695) Desktop configurations forum. 

Thread closed. :0

---

