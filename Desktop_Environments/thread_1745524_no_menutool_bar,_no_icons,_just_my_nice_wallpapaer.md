---
title: "no menu/tool bar, no icons, just my nice wallpapaer"
date: 2011-05-01
forum: Desktop Environments
---

### Post by BogdanIoan on 2011-05-01
Hello

This is my first day with ubuntu 11.04. First impression was great but now I have a problem.

I tried to change the desktop switcher to rotate cube. On ubuntu 10.10 I had installed compiz fusion. So I went to compiz setting, I looked for rotate cube and I ticked it. When I did this a couple of windows asking about enableing and disableing poped up, and unfortunatley I clicked them without reading. I assumed they were just interface related...

Know when I open my laptop I don't have any main menu bar, or tool  bar at the top of the desktop nor application icons on my left. I tried "CTRL+ALT+T" but the terminal does not open. I tried opening with recovery mode but unssuccessful.

I've read somebody has issues as well trying to install rotate cube feature. Hope this will help prevent any other problems.

I have an assignment I have to hand in this week so I would be very happy to recover my work.

Thank you

---

### Post by BogdanIoan on 2011-05-01
I found out how to open file system. 

Maybe, If somebody knows how to get to compiz setup in the file system, I could change back to desktop switcher insted of rotate cube.

---

### Post by JRV on 2011-05-01
Open a terminal with <CTRL>-<ALT>-T and enter ccsm.

---

### Post by BogdanIoan on 2011-05-01
Thank you for the good intent, but as I wrote, CTRL ALT T dose not open the terminal. 

However, with CTRL F, I can open the file system. May that help in any way?

---

### Post by atul1412 on 2011-05-01
Same Problem Happened with me.. 
Even i reupgraded mine with a C.D.. But Still No Results.. Somebody Plzz Help Me.. 
 
:( :( :(

---

### Post by Mike Daniels on 2011-05-01
I have also just upgraded to 11.04 and all I get now is my wallpaper. CTRL+ALT+F1/F2 do not work.

There seems to be no way to change the settings as I can't get into the system at all.

Anyone any ideas how to go about fixing this?

Thanks

---

### Post by BogdanIoan on 2011-05-01
CTRL+F works on my computer. It opens the file system, but I can't find my way to the applications. Luckly, I can access my home folder, but that's it.

If someone would know how to browse the files to get to compiz, I guess I could undo the changes I made and maybe that would fix the problem.

---

### Post by vanadium on 2011-05-01
Proceed as following to reset the compiz and unity settings:

- Right-click on the destop, select "create launcher". Specify "bash" as command.
- Double-click to open the terminal
- Issue following commands
```

gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
sudo reboot now

```
With the last command, you will cleanly reboot the system. Provide your login password when asked.

---

### Post by atul1412 on 2011-05-01
I was also having Same problem... But when i tried this.. my Problem got solved..
 
 
You will need to reset compiz and unity settings. Switch to a text terminal by pressing Ctrl+Alt+F1. Login there, and issue the following commands.
Code:
gconftool-2 --recursive-unset /apps/compiz-1unity --reset
You better reboot now
Code:
sudo reboot now
and Unity should now launch properly when the system is ready again.
 
Hope it will work 4 u Even..
 
GOD BLESS !!

---

### Post by kelsos on 2011-05-01
I actually have the same problem and depending on the reboot sometimes the terminal (ALT+CTRL+Fsomething) will appear white with degraded fonts. When I actually manage to runt he commands the unity --reset will end with a segmentation fault, giving me various Glib-GObject-Warnings and some Critical stuff together... when I reboot the problem persists..

---

### Post by Mike Daniels on 2011-05-01
Hi, I have tried the above but get this message:

"Error while parsing options: unknown option --reset" 

Any ideas why this should be happening?

Thanks

Mike

---

### Post by BogdanIoan on 2011-05-01
My problem is solved!

THANK YOU VERY MUCH

---

### Post by CleveRuse on 2011-05-28
I'm also getting an error ...so I typed "gconftool-2 --help-all"  and basically it says 'reset' is not a command, so how r u guys getting it to work?

God I'm Sooo sick of "Compiz" screwing things up ...losing options, boarders disappearing, wndows not resizing correctly or not fitting the screen... WTF? ...I'm getting discusted. I'm -cant believe I'm saying this- really missing 'Windows'

---

### Post by CleveRuse on 2011-05-28
Hey, try replacing the "--reset" at end of the command with "--replace". I found this somewhere else, tho I haven't tried myself, cuz I set the shortcut manually and I have things set up pretty well. I'm interested to see how this works ...let me know. 

BTW, if u use "Ubuntu Tweak", there's an option to reset ...just about anything, either a specific app, multiple  apps at once, or ur whole system. I believe u can even save different settings (like restore points), then restore them whenever (like nandroids). -i'm guessing, I just noticed it. 

Anyway, let me know if the above works. Hope it helps

---

### Post by wildmanne39 on 2011-05-28
> **CleveRuse said:**
> I'm also getting an error ...so I typed "gconftool-2 --help-all"  and basically it says 'reset' is not a command, so how r u guys getting it to work?

God I'm Sooo sick of "Compiz" screwing things up ...losing options, boarders disappearing, wndows not resizing correctly or not fitting the screen... WTF? ...I'm getting discusted. I'm -cant believe I'm saying this- really missing 'Windows'
Hi, look in my signature right below this text and it says reset unity and compiz click on it and follow the instructions.

---

### Post by CleveRuse on 2011-05-29
> **wildmanne39 said:**
> Hi, look in my signature right below this text and it says reset unity and compiz click on it and follow the instructions.

Hey, Thnx, wish ida seen that b4. I stumbled onto an answer anyway. 

While on the subject of Compiz related problems, U have any idea wut would cause my main Compiz page to keep auto-resizing, not fitting on page, and not be able to be resized? It's the only window I'm having a problem with ...now anyway. Or will I find that answer in ur "signature" as well?

Note: I've already reset all my apps using "ubuntu tweak". Then I set everything in Compiz to my liking. I was thinking bout using the "fixed window placement" option, but I'm confused on how.

---

### Post by wildmanne39 on 2011-05-29
> **Mike Daniels said:**
> Hi, I have tried the above but get this message:

"Error while parsing options: unknown option --reset" 

Any ideas why this should be happening?

Thanks

Mike

unity --reset there is a space between unity and --reset

---

