---
title: "I just broke my sudoers file"
date: 2005-08-14
forum: Desktop Environments
---

### Post by GoA on 2005-08-14
Yes, thats what happened. I tried to modify the  file to get the firestarter to start without asking the the password. I missspelled the username and the file broke. It now cannot be opened and the terminal says me this: 

ha@hki2-8-4-41:/etc$ sudo kwrite /etc/sudoers
>>> sudoers file: syntax error, line 23 <<<
sudo: parse error in /etc/sudoers near line 23
ha@hki2-8-4-41:/etc$

What can I do? there is a file called sudoers~ but I cannot do nothing with it. Can I somehow reinstall the file or what? 

Thank you for help.

EDIT: Actually, I think the problem is bigger than I though. It seems to be that the root password is completely missing so I cannot use my password to do sudo, Maybe a reinstall of system will help? :P

EDIT: A little bit of search and google did the trick. Lets write it also here so that others can also read it. 

So, I booted the machine and entered the recovery console from the grup. In the console I wrote nano /etc/sudoers and retyped the missspelled username. Then I just hit  f3 button to write it into the hardisk and booted my computer normally. Voila, everything works again. But the firewall still needs the password. ;)

---

### Post by lovebug356 on 2005-08-14
That is why everery body say's playing with the root-account is dangerous... ;-)

---

### Post by GoA on 2005-08-14
[QUOTE=lovebug356]That is why everery body say's playing with the root-account is dangerous... ;-)[/QUOTE]
 But what would life be without littlebit of excitement. ;)

---

### Post by yaye on 2005-08-14
[QUOTE=GoA].......What can I do? there is a file called sudoers~ but I cannot do nothing with it.......[/QUOTE]

Hello,

One trick I've learned over the years is to always make a backup of any file I'm going to edit **before** I edit it.  I open the file with gedit and immediately safe it with an additional .orig ( such as xorg.conf.orig for xorg.conf ). If I mess the file, I can get it back by using nano, at the console, to pull up the file with .orig and save the again without the .orig .

> So, I booted the machine and entered the recovery console from the grup. In the console I wrote nano /etc/sudoers and retyped the missspelled username. Then I just hit  f3 button to write it into the hardisk and booted my computer normally. Voila, everything works again. But the firewall still needs the password. ;)

Nano is great for editing text files at a console.  It has an onscreen menu with the commands for writing the file to disk and exiting the program.

Ian

---

### Post by f1dave on 2005-08-15
Moral of the story: be content with sudo.

The developers of ubuntu obviously included it for a reason, as I think does mac osx.

---

### Post by Sam on 2005-08-15
To modify your sudoers file, ALWAYS use visudo: it checks the file format before saving to prevent such problems.

```
$ export EDITOR=gedit && sudo visudo
```

---

### Post by hashimoto on 2005-08-15
[QUOTE=GoA]Yes, thats what happened. I tried to modify the  file to get the firestarter to start without asking the the password. [/QUOTE]

But why do you want the firestarter to run in GUI at startup? Just for the fun of it? The daemon should be running in the background always, so you need the GUI only if you change the settings or want to see what is going on.

---

### Post by GoA on 2005-08-15
[QUOTE=hashimoto]But why do you want the firestarter to run in GUI at startup? Just for the fun of it? The daemon should be running in the background always, so you need the GUI only if you change the settings or want to see what is going on.[/QUOTE]
 Well, actually I don't need it. It runs automatically and I don't know how to get rid of it. :)

---

