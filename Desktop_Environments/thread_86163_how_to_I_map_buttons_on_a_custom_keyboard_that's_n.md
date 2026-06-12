---
title: "how to I map buttons on a custom keyboard that's not a supported option"
date: 2005-11-04
forum: Desktop Environments
---

### Post by teaker1s on 2005-11-04
could someone tell me how to map the extra keys on the keyboard- I did find this but I'm not too sure if there is an easier way
[URL="http://linux.seindal.dk/item65.html"]
http://linux.seindal.dk/item65.html[/URL]

---

### Post by ultima2k on 2005-11-04
I use the package "hotkeys" to use special keys on my Logitech keyboard and it works perfectly, maybe it supports your keyboard too :)

---

### Post by teaker1s on 2005-11-04
okay I've the packages installed for hotkeys run it and i'm still not getting all multimedia keys detected

any more Ideas please

---

### Post by teaker1s on 2005-11-04
/usr/X11R6/lib/X11/xkb appears to hold keyboard settings etc

can enyone suggest an app that will show output when key is pushed?

---

### Post by Kyral on 2005-11-04
I got lazy and manually mapped them using the Keyboard Shortcuts in the GNOME Preferences menu

(though I use XFCE now ;)

---

### Post by teaker1s on 2005-11-04
problem I have is there is no output detected on some keys for shortcuts and from
looking at var/log/messages I can see the keys as unknown but with an identifying output,
 so I guess I need to use them and then asign them so I'll write a wilki page when i figure it out

eg.
Nov  4 21:05:47 localhost kernel: [4300089.831000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known. is a currently dead button
will try to setkeycodes in terminal when I am sure I'm not going to muck a set key up allegedly keycode can  
be from 1-127 but I think it has to match hex or it wont work

---

### Post by teaker1s on 2005-11-04
right I've 

Nov 4 21:05:47 localhost kernel: [4300089.831000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known

next

teaker1s@ubuntu:~$ sudo getkeycodes
Password:
Plain scancodes xx (hex) versus keycodes (dec)
for 1-83 (0x01-0x53) scancode equals keycode

 0x50:   80  81  82  83  84   0  86  87
 0x58:   88 117   0   0  95   0 184 185
 0x60:    0   0   0   0   0   0   0   0
 0x68:    0   0   0   0   0   0   0   0
 0x70:   93   0   0  89   0   0  85  91
 0x78:   90  92   0  94   0 124 121   0

Escaped scancodes e0 xx (hex)

e0 00:    0   0   0   0   0   0   0   0
e0 08:    0   0   0   0   0   0   0   0
e0 10:  165   0   0   0   0   0   0   0
e0 18:    0 163   0   0  96  97   0   0
e0 20:  113 140 164   0 166   0   0   0
e0 28:    0   0   0   0   0   0 114   0
e0 30:  115   0 150   0   0  98 255  99
e0 38:  100   0   0   0   0   0   0   0
e0 40:    0   0   0   0   0 119 119 102
e0 48:  103 104   0 105 112 106 118 107
e0 50:  108 109 110 111   0   0   0   0
e0 58:    0   0   0 125 126 127 116 142
e0 60:    0   0   0 143   0 217 156 173
e0 68:  128 159 158 157 155 226   0   0
e0 70:    0   0   0   0   0   0   0   0
e0 78:    0   0   0   0   0   0   0   0

so I try as I've seen online

teaker1s@ubuntu:~$ setkeycodes e02a 165
Couldnt get a file descriptor referring to the console
teaker1s@ubuntu:~$ setkeycodes e02a<165>
bash: syntax error near unexpected token `165'
teaker1s@ubuntu:~$
 
any Ideas?

please

---

### Post by teaker1s on 2005-11-04
I can now make buttons work until reboot any Ideas how to create a new keyboard entry in gnome for my model?

---

### Post by daller on 2005-11-07
[QUOTE=teaker1s]

teaker1s@ubuntu:~$ setkeycodes e02a 165
 Couldnt get a file descriptor referring to the console
 teaker1s@ubuntu:~$ setkeycodes e02a<165>
 bash: syntax error near unexpected token `165'
 teaker1s@ubuntu:~$

[/QUOTE]

You need superuser priviledges!

sudo setkeycodes e02a 165

...Is it a HP pavilion 4400, or why did you post a link in my thread?

---

### Post by teaker1s on 2005-11-08
I posted a link in your thread as I can see that any missing keys can be made to work by using 'dmsg' and setcodes to make the key known and running a script. I've found out how to asign gnome new unlisted shortcut keys also.

The base of the problem I believe to sort out your key issues and mine is someone to explain how to configure xorg xkb for a new keyboard.
I have got to the point where I have my keyboard listed but when I select it for some reason Its not calling the correct keycode and symbols for the keyboard if I can figure it out the solution will allow you to create a new keyboard layout to support your keyboard.

---

