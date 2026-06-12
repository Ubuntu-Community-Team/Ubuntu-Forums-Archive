---
title: "some small problems"
date: 2006-06-21
forum: Desktop Environments
---

### Post by nibbo on 2006-06-21
I have some problems that i would love to get solved as soon as possible (maby i will update this thread if i get more of them).

1. I cant get the button Alt Gr to work as it uses to in windows. That means that i cant write some special characters. Is there a sulotion to this?

2. Sometimes i restart X when typing. It happens when writing capital letters.  So i figured it had to do with som Shift combination. Is there a way to prevent this from happening?

//nibbo

---

### Post by rowanparker on 2006-06-21
1. Not all Windows shortcuts work in Ubuntu, although some do (Alt+F4). Google around, see what you can find.
2. Pressing Ctrl+Alt+Backspace will restart X. This can be changed, also google around.

Rowan.

---

### Post by nibbo on 2006-06-21
[QUOTE=rowanparker]1. Not all Windows shortcuts work in Ubuntu, although some do (Alt+F4). Google around, see what you can find.
2. Pressing Ctrl+Alt+Backspace will restart X. This can be changed, also google around.

Rowan.[/QUOTE]

1. no i do not mean those shortcuts. On the swedish keyboards there are like symbols to the right of the numbers. To write them you have to press the button "Alt Gr". I cant write those :/

2. Tested some combinations and apperently "Shift" + "Backspase" makes X restart to... but ill google that one...

---

### Post by rowanparker on 2006-06-22
1. Erm, maybe if somebody who uses a language other than English can explain how to do thoe characters.
2. Cool, didn't know that.

---

### Post by 3zrael on 2006-06-22
It sounds like a not properly configured keyboard...
Have you checked your xorg.conf ?

---

### Post by nibbo on 2006-06-22
[QUOTE=3zrael]It sounds like a not properly configured keyboard...
Have you checked your xorg.conf ?[/QUOTE]

Actually i solved both problems with the command
```
xmodmap /usr/share/xmodmap/xmodmap.<language>
```
and changed  <language> to "se"

[Found the tip here ]("http://www.fedoraforum.org/forum/showthread.php?t=105054")

---

### Post by rowanparker on 2006-06-22
Glad you got it sorted.

Rowan.

---

### Post by nibbo on 2006-06-22
New problem... I am trying to start Stepmania but i get a error saying somthing about direct render not being available and that i have to get the newest drivers.

I have a Radeon x800 card.  have installed the xorg-fglrx-driver or whaterver they are called. I added it in the /etc/modules and in xorg.conf

Is there somthing i have missed?

---

### Post by nibbo on 2006-06-22
Another problem:
Trying to get linux dc++ to work. Getting the following error:

nibbo@nibbo:~/linuxdcpp$ ./ldcpp
Loading: Hash database
Loading: Shared Files
Loading: Download Queue

(ldcpp:7072): libglade-WARNING **: could not find glade file '/usr/local/share/ldcpp/glade/mainwindow.glade'
Error: Missing required glade file: /usr/local/share/ldcpp/glade/mainwindow.glade

Anyone?

---

### Post by rowanparker on 2006-06-22
You might get better luck posting a new thread on it.

---

### Post by 3zrael on 2006-06-23
Could you post the output of fglrxinfo?

---

### Post by nibbo on 2006-07-21
[QUOTE=3zrael;1172251]Could you post the output of fglrxinfo?[/QUOT

Error: unable to open display :0


oops... dosent look too good... :(

---

