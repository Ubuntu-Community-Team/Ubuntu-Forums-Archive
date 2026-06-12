---
title: "Theme The Ubuntu"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by Dwiman89 on 2007-10-31
Hi IVe got Ubuntu 7.10 Gutsy. Compiz Fusion Works great. Ive got that Default human theme on it now. Ive found some cool themes i want to try under the Compiz section on gnome-look.org. All that im seeing refers to using Emerald. Is There a way to use thes themes without using Emerald. I dont see whats the purpose in using emerald if i have compiz fusion. 

So what do I do to install a theme using compiz fusion?

---

### Post by emiltusiowy on 2007-10-31
Compiz-Fusion and Emerald are two different programs.
Compiz-Fusion is just bunch of desktop effects.
If you wish to use Emerald decorations you have to install Emerald :P

---

### Post by Dwiman89 on 2007-10-31
Do i have to in order to use the Compiz Fusion themes. And if so How do I make it where Compiz Fusoin Uses Emerald insted of what ever it uses now?

---

### Post by rocketman768 on 2007-10-31
I also have this question. Could somebody answer how to install the "compiz themes" at [www.compiz-themes.org?](www.compiz-themes.org?)

---

### Post by pjones0404 on 2007-11-01
this is basically what u need to do to get the compiz themes installed. u have to use emerald to draw the windows borders. the other parts of themes are controlled by the actual gtk theme that u select. 

first install emerald y either running "sudo apt-get install" emerald or by using synaptic. 

once this is installed make sure that u have the compizconfig-settings-manager installed. look for this in synaptic as well. 

then go to the windows decoration option and put the word "emerald" in the command field.

now u can go to emerald and import the compiz theme of ur choice.  


this is what i did and it worked, :)

---

### Post by Dwiman89 on 2007-11-01
Cool Ill try that when i get my computer woring again so to speak. Firefox does work though. check it out [http://ubuntuforums.org/showthread.php?t=599160](http://ubuntuforums.org/showthread.php?t=599160)

---

### Post by CheshireMac on 2007-11-02
> **pjones0404 said:**
> this is basically what u need to do to get the compiz themes installed. u have to use emerald to draw the windows borders. the other parts of themes are controlled by the actual gtk theme that u select. 

first install emerald y either running "sudo apt-get install" emerald or by using synaptic. 

once this is installed make sure that u have the compizconfig-settings-manager installed. look for this in synaptic as well. 

then go to the windows decoration option and put the word "emerald" in the command field.

now u can go to emerald and import the compiz theme of ur choice.  


this is what i did and it worked, :)

Okay, so I did all of this, without any trouble, but I'm having trouble understanding your instructions after install. Where do I go to access Emerald for theme installs? I have an Emerald section in System, but it has no effect when I change the theme. I'm going to do a reboot and check it out again, but there was no prompt for it, so by all means, this should be working, right? 
Like I said, there was no issue with the install, so I'm assuming I just don't know what I'm doing. ~LOL~ Thanks for any help.

---

### Post by VictorR on 2007-11-02
What I could suggest:
1. in the terminal type the command
```
 apt-cache search emerald
```
and see if you have a line like this

emerald - Decorator for compiz-fusion

Seem that stuff should be already on your system.
Then go to System -> Preferences -> CompizConfig Settings Manager or just type
```
ccsm
```

click Windows Decoration and check if Command field has
```
emerald --replace
```
This should start Emerald when Compiz starts.

Selecting the different theme in Emerald Theme Manager has an immediate effect so you do not have to reboot the system.

---

