---
title: "[fluxbox] Window placement help needed"
date: 2008-12-02
forum: Desktop Environments
---

### Post by rakris on 2008-12-02
I just installed fluxbox and am happy with it.
But the problem is if I run any program the window appears at the back of any current running program.

I want the newly running windows to be at the front when i run it.

For eg: in terminal I typed gnome-terminal, It opened at the back of current window..I dont want this to work this way..

Fluxnewbie here...:)

---

### Post by kerry_s on 2008-12-02
gnome things do that, try using as little gnome specific programs as possible. for example: xterm, roxterm, rxvt, etc...
sounds like your running the gnome-settings-manager(i think thats what its called) if you are you can only expect it to act like gnome. there are others ways to get the settings you want with out running gnome stuff.

---

### Post by rakris on 2008-12-02
> **kerry_s said:**
> gnome things do that, try using as little gnome specific programs as possible. for example: xterm, roxterm, rxvt, etc...
sounds like your running the gnome-settings-manager(i think thats what its called) if you are you can only expect it to act like gnome. there are others ways to get the settings you want with out running gnome stuff.

No. I use only gnome-terminal because i am used it. No other gtk apps except firefox.

Does this behaviour specific to gnome? I was using gnome before and never faced such issues...

---

### Post by kerry_s on 2008-12-02
> **rakris said:**
> No. I use only gnome-terminal because i am used it. No other gtk apps except firefox.

Does this behaviour specific to gnome? I was using gnome before and never faced such issues...

gnome did that when i used it, but than again i haven't used fluxbox in a long while, it could be a new feature.

gtk is fine, most programs are gtk.

try roxterm, it's ton's better than gnome-terminal, it's faster, lighter, but has all the features like transparency, tabs, smooth fonts, etc.... just select "edit current profile" you can do most things there, like turn off the menu bar and scrollbar, etc....
**sudo apt-get install roxterm**

if you only need simple, than the included xterm, with a little tweaking, works just fine.

i use xterm, i just use larger fonts and a simple title.

---

### Post by rakris on 2008-12-02
Thanks kerry. 

I installed roxterm and liked it. 
But I want to know how did you changed xterm fonts and background?

---

### Post by kerry_s on 2008-12-03
> **rakris said:**
> Thanks kerry. 

I installed roxterm and liked it. 
But I want to know how did you changed xterm fonts and background?

xterm fonts is done by the Xdefaults file, background is the normal color. you can also specify it in the command.
use "man xterm" to learn more
from command line my setting look like this:
**xterm -T "Terminal" -fn 9x15**
if yours is black on white you can reverse it with "-rv"
**xterm -rv -fn 9x15**

xterm is the best when you need to use scripts.
for example i use it for my screen shot shortcut with scrot & xmessage, another program i use a lot.
example, 5 second wait set to ctrl+alt+print:
**xterm -fn 10x20 -g 40x1+300+0 -e scrot -cd 5 %T.png; xmessage "Done" -center -timeout 1 -button , **

---

### Post by rakris on 2008-12-12
Solved.

The fluxbox window placement can be configured using 'configure' menu of fluxbox. OR editing init file(didn't check where it is in init file .yet).

Hey Kerry,
I took your advice and am using xterm. Loving it. I use .Xresources to edit config. 
Thanks :).....

---

### Post by Bradman67 on 2009-03-02
Hello there, 

I have a very similar issue also, all my newly opened programs open below my prominent window. Ive not come to any conclusion and its wearing me out, can you help me? 

Thanks in advance

---

### Post by rakris on 2009-03-03
Did you read my above post?

Check in configure sub menu of fluxbox menu. Dont remember exactly where. I am on Windows rite now.

---

