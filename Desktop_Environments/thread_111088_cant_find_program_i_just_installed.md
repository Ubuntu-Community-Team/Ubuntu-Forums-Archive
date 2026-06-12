---
title: "cant find program i just installed"
date: 2006-01-01
forum: Desktop Environments
---

### Post by PapaWiskas on 2006-01-01
please forgive me...but I am really new to Linux.  I downloaded dvdrip via synaptic...but it is not in my programs list under sound and video.

I know this sounds pathetic, but I have been dependent on Windows for so long, I really am trying to learn.
How do I search for this program, and put it in my menu so I can just click on the icon to activate it.
I have no clue where Linux puts things, I do intend to learn, but I am just trying to get things that I normally do in Windows, up and running in Linux.  Then I will dive under the hood afterwards.

Thanks everyone....

---

### Post by Omnios on 2006-01-01
A little newbie tip I figured out a long time ago is to find the package in synaptic right click it and look at installed files. 

 There will be a list of every thing it installed. There will be the bin in the bin section but I usualy copy and past the menu file into run and it opens a text file with the start command which you can then make a menue item with if you have to.

 Menu is a bit tricky sometimes I found a program shows up after restarting or refreshing the menu or restarting Xserver. 

 The main proglem is a new menue standard that is not always followed by older programs there for the program does not show up in menu.

---

### Post by kaamos on 2006-01-01
You can probably start the program from the terminal by typing "dvdrip".

One way to find out is to right click on the package is synaptic and choose properties and then look for installed files that are in /usr/bin or /usr/local/bin. The names of these files can be used as commads. It's usually the name of the program.

You can then use the menu editor the create a menu entry.

Luckily, most of the graphical programs automatically appear in the menu.. Anyway, hope this answered your question.

---

### Post by Nomearod on 2006-01-01
I didn't knew about that "bin" thing. Thanks ppl.

Btw, to lanuch a program you could try Alt +  F2  and then write the program's name. But remember that the name is case sensive.

---

### Post by Lord Illidan on 2006-01-01
In a terminal, entering the first few letters of the program, and then press TAB will complete the word or give you a list. For example, 

```
$ dvd [TAB]
dvd-ram-control   [COLOR=Red]_**dvdrip**_[/COLOR]            dvdrip-master     dvd+rw-booktype   dvd+rw-format     dvd+rw-mediainfo
```

---

### Post by PapaWiskas on 2006-01-01
Thank you so much for all your help.....I got it on the menu now.
Now to figure out how to use it.

Thanks for your time, I really appreciate it.

---

### Post by qferret on 2006-01-01
Omnios' approach is far easier in this case, but......

The "locate" command is invaluable to me quite often.

To set it up, simply type "sudo locate -u" in a terminal window.

It will create a searchable "database" of sorts.

After this command finishes, you can simply type "locate <stringToFind>" in a terminal window to list all files and folders containing that string.

Example: locate java 

The above would list all files and folders containing "java".

Note: You need to run "sudo locate -u" periodically to "refresh" the database.

---

### Post by Omnios on 2006-01-01
[QUOTE=qferret]Omnios' approach is far easier in this case, but......

The "locate" command is invaluable to me quite often.

To set it up, simply type "sudo locate -u" in a terminal window.

It will create a searchable "database" of sorts.

After this command finishes, you can simply type "locate <stringToFind>" in a terminal window to list all files and folders containing that string.

Example: locate java 

The above would list all files and folders containing "java".

Note: You need to run "sudo locate -u" periodically to "refresh" the database.[/QUOTE]

 Cool learnt something new and very usefull

---

