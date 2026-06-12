---
title: "ubuntu 11.04 launch bar and top bar gone"
date: 2011-04-28
forum: Desktop Environments
---

### Post by ser23 on 2011-04-28
Hi guys I have been using ubuntu since 10.04 version and configure with compiz to activate the corners, cube, etc. No problems with that. When I upgraded to 11.04 these things were not working but honestly I did not care that much and was just playing with compiz, so I was playing with an option in compiz about the size of the icons in the new 11.04 launch bar, just when I clicked it my top bar and launch bar are gone and not coming back after rebooting many times. Would you tell me please how can I restore this two 11.04 bars or panel.
 
BTW I already uninstalled compiz via terminal and the same problem is happening, maybe important for you to know (alt+f2 or other shortcuts not working except for ctr+alt+t) Thank you 
 
Ser

---

### Post by ivanovnegro on 2011-04-28
I had a similar bug when I was playing with the Compiz settings but you removed Compiz, wasnt a good idea as it is needed to have a working Unity.
Reinstall Compiz and try it again.

---

### Post by ser23 on 2011-04-28
Thank you for ur answer. Reinstalled and did not touch anything in it, and still the same problem. 
 
more ideas please

---

### Post by ser23 on 2011-04-28
Solved. I just run in terminal [COLOR=#222222]unity --reset.[/COLOR]
[COLOR=#222222][/COLOR] 
[COLOR=#222222]BTW unity was not installed. 


[/COLOR]

---

### Post by ivanovnegro on 2011-04-28
Strange if it wasnt installed.
Yes, with this command, I forgot it, you can restore Unity.

---

### Post by willchurch on 2011-04-28
I have the same problem, I'm not exactly sure how you solved it. Could you please explain it?

---

### Post by ivanovnegro on 2011-04-28
Type in the terminal:

```
[COLOR=#222222]unity --reset[/COLOR]
```

to restore the Unity Desktop.

---

### Post by willchurch on 2011-04-28
> **ivanovnegro said:**
> Type in the terminal:

```
[COLOR=#222222]unity --reset[/COLOR]
```

to restore the Unity Desktop.

I did this and get a long list of stuff in terminal (says initializing a bunch of stuff), but then nothing happens.

---

### Post by dupiparanoid on 2011-04-29
and how do you open terminal from the keyboard, i also have this problem and i can not open anything, everything on my desktop is gone, heeeelp!
bars have also dissappeared #-o

---

### Post by dupiparanoid on 2011-04-29
solved!!
just pressed alt+ctrl+f4, then wrote unity --reset
and there you go! haha i tought i had to format my computer

---

### Post by tjscool914 on 2011-04-29
Having the exact same probably after rebooting to complete the upgrade to 11.04.  I tried ctrl + alt+ f4 and my screen just goes black.  No terminal prompt and no mouse cursor.  Please help!

---

### Post by talofo on 2011-04-29
If your screen goes black and if you do alt+f2 and you get no access to your command line, then, reboot your system, and right after the bios message, before ubuntu starts, press and hold Shift+Down Arrow Key - You will enter on a recovery mode. From there, you can select a graphic safe mode book (that I don't recall the name).

---

### Post by tjscool914 on 2011-04-29
Didnt work!

---

### Post by Krytarik on 2011-04-29
When you are at your (messed up) Unity desktop, just create a launcher at it with either "gnome-terminal" or "unity --reset" itself as the commands.

Greetings.

---

### Post by jjokocha on 2011-04-30
i have the same problem, no bar at the bottom....
how can I solve that, since everything u've suggested doesn't work?
especially this unity --reset doesn't work
thanks

---

### Post by overtoyou14 on 2011-04-30
i experienced that same problem , no bar at the top or bottom bottom ... no access to terminal

now solved!!
pressed alt+ctrl+f4
then wrote username
then password
then type "unity --reset" without quote
:)

---

### Post by octocat on 2011-04-30
> **willchurch said:**
> I did this and get a long list of stuff in terminal (says initializing a bunch of stuff), but then nothing happens.

i have this same problem.
however, looking at the terminal output i notice this:
> libcompizconfig: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory


can this be my problem? I also got my issue same as OP, toying around with compiz.

UPDATE: Toying around to find the problem, I found that deleting compiz deletes Unity. I reinstalled compiz, but does not reinstall unity. 
I typed in "unity --reset" into terminal and it told me that Unity is uninstalled. I reinstalled unity via terminal. and tried "unity --reset" once more, and still no fix.

---

### Post by Krytarik on 2011-04-30
Create a launcher at your Unity desktop for the command "ccsm" (CompizConfig  Settings Manger), launch it and re-enable the "Ubuntu Unity Plugin", enable "Desktop Cube" before if you want to use it, the same for "Rotate  Cube", and check if there are other plugins that have been disabled in  the process.

---

### Post by manik.magar on 2011-05-01
Thanks ... ctrl+alt+f4 and unity --reset solved the problem :)
 
Kudos!

---

### Post by mem101296 on 2011-05-01
I'm having the same problem. I tried everything that you said and nothing worked. I know how to get to system settings but not the apps. Is there any other way to get your launcher bar and your top bar back. Help its getting annoying, my other profiles have one but this one doesn't.

---

### Post by Krytarik on 2011-05-01
> **mem101296 said:**
> I tried everything that you said and nothing worked.
Is the "Ubuntu Unity Plugin" enabled then in CCSM if you are logged in to "Ubuntu" (thus Unity)?

---

### Post by zabaksmers17 on 2011-11-15
> **ser23 said:**
> Solved. I just run in terminal [COLOR=#222222]unity --reset.[/COLOR]
[COLOR=#222222][/COLOR] 
[COLOR=#222222]BTW unity was not installed. 


[/COLOR]

Thank you! I had the same problem and ```
unity --reset
``` fixed it.

---

### Post by chris26jp on 2011-12-12
When you get this fixed, do yourselves a favor and throw a terminal icon on your desktop.  It might save you some headache later on.

---

