---
title: "GRUB Boot Loader Order"
date: 2005-07-02
forum: Desktop Environments
---

### Post by Scud89 on 2005-07-02
Hi there;
  how are you?

I have just recently installed ubuntu to my system and i must say am very very happy and pleased with it. On my system i also have windows xp. Now for me having ubuntu load as the default OS is perfect, although unfortunetly to the rest it's not as they are unfamiliar with the OS and would prefer the simplistic windows. How might i change the boot order so windows xp is the defualt boot up.

Thanks,
Scud

---

### Post by tonym on 2005-07-02
Edit /boot/grub/menu.lst and put the Windows entry at the top.  Be a bit careful because there is a group of lines that are generated automatically by update-grub  -  there are comments showing the start and end of these.  You  need to put the Windows entry just before the generated lines.

Regards

Tony

---

### Post by ceti on 2005-07-02
goto:
[http://ubuntuguide.org/](http://ubuntuguide.org/)

look for GRUB entries, it may helps.

---

### Post by Scud89 on 2005-07-02
[QUOTE=ceti]goto:
[http://ubuntuguide.org/](http://ubuntuguide.org/)

look for GRUB entries, it may helps.[/QUOTE]
 thanks, for that guys. just another question that i could not be bothered making a new topic for is that i was wondering on how to install the java2 runtime enviroment i have downloaded the files although im having problems installing them...

---

### Post by Scud89 on 2005-07-02
[QUOTE=tonym]Edit /boot/grub/menu.lst and put the Windows entry at the top.  Be a bit careful because there is a group of lines that are generated automatically by update-grub  -  there are comments showing the start and end of these.  You  need to put the Windows entry just before the generated lines.

Regards

Tony[/QUOTE]

also when you say the windows entry what exactly is the windows entry. is it just windows xp blah blah blah or the section its stored on hd. what is it?

---

### Post by ceti on 2005-07-02
[QUOTE=Scud89]thanks, for that guys. just another question that i could not be bothered making a new topic for is that i was wondering on how to install the java2 runtime enviroment i have downloaded the files although im having problems installing them...[/QUOTE]

again, go to the Unoffical Starter Guide, look for Java & follow ALL the steps. It works, I assure you.

---

### Post by Scud89 on 2005-07-02
[QUOTE=ceti]again, go to the Unoffical Starter Guide, look for Java & follow ALL the steps. It works, I assure you.[/QUOTE]
 im not talking about just the plugin for mozilla firefox im talking about the actual runtime enviroment

---

### Post by Scud89 on 2005-07-02
[QUOTE=Scud89]im not talking about just the plugin for mozilla firefox im talking about the actual runtime enviroment[/QUOTE]
 can anyone tell me the actual line i need to enter to make windows the default os. I have tried x_sequence, x_(0,0), (0,0), and heaps of other things i think the only thing i havnt tried is the thing that will work, anyone know the line needed? (PS: It's Windows XP Professional)

---

### Post by Firli on 2005-07-02
> 
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/hda3
#          initrd /initrd-version.img
#boot=/dev/hda
**[COLOR=Red]default[/COLOR]**=0 
timeout=5 
This is what a part of the menu.lst looks like for me. You need to set the [COLOR=Red]**default**[/COLOR] to the number corresponding with windows. (look at the number of options at start-up, 0 is the first option, 1 the second and so on). For me windows was always at the bottom:

my boot options:
Ubuntu
Ubuntu -troubleshooting
memorytest
other operating systems:
Windows

so I set it 4 (it seems to count the lines, as "other operating systems isn't really an option).

The timeout option defines how quickly it autoselects. I don't recommend setting this lower than 3 as it becomes quite hard to select another operating system than the default one in time.

---

### Post by Scud89 on 2005-07-02
[QUOTE=Firli]This is what a part of the menu.lst looks like for me. You need to set the [COLOR=Red]**default**[/COLOR] to the number corresponding with windows. (look at the number of options at start-up, 0 is the first option, 1 the second and so on). For me windows was always at the bottom:

my boot options:
Ubuntu
Ubuntu -troubleshooting
memorytest
other operating systems:
Windows

so I set it 4 (it seems to count the lines, as "other operating systems isn't really an option).

The timeout option defines how quickly it autoselects. I don't recommend setting this lower than 3 as it becomes quite hard to select another operating system than the default one in time.[/QUOTE]
 alrite, i have understood that for the last five plus posts. but what none has yet said is where to actually put those number on what line. eg: savedefualt, title and so on.

---

### Post by kado on 2007-02-21
> **tonym said:**
> Edit /boot/grub/menu.lst and put the Windows entry at the top.  Be a bit careful because there is a group of lines that are generated automatically by update-grub  -  there are comments showing the start and end of these.  You  need to put the Windows entry just before the generated lines.

Regards

Tony

Thanks Tony, 
I am glad I found this thread. I do not have enough background info: how do I get to where I'm supposed to enter the command line you gave?
Someone else installed Grub on my laptop and I am novice. I need to have XP home as the 1st loading OS.
Thanks.

---

