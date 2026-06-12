---
title: "Open Terminal Here?"
date: 2005-05-14
forum: Desktop Environments
---

### Post by b06tmm on 2005-05-14
Forgive me for my ineptness, but how do I open a terminal in any folder that I choose to run a terminal in?

For instance, if I want to open a terminal in /home/user/Menu Editor so I can install it and edit my menus.  How do I do it?  

Can I add/create a right-click context to perform this?

Ubuntu has detected and installed everything that I have and I am very happy with this DIstro!  

Thanks,

Mandrake/Mandriva Silver Member,
Tim 

M$ free for exactly four weeks...

---

### Post by arctic on 2005-05-14
the terminal will be opened at your /home directory by default. simply use the cd command to go to the folder you want to use. e.g.
# cd /home/user/menu
or
# cd ~/menu

oops... i forgot to say: welcome aboard :D

---

### Post by ow50 on 2005-05-14
If you're looking for a nautilus script to open terminal at the directory you're currently browsing in nautilus:
[http://www.iol.ie/~padraiga/scripts/command_prompt_here](http://www.iol.ie/~padraiga/scripts/command_prompt_here)

Copy that to a text editor, save to ~/.gnome2/nautilus-scripts and give it execute permissions.

---

### Post by jobezone on 2005-05-14
[QUOTE=b06tmm]Forgive me for my ineptness, but how do I open a terminal in any folder that I choose to run a terminal in?

For instance, if I want to open a terminal in /home/user/Menu Editor so I can install it and edit my menus.  How do I do it?  

Can I add/create a right-click context to perform this?

Ubuntu has detected and installed everything that I have and I am very happy with this DIstro!  

Thanks,

Mandrake/Mandriva Silver Member,
Tim 

M$ free for exactly four weeks...[/QUOTE]
 There is a huge colection of nautilus scripts here:
[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/) 
[list=1]
[*]Open this one: [http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Open%20terminal/gnome2-terminal-here](http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Open%20terminal/gnome2-terminal-here)
[*]save it as a file called "open_terminal"(the choice of name is yours), and place it inside this directory: ~/.gnome2/nautilus-scripts/ (~ allways points to your home directory)
[*]right-click on the file, open the Properties dialog, and make it executable (in the permissions tab)
[*]you can now right-click on any nautilus window and choose Scripts->open_terminal
[/list]

---

### Post by b06tmm on 2005-05-14
Thanks!!!

I've learned a lot in these four weeks but still have much to learn...I used to be a DOS junkie and didn't realize how lazy Windows had made me until recently when I embraced Linux exclusively.

To my terminal problem...

No matter how I type the folder name (Menu Editor) I cannot navagate to it!  See example:

root@ngundo:/home/tim # ls -l
total 80
drwxr-xr-x    3 tim tim 4096 1969-12-31 18:00 Cool Pics
drwxr-xr-x    2 tim tim 4096 2005-05-14 16:08 Desktop
drwxr-xr-x    3 tim tim 4096 1969-12-31 18:00 Docs
drwxr-xr-x    2 tim tim 4096 2005-05-14 01:57 Downloads
drwxr-xr-x    3 tim tim 4096 2005-05-13 11:27 Firefox
drwxr-xr-x    2 tim tim 4096 1969-12-31 18:00 Guitars
drwxr-xr-x    3 tim tim 4096 1969-12-31 18:00 Icons
drwxr-xr-x    2 tim tim 4096 2005-05-14 12:21 IP Cop
drwxr-xr-x    3 tim tim 4096 1969-12-31 18:00 KDE 3.4
drwxr-xr-x    2 tim tim 4096 1969-12-31 18:00 Linux
drwxr-xr-x    2 tim tim 4096 2005-05-14 14:04 Menu Editor
drwxr-xr-x    4 tim tim 4096 2005-05-14 03:56 MP3's
drwxr-xr-x  164 tim tim 8192 2005-05-14 03:53 Pictures
drwxr-xr--    2 tim tim 4096 2005-05-14 11:59 Screen Shots
drwxr-xr-x    2 tim tim 4096 2005-05-14 16:29 SMEG
drwxr-xr-x    3 tim tim 4096 1969-12-31 18:00 Super Karamba
drwxr-xr-x    3 tim tim 4096 2005-05-13 11:56 Thunderbird
drwxr-xr-x    3 tim tim 4096 2005-05-14 01:58 Ubuntu
root@ngundo:/home/tim #


Here is what I tried so far:

root@ngundo:/home/tim # cd Menu Editor
bash: cd: Menu: No such file or directory
root@ngundo:/home/tim #
root@ngundo:/home/tim #
root@ngundo:/home/tim # cd/home/tim/Menu Editor
bash: cd/home/tim/Menu: No such file or directory
root@ngundo:/home/tim #
root@ngundo:/home/tim #
root@ngundo:/home/tim # ls -l /home/tim/Menu Editor
ls: /home/tim/Menu: No such file or directory
ls: Editor: No such file or directory
root@ngundo:/home/tim # cd Menu
bash: cd: Menu: No such file or directory
root@ngundo:/home/tim # cd /Menu
bash: cd: /Menu: No such file or directory
root@ngundo:/home/tim # cd /Menu Editor
bash: cd: /Menu: No such file or directory
root@ngundo:/home/tim #

Does this make any sense?

Thanks,
Tim

---

### Post by bored2k on 2005-05-14
[QUOTE=b06tmm]Thanks!!!

I've learned a lot in these four weeks but still have much to learn...I used to be a DOS junkie and didn't realize how lazy Windows had made me until recently when I embraced Linux exclusively.

To my terminal problem...

No matter how I type the folder name (Menu Editor) I cannot navagate to it!  See example:

root@ngundo:/home/tim # ls -l
total 80
drwxr-xr-x    3 tim tim 4096 1969-12-31 18:00 Cool Pics
drwxr-xr-x    2 tim tim 4096 2005-05-14 16:08 Desktop
drwxr-xr-x    3 tim tim 4096 1969-12-31 18:00 Docs
drwxr-xr-x    2 tim tim 4096 2005-05-14 01:57 Downloads
drwxr-xr-x    3 tim tim 4096 2005-05-13 11:27 Firefox
drwxr-xr-x    2 tim tim 4096 1969-12-31 18:00 Guitars
drwxr-xr-x    3 tim tim 4096 1969-12-31 18:00 Icons
drwxr-xr-x    2 tim tim 4096 2005-05-14 12:21 IP Cop
drwxr-xr-x    3 tim tim 4096 1969-12-31 18:00 KDE 3.4
drwxr-xr-x    2 tim tim 4096 1969-12-31 18:00 Linux
drwxr-xr-x    2 tim tim 4096 2005-05-14 14:04 Menu Editor
drwxr-xr-x    4 tim tim 4096 2005-05-14 03:56 MP3's
drwxr-xr-x  164 tim tim 8192 2005-05-14 03:53 Pictures
drwxr-xr--    2 tim tim 4096 2005-05-14 11:59 Screen Shots
drwxr-xr-x    2 tim tim 4096 2005-05-14 16:29 SMEG
drwxr-xr-x    3 tim tim 4096 1969-12-31 18:00 Super Karamba
drwxr-xr-x    3 tim tim 4096 2005-05-13 11:56 Thunderbird
drwxr-xr-x    3 tim tim 4096 2005-05-14 01:58 Ubuntu
root@ngundo:/home/tim #


Here is what I tried so far:

root@ngundo:/home/tim # cd Menu Editor
bash: cd: Menu: No such file or directory
root@ngundo:/home/tim #
root@ngundo:/home/tim #
root@ngundo:/home/tim # cd/home/tim/Menu Editor
bash: cd/home/tim/Menu: No such file or directory
root@ngundo:/home/tim #
root@ngundo:/home/tim #
root@ngundo:/home/tim # ls -l /home/tim/Menu Editor
ls: /home/tim/Menu: No such file or directory
ls: Editor: No such file or directory
root@ngundo:/home/tim # cd Menu
bash: cd: Menu: No such file or directory
root@ngundo:/home/tim # cd /Menu
bash: cd: /Menu: No such file or directory
root@ngundo:/home/tim # cd /Menu Editor
bash: cd: /Menu: No such file or directory
root@ngundo:/home/tim #

Does this make any sense?

Thanks,
Tim[/QUOTE]
 Dude you can't do it that way. Since the dir has spaces in between, its
```
cd Menu\ Editor/
```.

It's easier if you just
```
cd "Menu Editor"
```
BTW you know there's TAB completion right ? you could "cd Menu[press TAB]" for the dir to complete itself ;).

---

### Post by Ali_Baba on 2005-05-14
Thanks for that cd " " command.Didnt know that,thats much easier that way :) Much to learn about Linux.

