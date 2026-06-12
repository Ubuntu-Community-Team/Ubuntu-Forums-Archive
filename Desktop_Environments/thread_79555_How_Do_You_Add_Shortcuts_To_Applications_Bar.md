---
title: "How Do You Add Shortcuts To Applications Bar"
date: 2005-10-20
forum: Desktop Environments
---

### Post by rickon on 2005-10-20
Hi all,

I downloaded Opera web browser but am not sure how to add an icon to the applications short cut bar.

All help really appreciated.

Rickon 

Ubuntu newbie.........

---

### Post by mostwanted on 2005-10-20
type smeg in the terminal.

---

### Post by rickon on 2005-10-20
Hi, Thanks for the reply.  I have got so far but still stuck.

Typed in smeg and the menu editor appears, then I selected the Internet section, then add new entry, typed Opera and then hit browse for command.

Not sure what to do next, I downloaded the opera files onto the desktop.  Am I looking for a shortcut.

Sorry to be a pest.

Rickon 

Newbie

---

### Post by Gordonbp531 on 2005-10-20
If it shows in your Applications menu, right-click and choose "Add to Panel".....

---

### Post by rickon on 2005-10-20
Hi, No it doesnt show in the applications panel

Rickon

---

### Post by PuleX on 2005-10-20
You got the opera .deb file, right? 
Did you do: 
[INDENT]sudo dpkg -i path/to/opera85.deb[/INDENT] 

If yes, then by running smeg (also available via Applications > System Tools > Applications Menu Editor ) you can go and add a Opera shortcut. You don't need to browse. In the command field just fill out 'opera' or 'opera %u'. The Opera icon can be found in /usr/share/opera/images/

---

### Post by flyingbrass on 2005-10-20
If you mean you want to add an Opera launcher to the panel, right click on the panel and select "Add to panel."  Then, if Opera already exists in your Applications menu, choose "Application Launcher."  Navigate to Opera and select it.  If Opera isn't in your Applications menu, select "Custom Application Launcher."  The command is simply "opera" without the quotes. You can select an icon in /usr/share/opera/images.

---

### Post by rickon on 2005-10-20
Hi all, I seem to be getting muddled up here.

When I type sudo dpkg -i path/to/opera85.deb  in the terminal window I get:  rickon@ubuntu:~$ sudo dpkg -i path/to/opera85.deb
dpkg: error processing path/to/opera85.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 path/to/opera85.deb
rickon@ubuntu:~$

And I cannot find: Custom Application Launcher in the Menu Editor, sorry about this..........

Rickon

---

### Post by objorkum on 2005-10-20
First of all, do you actually have Opera installed?

Then Opera should start if you type "opera" in a terminal.

If you have it installed, you can add it to the meny by using the "Applications Menu Editor" > New Entry > Name: Opera - Command: opera (case sensitive)

---

### Post by iimess on 2005-10-20
[QUOTE=rickon]Hi all, I seem to be getting muddled up here.

When I type sudo dpkg -i path/to/opera85.deb  in the terminal window I get:  rickon@ubuntu:~$ sudo dpkg -i path/to/opera85.deb
dpkg: error processing path/to/opera85.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 path/to/opera85.deb
rickon@ubuntu:~$

And I cannot find: Custom Application Launcher in the Menu Editor, sorry about this..........

Rickon[/QUOTE]

1) You downloaded Opera. Did you install it? If no then install it by:
$ cd ~/Desktop
$ sudo dpkg -i *opera_blah.deb*
(note that you need to change that to _your_ downloaded opera file name)

2) To add it to Applications->Internet:
a) Open the menu editor from Applications->System Tools->Applications Menu Editor.
b) Click on Internet on the left.
c) Click New Entry.
d) Give it a name, say "Opera." For command, try "opera." For icon, click on the big rectangle and browse to (left) File System, (right) usr, share, opera, images, and pick whatever you like.

(oops, I just repeated what everyone has said!)

---

### Post by rickon on 2005-10-20
Hi, I am still rather stuck.  I have tried tutorials and FAQ, I think I am trying to walk before I can run if you see what I mean.

I tried your instructions but get the following error message:

rickon@ubuntu:~$ cd ~/Desktop
rickon@ubuntu:~/Desktop$ sudo dpkg -iopera-8.50-20050916.6-shared-qt.i386-en
Password:
dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
rickon@ubuntu:~/Desktop$

I have a folder on my desktop that has the following file name on it:

opera-8.50-20050916.6-shared-qt.i386-en

Do you think I should start again from scratch or????

Rickon

---

### Post by emendelson on 2005-10-20
space between -i and opera...etc. NOT:

rickon@ubuntu:~/Desktop$ sudo dpkg -iopera-8.50-20050916.6-shared-qt.i386-en

BUT

rickon@ubuntu:~/Desktop$ sudo dpkg -i opera-8.50-20050916.6-shared-qt.i386-en

Did you see the space between -i and opera-8..... ? That's the key.

---

### Post by rickon on 2005-10-21
Hi everyone,

Yahoo... I got Opera to work thanks to you all.  And it is now a shortcut in my Applications bar.

I am really enjoying using Ubuntu it works great, however I think I need to read more about how it all works the terminal etc.  I have looked at the user guide etc.  In what order do you think I should start reading/learning to get a good knowledge of Ubuntu...or should I learn about Linux in general first?

Regards

Rickon

---

### Post by nils234 on 2008-01-09
I wanted to do the same thing, however I found smeg isn't in ubuntu anymore. After running apt-get install smeg, it gave me " selecting alacarte instead, alacarte allready latest version ". I ran alacarte and it was exactly what I needed. I guess the program has been renamed over the years. I know this is an ancient thread, but I got here through google and I guess this might also happen to other people. So, replace smeg by alacarte ;)

---

