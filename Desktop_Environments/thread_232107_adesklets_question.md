---
title: "adesklets question"
date: 2006-08-08
forum: Desktop Environments
---

### Post by Special K on 2006-08-08
Hi Guys & Girls

After reading around and getting to grips with downloading adesklets, i am happy with the downloads, but would like some advice on how to actually run a  desklet.

After reading the "readme" it advises to run the  python script from its location. Does this mean from where it resides after download, or do i have to put it somewhere?

As yet i have not managed to run one! 

Can anyone advise.

Cheers

Spesh

---

### Post by louis_nichols on 2006-08-08
It's pretty easy, actually: go to ```
~/.desklets/*desklet-name*
``` and then run ```
./*desklet-name*.py --nautilus
``` (assuming you're using Gnome. for kde use "kde" instead of "nautilus")
It will ask you whether you want to test the desklet or register it. use whichever you want. All registered desklets start automatically when issuing the command

```
adesklets --nautilus
``` which you may wanna place among your session startup commands.

Keep in mind that some desklets need a certain amount of configuring, as they all have a file config.txt in their folder, which usually has all the info you might need to configure them. 

All this info assumes you use adesklets-installer to fetch desklets.

---

### Post by Special K on 2006-08-08
Thanks for the info Louis, i think i might be doing this wrong but dont know how. I have included a copy of the 4th attempt i did.:confused: 

drwxr-xr-x  4 bongo bongo  4096 2006-08-07 16:01 .
drwxr-xr-x 10 bongo bongo  4096 2006-08-07 16:15 ..
-rwxr-xr-x  1 bongo bongo 20967 2005-03-28 20:34 acpumon.py
-rw-r--r--  1 bongo bongo 40960 2005-03-28 20:34 .acpumon.py.swp
-rw-r--r--  1 bongo bongo 15145 2005-03-28 20:34 COPYING
drwxr-xr-x  5 bongo bongo  4096 2006-08-07 16:01 images
-rw-r--r--  1 bongo bongo  2273 2005-03-28 20:34 README
drwxr-xr-x  2 bongo bongo  4096 2006-08-07 16:01 themes
[email]bongo@bongo-laptop:~/.desk[/email]lets/acpumon-0.1.1$ acpumon.py
bash: acpumon.py: command not found
[email]bongo@bongo-laptop:~/.desk[/email]lets/acpumon-0.1.1$ acpumon.py --nautilus
bash: acpumon.py: command not found
[email]bongo@bongo-laptop:~/.desk[/email]lets/acpumon-0.1.1$ acpumon.py --nautilus
bash: acpumon.py: command not found
[email]bongo@bongo-laptop:~/.desk[/email]lets/acpumon-0.1.1$ acpumon.py
bash: acpumon.py: command not found
[email]bongo@bongo-laptop:~/.desk[/email]lets/acpumon-0.1.1$ acpumon.py
bash: acpumon.py: command not found
[email]bongo@bongo-laptop:~/.desk[/email]lets/acpumon-0.1.1$ ./acpumon.py --nautilus
Do you want to (r)egister this desklet or to (t)est it? r
Registered. Run 'adesklets' to (re)start your desklets.
Look at 'adesklets --help' for special options.
Terminated

---

### Post by Special K on 2006-08-08
ok, i am now a bit further on

++++++++++++++++++++++++++++++++

bongo@bongo-laptop:/home$ cd bongo
bongo@bongo-laptop:~$ cd .desklets
[email]bongo@bongo-laptop:~/.desk[/email]lets$ cd acpumon-0.1.1
[email]bongo@bongo-laptop:~/.desk[/email]lets/acpumon-0.1.1$ ./acpumon.py
Do you want to (r)egister this desklet or to (t)est it? r
Registered. Run 'adesklets' to (re)start your desklets.
Look at 'adesklets --help' for special options.
Terminated

+++++++++++++++++++++++++++++++

it seemed to register, so where/how do i run "adesklets"

---

### Post by louis_nichols on 2006-08-08
you just open a terminal window and run

```
adesklets
```

It's as simple as that. As I said, i would recommend adding it to the session startup programs, so it will be there when you login.

for this, go to System>Preferences>Sessions>Startup Programs, choose "Add" and in the window, just write "adesklets --nautilus". You HAVE TO tell it the interface you're running: whether it's nautilus (for gnome), or kde or something else.

---

### Post by Special K on 2006-08-08
Louis, i added it to System>Preferences>Sessions>Startup Programs as you advised and rebooted......and i am now the proud owner of EIGHT of the same!!!!!:shock:  

can i quit 7 of them and reboot and only one will appear?

---

### Post by Special K on 2006-08-08
Ok, i rebooted and i am now the proud owner of 1 little desklet!

I guessed it would be the same process for installing the big one (system monitor.py, but how wrong i was.

Nothing appears, but i noticed i got a failed warning for something during reboot, something to do with limits, would this be causing the non display of the big multi output monitor?

I suppose i couls still install the individual ones, but it seems a long way round.

Can i say thank you very much for the advice and help so far louis, it been a great help. Any ideas on the non display!

---

### Post by louis_nichols on 2006-08-09
Sorry, but I can't really tell you anything about the reboot warning, as my knowledge doesn't go that deep. But if it is the warning I'm thinking about, it's harmless. Something about failing to stop a process because it's not found? I remember having it once. Never thought it might be caused by adesklets...

As for the desklets, it's simple: every desklet is registered and therefore started as many times as you used *./desklet-name.py* and selected *register *so there's the explanation for the duplicates. It's solved easily, though: open and edit the file ~/.adesklets and delete unwanted copies.

---

### Post by Special K on 2006-08-09
Louis, the error was on reboot and it said

"setting sensors limits......failed"
i have done some digging around and discovered it is something to do with lm-sensors. So i will investigate further.

Many thanks for your help Louis:KS , its a steep lurning curve, but very rewarding.

Spesh

---

