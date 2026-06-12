---
title: "Avast Antivirus - cannot find it to uninstall it."
date: 2009-05-14
forum: General Help
---

### Post by sent2coventry2003 on 2009-05-14
Hi all,

Sort of new to using Linux regularly (Ubuntu Jaunty) - I tried to install Avast Antivirus. I had to use the --force-architecture command as my system is 64 bit.

Anyway, I have Applications > Accessories > Avast! Antivirus on my menu , however when I click it, it doesn't run. I only get "starting avast! Antivirus" at the bottom taskbar for about 10 seconds. I also tried typing "getlibs" in terminal, but still nothing.

Now I have got fed up enough to want to uninstall it, as I don't really need it, however I cannot find it in either Synaptic Package Manager or Add/Remove. But it's sitting there in my menu, and I think all the files seem to be on my system (checked /usr/lib/avast4workstation ).

Can anyone please advise?

-regards, sent2coventry2003

---

### Post by Tipped OuT on 2009-05-14
Why would you install an anti virus in Ubuntu for? Isn't that one of the reasons why you would use Linux...to not worry about viruses and anti viruses? :p

**EDIT: Sorry I can't help you, but I just wanted to let that out ^^. My apologeeze.**

---

### Post by konqueror7 on 2009-05-14
i used to also use avast, and the package was 'avast4workstation', if i remember correctly...try doing in the terminal
```
sudo apt-get autoremove --purge avast4workstation
```

see if that works...

and oh, maybe his reason is that he can prevent infecting windows machines that are connected to him, thats all...

---

### Post by Tipped OuT on 2009-05-14
> **konqueror7 said:**
> i used to also use avast, and the package was 'avast4workstation', if i remember correctly...try doing in the terminal
```
sudo apt-get autoremove --purge avast4workstation
```

see if that works...

and oh, maybe his reason is that he can prevent infecting windows machines that are connected to him, thats all...

Oh. Thanks for the extra knowledge, cheers! :D

---

### Post by lisati on 2009-05-14
> **Tipped OuT said:**
> Why would you install an anti virus in Ubuntu for? Isn't that one of the reasons why you would use Linux...to not worry about viruses and anti viruses? :p

**EDIT: Sorry I can't help you, but I just wanted to let that out ^^. My apologeeze.**

I'm sure this is answered somewhere ina recurring security discussion.....I'd use it to help avoid *accidentally* passing on something nasty to a Windows machine.

---

### Post by sent2coventry2003 on 2009-05-14
> **konqueror7 said:**
> i used to also use avast, and the package was 'avast4workstation', if i remember correctly...try doing in the terminal
```
sudo apt-get autoremove --purge avast4workstation
```see if that works...

Hi there,

many thanks for your advice, I tried this and got:

***

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avast4workstation

***

By the way, I had the idea to install it because I am dual-booting with XP - some programs I use are Windows only, and I'm probably not quite ready to abandon the Windows world yet having been so accustomed to it over the years.

-regards
sent2coventry2003

---

### Post by konqueror7 on 2009-05-14
have you tried searching for the keyword 'avast' in synaptic, because the version of my avast was for workstation, as the package implies...

---

### Post by sent2coventry2003 on 2009-05-14
> **konqueror7 said:**
> have you tried searching for the keyword 'avast' in synaptic, because the version of my avast was for workstation, as the package implies...

Hi there,

yes I tried that, but nothing comes up. All in all very strange!

-regards
sent2coventry2003

---

### Post by konqueror7 on 2009-05-14
can you give me a link to the program you installed?

---

### Post by sent2coventry2003 on 2009-05-14
> **konqueror7 said:**
> can you give me a link to the program you installed?

Hi there,

I believe it was the one on this page:

[http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)

which gives:

[FONT=monospace]*[http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb](http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb)*[/FONT][I][I][FONT=Verdana]-regards
sent2coventry2003
[/FONT][/I][/I]

---

### Post by steve01832 on 2009-05-14
Using Avast in Linux is much different than it is in Win***s. It is a command line interface that does not automatically update. I tried it and it was garbage. If you want to run an AV in Linux I would recommend ClamTK.

Steve

---

### Post by The-ITu on 2009-05-14
lol you don't need an anti virus for Liux!
Linux is especially designed for absolute 0 viruses!
did you know that expert hackers tryd to get into a secured and locked down text document on ubuntu but failed!! 
you don't need an anti virus so don't worry about it.

---

### Post by konqueror7 on 2009-05-14
@The-ITu
as he already said, he's on a dual-boot and just making precautions...it doesn't mean that we are on linux there is no virus threat... do you think it would be nice to hear that you boast that linux is secured yet you didn't noticed that you accidentally infected a windows machine with a virus you didn't get infected with, the output would be that you linux machine would be the source of the virus, which will make you somehow not secured...

back to topic, we got the same version of avast. i did'nt find a way to uninstall it via package managers, but if it would be me, i would just delete the all files related to it, in the /usr/bin and /ust/lib and just delete the shortcut...;)

oh, and if you want an antivirus, there is a linux version of BitDefender and AVG...currently i'm using BitDefender...

---

### Post by sent2coventry2003 on 2009-05-14
> **konqueror7 said:**
> back to topic, we got the same version of avast. i did'nt find a way to uninstall it via package managers, but if it would be me, i would just delete the all files related to it, in the /usr/bin and /ust/lib and just delete the shortcut...;)

oh, and if you want an antivirus, there is a linux version of BitDefender and AVG...currently i'm using BitDefender...

Hi there,

I can't thank you enough! I got rid of it finally. Seems simple now, but I have to learn as I go along. I probably will check out AVG as that is what I use for Windows.

In response to the "Linux is especially designed for absolute 0 viruses", I use Windows XP on the same computer, and don't want to find a virus or trojan when I load into XP.

-sent2coventry2003

---

### Post by lisati on 2009-05-14
I think we've been sidetracked enough by the "no need for antivirus on Ubuntu". Have a look here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

