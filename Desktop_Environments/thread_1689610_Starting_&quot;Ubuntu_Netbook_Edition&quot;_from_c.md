---
title: "Starting &quot;Ubuntu Netbook Edition&quot; from command line"
date: 2011-02-17
forum: Desktop Environments
---

### Post by Semferon on 2011-02-17
Hello.

I have a relatively simple question yet i can't find
answer to it.

I am serching the web for 3 hours straight and still no luck.

My question is how to start .desktop files from command line? 

As far as i can see desktop managers use <sessionname>.desktop
files located in /usr/share/xsessions

and the only difference between gnome.desktop and une.dsektop
is one little annoying key:

for gnome.desktop
X-Ubuntu-Gettext-Domain=gnome-session-2.0
(which is default i guess)

for une.desktop
X-Ubuntu-Gettext-Domain=une-session

when i initiate Xserver and running

```
xxxx@xxxx:~$ gnome-session
```
obviously standard gnome evironment starts

So i need to either communicate
```
X-Ubuntu-Gettext-Domain=une-session
```
to gnome-session which i dont know how to do

or somehow start une.desktop from commandline
which i do not know how to do either...

(Just a remark: i want to start it straight from command line 
without GDM)

Does anybody have any suggestions?

ps: i also tried using
```
xxxx@xxxx:~$ xdg-open /usr/share/xsessions/une.desktop 
```
which decided to open file as text in lynx...

---

### Post by DaithiF on 2011-02-17
.desktop files typically contain an Exec=**something** line where something is what gets executed.  Not always true, as there can be desktop entries which launch URLs for example rather than run commands ... but in your case you should be able to execute whatever that **something** is.

---

### Post by Semferon on 2011-02-17
It's true it does contain exec command but as I said before that exec command is:

Exec=gnome- session

With no options...

It looks something like this...

Name=Ubuntu Netbook Edition
Comment=blahblahbla
Exec=gnome-session
TryExec=gnome-session
X-Ubuntu-Gettext-Domain=une-session

If I change
X-Ubuntu-Gettext-Domain=une-session
To
X-Ubuntu-Gettext-Domain=gnome-session-2.0

Then gdm still calls session Ubuntu Netbook Edition
but starts gnome standard desktop instead...

So the key is communicating 
X-Ubuntu-Gettext-Domain=une-session

To gnome-session during start but how to do that???

Isnt there any command something like 

launch blahblahblah.desktop?
It is so frustrating that I can launch .desktop files in GUI 
but can't do it from command line...

---

### Post by Krytarik on 2011-02-17
You are right, you can't launch *.desktop files from the command-line/console.

Try this command, and of course also the other way around:
```
startx une-session
```

---

