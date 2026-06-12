---
title: "Keyboard repeat/delay :: PLEASE HELP!! I don't want to leave Ubuntu!!!"
date: 2005-08-03
forum: Desktop Environments
---

### Post by optikshell on 2005-08-03
Ok, I'm going to type like normal so you can ggggggggggggggggggggggggggggget an idea of what I'm having to deal with as far as the key repeat thing goes.  I've tried different layouts, etc.  The only thing that kinda worked was the "	Option 		"XkbDisable" 	"off" " thing someone else suggested.  The only problem with that is, there seems to be a crazy delay when typing.  I'll be typing, then itttttttttttttttttttttttttttttt'll hannnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnng for a couple seconds then type most of what I'd typed before the delay startttttttttttttttttttttttttttttted.  I've been searching and posting for days, and I can't seem to getttttttttttttttttttttttttttttt any help.  This is such a retaded problem... I know there has to be a soluttttttttttttttttttttttttttion.  

I've used Suse 9.2 on this laptop with KDE and had the same delay/rrrrrrrrrrrrrrrrrrrrrrrrrrrrrrepeat problems, so I don't tttttttttttttttttttttttttttttthink iiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiits a Gnome/Ubuntu problem.  

Laptop:  Toshiba M35-s359

I love Ubuntu, and run the AMD64 distro on my desktop.  I don't want to ggggggggggggggggggggggggggggo back to Windows on my laptop.  But if I can't gettttttttttttttttttttttttttttttt simple things such as typing working on this laptttttttttttttttttttttttttttop in linux... I'll have no choice.  

I'm open to anything, I just want to keep Ubuntu and Gnome.  PLEASE HELP!!!!!

---

### Post by matthew on 2005-08-03
Is it only your g, n, t and r keys that stick? They are kind of close together on the keyboard. Spill anything recently??

Edit: noticed the i now as well...maybe it's something else.

---

### Post by optikshell on 2005-08-03
never happened when I had winXP on here... never spilled anything

---

### Post by matthew on 2005-08-03
How mysterious. Well...I helped you rule out the obvious anyway. Let's hope someone else has an idea.

---

### Post by chazm on 2005-08-03
Can you try with a different keyboard? Maybe somethings messed up with those keys.

---

### Post by spudley on 2005-08-03
FWIW, I had this same problem -- SAME KEYS too!!....  on a P3 600 system -- which ran W2K just fine -- I 'fixed' the problem by turning off the key repeat function (trying to find it)

In: System -> Prefererences -> Keyboard

I played & adjusted settings there and got it to work -- I can't check now, I had to put w2k back on that machine (unrelated reason).  When using the machine after the adjustment, I could tell I had key repeat off, but the average user at that workstation didn't have a clue.

Hope that helps... its certainly not the proper 'fix', but maybe a temporary work around for you until the problem can be more accurately reproduced & a solution found.  I have Ubuntu on a different workstation now and it works great w/ no keyboard problems.

---

### Post by optikshell on 2005-08-03
I've tried that, but i still get the delay.  eg. I can type a word and a half or so, and nothing will happen, then the system "catches up" so to speak.  Really annoying.  

The repeat thing... I've fixed with turning off key repeat.  Not really fixed, just compromised.  I'm really looking to have my keyboard work normally.  I don't like not being able to hold down a key (backspace for instance) and have it delete a bunch of stuff.  Hitting it 20 times or so gets annoying.

Thanks for all the replies... keep em coming.  I justttttttttttttttttttttttttttttttttttt want this basic function to worrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrk.

Here's a question:  What do SUSE 9.2, Ubuntu, KDE, and Gnome all have in common thatttttttttttttttttttttttttttttttt would cause this problem?  It isn't the hardware, as it works fine in Windows XP.

Please help, I just wanna be able to type nooooooooooooooooooooooooooooooooooormally on my laptop.

---

### Post by Ramses on 2005-08-04
This is from: [http://home.imf.au.dk/risager/m35-mandrake/](http://home.imf.au.dk/risager/m35-mandrake/)

> Keyboard and touchboard

The Toshiba keyboard controller has some problems that result in key repetition. There are many fixes to this(See e.g. [http://www.marcsaric.de/m30_linux1.html)](http://www.marcsaric.de/m30_linux1.html)). What I did was the following which was rather easy. I enabled bounce keys. In the System> Configuration> GNOME> Accessibility menu I set the time limit on bounce keys to 5ms

---

### Post by NeoChaosX on 2005-08-04
So how do I get to the Accessibility menu in Gnome? I don't see it in the Preferences menu.

---

### Post by Kitty on 2005-08-04
Hi

I got the same problem with my toshiba laptop.
I solved it by modifying /etc/modules :
the line:
psmouse
become ->
psmouse rate=40

---

### Post by optikshell on 2005-08-04
Using hoary 5.04... i hope I'm not retarded... but i can't find modprobe.conf... did a search for it and everything... doesn't seem to exist.  what am i doing wrong?

jeebus i need ttttttttttttttttttttto fix this.

---

### Post by varunus on 2005-08-04
Hoary renames /etc/modprobe.conf to /etc/modules

Some other distros use modprobe.conf.

---

### Post by optikshell on 2005-08-04
so is /etc/modules a directory... or a file with no extension?

---

### Post by professor_chaos on 2005-08-04
A file...

---

### Post by Kitty on 2005-08-05
[QUOTE=optikshell]Using hoary 5.04... i hope I'm not retarded... but i can't find modprobe.conf... did a search for it and everything... doesn't seem to exist.  what am i doing wrong?

jeebus i need ttttttttttttttttttttto fix this.[/QUOTE]

Ups... Sorry...
Fixed my mistake.

---

### Post by wiraone on 2005-08-05
Once upon a time, my keyboard was suddenly locked dead .. but not the mouse .. found what the culprit was .. the Accessibility Preferences ..

Menu path:

System->Preferences->Keyboard->Accessibility .. DISABLE them all!

---

### Post by foresto on 2008-05-16
Is this the same problem as reported in [this thread](http://ubuntuforums.org/showthread.php?t=772773)?  I'll be posting more info there in a few minutes.

---

