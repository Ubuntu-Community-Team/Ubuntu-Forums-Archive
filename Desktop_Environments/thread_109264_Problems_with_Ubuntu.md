---
title: "Problems with Ubuntu"
date: 2005-12-28
forum: Desktop Environments
---

### Post by Aero-Z on 2005-12-28
HI,

I'm having some odd problems with Ubuntu. The problem is, when I leave my computer on for the night (for Azureus), then next morning my applications doesn't work anymore. I just see, for example Opening Firefox, and later it just disappears. So I see that there is nothing more to do and I want to Log Out. When I choose that I see just a box without texts like Log Out, Restart Computer etc, there's just a box with Cancel and OK buttons. After pushing OK, I get only my Ubuntu wallpaper and nothing else than hard restart helps me out on this one.
Any ideas?

Sorry for my bad english...

---

### Post by ingo on 2005-12-28
not really, sorry.

but to avoid the brutal power off method you could try CTRL+ALT+F1. Then just log in and type "sudo reboot".

Might also be interesting to see what you get in your /var/log/messages file (it's big, but interesting).

---

### Post by ctt1wbw on 2005-12-28
Sorry, I don't want to hijack a thread, but it never ceases to amaze me how many people in so many different countries use Linux or Ubuntu or anything open source.  I see people from all over the world here at the Ubuntu forums.  I love it!  

Reminds me of the early days of Apple's online service called eWorld.  What great days they were.  :)

---

### Post by anil_robo on 2005-12-28
I faced this problem when I installed some KDE packages (amaroK). I removed all KDE components and this problem was solved automatically.

I think that KDE and GNOME are not quite at peace with each other - sometimes they don't like each other. Please uninstall all KDE applications from your computer and see if this problem is still there.

And let me know what happened! :)

---

### Post by Aero-Z on 2005-12-28
[QUOTE=anil_robo]I faced this problem when I installed some KDE packages (amaroK). I removed all KDE components and this problem was solved automatically.

I think that KDE and GNOME are not quite at peace with each other - sometimes they don't like each other. Please uninstall all KDE applications from your computer and see if this problem is still there.

And let me know what happened! :)[/QUOTE]
I don't think I have any KDE apps installed.:confused: If some dependencies needed some KDE packages then I don't know which ones I have...

---

### Post by ubuntu27 on 2005-12-28
[QUOTE=Aero-Z]HI,

I'm having some odd problems with Ubuntu. The problem is, when I leave my computer on for the night (for Azureus), then next morning my applications doesn't work anymore. I just see, for example Opening Firefox, and later it just disappears. So I see that there is nothing more to do and I want to Log Out. When I choose that I see just a box without texts like Log Out, Restart Computer etc, there's just a box with Cancel and OK buttons. After pushing OK, I get only my Ubuntu wallpaper and nothing else than hard restart helps me out on this one.
Any ideas?

Sorry for my bad english...[/QUOTE]
I have the SAME EXACT problem as you described.

Ubuntu/nautilus/Gnome [Wonder which one...] dosn't respond at all when I leave ir alone for one minute or more. 


[QUOTE=anil_robo]I faced this problem when I installed some KDE packages (amaroK). I removed all KDE components and this problem was solved automatically.

I think that KDE and GNOME are not quite at peace with each other - sometimes they don't like each other. Please uninstall all KDE applications from your computer and see if this problem is still there.

And let me know what happened! :)[/QUOTE]

Well, the only Kde app that I have is k3b, but the problem already started long time before I used any KDE apps....

---

### Post by ubuntu27 on 2005-12-28
**** ignore this post ****

---

### Post by Aero-Z on 2005-12-28
So I post my messages file for you to analyze. Ubuntu even now messes up my modem. When I boot to Ubuntu, then the modem can't make connection. It show that there are no signal in the cable. But if I boot to Windows, then modem works fine.:confused: 
[messages]("http://zone.ee/aerozolic/messages.txt")

---

### Post by cjazz on 2005-12-29
In the situation you describe, it also might be interesting to see what happens when you try to start one of the non-responding applications from the command line at a terminal.

---

### Post by anil_robo on 2005-12-29
Open a terminal and type```
top
``` and press enter..
This will start a process viewer, and you'll be able to see the system resources usage by each process, refreshed every second. Keep this window open, and see how does it change when the bad symptoms appear in your computer.
Tip: To quit **top,** simply press q on the keyboard.

---

### Post by Ocxic on 2005-12-29
check your power settings in the screen saver dialog it might be trying to go into come out of sleep/suspend, and it not workin properly. try disableing power managment.

---

### Post by Aero-Z on 2005-12-29
[QUOTE=Ocxic]check your power settings in the screen saver dialog it might be trying to go into come out of sleep/suspend, and it not workin properly. try disableing power managment.[/QUOTE]
It is disabled

---

### Post by ubuntu27 on 2005-12-29
[QUOTE=Ocxic]check your power settings in the screen saver dialog it might be trying to go into come out of sleep/suspend, and it not workin properly. try disableing power managment.[/QUOTE]

My Screen Saver is turned off. The problem occurs even whe the screen saver is turned on.  ANd about the power management, I don't use it.




Hey! One thing I've noticed is that when you boot Ubuntu and open System Monitor right in the moment that you just log on.  It will prevent "freezing" 

Weird symtoms really...

---

### Post by webra on 2005-12-29
[QUOTE=Aero-Z]HI,

I'm having some odd problems with Ubuntu. The problem is, when I leave my computer on for the night (for Azureus), then next morning my applications doesn't work anymore. I just see, for example Opening Firefox, and later it just disappears. So I see that there is nothing more to do and I want to Log Out. When I choose that I see just a box without texts like Log Out, Restart Computer etc, there's just a box with Cancel and OK buttons. After pushing OK, I get only my Ubuntu wallpaper and nothing else than hard restart helps me out on this one.
Any ideas?

Sorry for my bad english...[/QUOTE]

Hi !!!

Do the problem only occur when you are running Azureus ??? My computer behaved exactly as you described when i left it running with Azureus

Try to change the "Size of cache in MB" under Options->Files->Performans Options in Azureus.

I had to experiment for a while before I found the right setting. I have mine set to 8 MB, and now I can leave it on for days without a problem.

/WebRa

---

### Post by ubuntu27 on 2005-12-29
[QUOTE=webra]Hi !!!

Do the problem only occur when you are running Azureus ??? My computer behaved exactly as you described when i left it running with Azureus

Try to change the "Size of cache in MB" under Options->Files->Performans Options in Azureus.

I had to experiment for a while before I found the right setting. I have mine set to 8 MB, and now I can leave it on for days without a problem.

/WebRa[/QUOTE]

I don't think it is Azureus thing...

I don't have Azureus installed but I have the exact SAME problem as him (Aero-Z)

---

### Post by ctt1wbw on 2005-12-29
[QUOTE=ubuntu27]**** ignore this post ****[/QUOTE]


No, I don't have to if I don't want to.  :p

---

