---
title: "Updated to Vista, Lost Grub"
date: 2006-09-19
forum: Desktop Environments
---

### Post by bobap1950 on 2006-09-19
I just updated XP to Vista RC1.  I lost my dual boot ability doing this upgrade and I can no longer boot to Ubuntu 6.06.  How can I fix it without having to re-enter Ubuntu?  I tried "sudo grub-install /dev/hda" while in the live cd and it did not work.

Thanks for your time and help.

Bob :cool:

---

### Post by lagagnon on 2006-09-19
I guess that you did not realize that Microsoft assumes that its operating system is the best and therefore no other OS could possibly exist on your system? It wipes your MBR and replaces it with its own. Grub is gone, I'm afraid to say.

Did you run Ubuntu recovery? And when you ran that grub-install command what messages did you get? Because what you did is the correct way as far as I know. 

BTW I would call installing MS Vista a "downgrade, not an "upgrade".;)

---

### Post by gatti on 2006-09-19
Seems like you have overwritten your MBR. Try googling for "super grub disk", worked for me when I had to re-install XP

---

### Post by joeljkp on 2006-09-19
Yeah, you need to use the recovery option on the CD to boot into Ubuntu, then do the grub thing you tried before.

---

### Post by distroman on 2006-09-19
Have a look here, might help.
[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub)
> **lagagnon said:**
> BTW I would call installing MS Vista a "downgrade, not an "upgrade".;)
I bet it's going to be a nightmare for the next 3 years. :D

---

### Post by joeljkp on 2006-09-19
How is Vista, anyway? I thought about installing RC1, but I was scared that a lot of my programs and drivers wouldn't work, etc.

---

### Post by rocknrolf77 on 2006-09-19
[http://freshmeat.net/projects/supergrub/](http://freshmeat.net/projects/supergrub/) I've jused it. it's has alot of features. good to have tools like this. :)

---

### Post by artinla on 2006-09-19
The procedure linked by distroman is the best that I have found.  It always works for me.

Vista is crap.  It is a poor implementation of microsoft trying to imitate linux security.  It is nearly impossible to get any programs working unless they were specifically written for it, and it is constantly nagging you with "are you sure", "are you sure that you're sure", and "could you verify that you are sure you're sure?".  I also had great problems with it losing network information and generally not being network friendly.  I agree with the poster above, it is gonna be a crazy year when they release it.  

Don't waste your time with it.

---

### Post by bobap1950 on 2006-09-19
Thanks to all of you for your suggestions.  I went to the link suggested by distroman.  It worked great and all is working now.  Thanks for the information distroman!

For joeljkp, VISTA RC1 is working well on my system.  My printer was not supposed to work under it, but it is working fine.  So far all the programs I have tried are working well under RC1. The previous VISTA beta was garbage but RC1 has drastically improved VISTA.  

I think Ubuntu is a great OS.  The Ubuntu OS itself leaves all Windows programs including VISTA in the dust. I would leave Windows entirely but there are Windows programs that I use and I have not found linux replacements for or the replacements don't do nearly as good a job. Anyway, while I used Ubuntu most of the time I keep Windows around for when I need those programs.

Thanks again for all your help.

Bob  :cool:

---

