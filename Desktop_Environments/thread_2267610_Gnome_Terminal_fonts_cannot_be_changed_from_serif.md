---
title: "Gnome Terminal fonts cannot be changed from serif"
date: 2015-03-02
forum: Desktop Environments
---

### Post by hfinger on 2015-03-02
Back in primordial times I somehow changed the font in Terminal (gnome-terminal) accidentally -- certainly not intentionally. It is now fixated on a 10 pt serif (Roman, Latin) font that is badly spaced so that letters overlap and strange spaces appear within words. Look at the window capture at <[https://www.dropbox.com/s/ftjcw5yv6sj1c7h/gnome-terminal-font-problem_2015-03-03%3D14%3A57%3A08.png?dl=0](https://www.dropbox.com/s/ftjcw5yv6sj1c7h/gnome-terminal-font-problem_2015-03-03%3D14%3A57%3A08.png?dl=0)>. Isn't it horrible?

None of the following tweaks worked:


[LIST]
[*]changing the Monospaced font in Unity Tweaks 
[*]changing the Monospaced font in Ubuntu Tweaks 
[*]changing the Monospaced font using GSettings 
[*]changing the font in Terminal: Edit > Profile Preferences > General, either by itself or in combination with the system fonts as settable in the Tweaks and GSettings, and clicking the **Using the system fixed width font** 
[*]deleting ~/.bashrc 
[*]in Synaptic, *completely* removing and then reinstalling gnome-terminal (disappointingly, some other customisations had been preserved!). 
[/LIST]

I tried Terminal TNG (ttng, Terminal The Next Generation) as an alternative but the Preferences window does not scroll, and does not refresh when you resize it.

):P Drowning not waving ... . Can anybody tell me how to get rid of this maddening font? Or recommend a really good alternative terminal/console emulator?

Regards,
Hedley

---

### Post by papibe on 2015-03-02
Hi hfinger.

May be you had a little accident with sudo?

Le'ts make sure your user is the owner of all the relevant files. Could you open a terminal, run these commands, and post back the results (you can copy/paste the text)?
```
ls -ld .gconf/ .gconf/apps/ .gconf/apps/gnome-terminal/

ls -lR .gconf/apps/gnome-terminal/
```
Regards.

---

### Post by hfinger on 2015-03-02
Thank you, Pabibe. Here are the results of the two commands (with username and computer name heavily disguised):[INDENT][FONT=courier new][FONT=courier new][SIZE=3]MeMeMe@MyComputer:~$ ls -ld .gconf/ .gconf/apps/ .gconf/apps/gnome-terminal/
drwx------ 4 MeMeMe MeMeMe 4096 Mar  3 10:01 .gconf/
drwx------ 8 MeMeMe MeMeMe 4096 Jan  4 18:38 .gconf/apps/
drwx------ 3 MeMeMe MeMeMe 4096 Aug 22  2014 .gconf/apps/gnome-terminal/
MeMeMe@MyComputer:~$ ls -lR .gconf/apps/gnome-terminal/
.gconf/apps/gnome-terminal/:
total 4
-rw------- 1 MeMeMe MeMeMe    0 Aug 22  2014 %gconf.xml
drwx------ 3 MeMeMe MeMeMe 4096 Aug 22  2014 profiles

.gconf/apps/gnome-terminal/profiles:
total 4
drwx------ 2 MeMeMe MeMeMe 4096 Mar  3 10:34 Default
-rw------- 1 MeMeMe MeMeMe    0 Aug 22  2014 %gconf.xml

.gconf/apps/gnome-terminal/profiles/Default:
total 4
-rw------- 1 MeMeMe MeMeMe 1711 Mar  3 10:34 %gconf.xml
MeMeMe@MyComputer:~$[/SIZE][/FONT][/FONT]
[/INDENT]

(Well, ain't that ironic. I tried to change the font of the terminal interaction to Courier New from the drop-down in the forum editing window, but it stubbornly remained ... serif! **But when I received this post in an email message, the terminal text was in Courier New, as requested. Hmmmm ... interesting.**) The 22 Aug 2014 dates are when I installed Ubuntu on this laptop.

Regards, Hedley

Ubuntu 14.04.02 LTS Trusty Tahr (autoupdate daily turned on, all updates accepted except source code)
Gnome Terminal 3.6.2

---

### Post by papibe on 2015-03-02
Thanks.

Let's try reconfiguring the terminal package:
```
sudo dpkg-reconfigure gnome-terminal

sudo dpkg-reconfigure gnome-terminal-data
```
If that doesn't work try reinstalling:
```
sudo apt-get install gnome-terminal gnome-terminal-data --reinstall
```
Let us know how that goes.
Regards.

---

### Post by hfinger on 2015-03-03
Gak! The crummy, badly-spaced, serif roman is still there. You can look at the log of the reconfigure and reinstall commands at <[https://www.dropbox.com/s/7fxo6dw9xmpf4f4/gnome-terminal-font-problem_reconfigure%2C-reinstall.text?dl=0](https://www.dropbox.com/s/7fxo6dw9xmpf4f4/gnome-terminal-font-problem_reconfigure%2C-reinstall.text?dl=0)>. Is configuration stored somewhere not reachable by the reconfigure command, because my bar cursor and choice of monospaced font, Inconsolata, were the same as before reconfig and reinstall?

Regards, Hedley

---