---

### Post by bvc on 2005-05-15
why such complicated, long scripts, I wonder? this does the same
```
#!/bin/bash
cd $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
gnome-terminal
```
;-)

---

### Post by ow50 on 2005-05-15
[QUOTE=bvc]why such complicated, long scripts, I wonder? this does the same
```
#!/bin/bash
cd $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
gnome-terminal
```
;-)[/QUOTE]
Does that work in folders considered special by nautilus? Meaning at least Desktop, Trash and Computer. That python script I posted has always worked for me, others haven't. Also the python script will work differently based on whether a folder is selected in nautilus or just clicking in the background.

---

### Post by bvc on 2005-05-15
Nothing on the desktop, if that is what you mean. You have to be in nautilus. You have to click on a folder, not just the background in a folder. That could be useful. Thanks for explaining the advantage as I didn't read the scripts. I'll give it a whirl.

---

### Post by elgalloloco on 2007-10-27
> **jobezone said:**
> There is a huge colection of nautilus scripts here:
[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/) 
[list=1]
[*]Open this one: [http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Open%20terminal/gnome2-terminal-here](http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Open%20terminal/gnome2-terminal-here)
[*]save it as a file called "open_terminal"(the choice of name is yours), and place it inside this directory: ~/.gnome2/nautilus-scripts/ (~ allways points to your home directory)
[*]right-click on the file, open the Properties dialog, and make it executable (in the permissions tab)
[*]you can now right-click on any nautilus window and choose Scripts->open_terminal
[/list]

SUPER MEGA thanx for this!

---

