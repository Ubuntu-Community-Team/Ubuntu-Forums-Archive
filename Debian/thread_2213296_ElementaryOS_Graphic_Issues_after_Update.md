---
title: "ElementaryOS Graphic Issues after Update"
date: 2014-03-25
forum: Debian
---

### Post by mauro4 on 2014-03-25
[COLOR=#252C2F][FONT=Helvetica]Hey guys, i am new to Ubuntu in general, so go easy on me.[/FONT][/COLOR]
[COLOR=#252C2F][FONT=Helvetica]I made an update last friday on my thinkpad running with elementaryOS everything worked fine, then today i tried to start up my computer, the elementaryOS logo took a bit longer than usual to disappear, and when my computer finally turned on the ui was very slow, my mouse cursor didint showed, and when i used a shortcut to open something it showed only as a black cross, [/FONT][/COLOR]
[COLOR=#252C2F][FONT=Helvetica]You can see here that theres a strange grey bar around the icons nad the mouse is missing: [/FONT][/COLOR][http://imgur.com/Y0OHySH](http://imgur.com/Y0OHySH)
[COLOR=#252C2F][FONT=Helvetica]If i open the terminal with short cut my mouse stays like this: [/FONT][/COLOR][http://imgur.com/Owo6wCN](http://imgur.com/Owo6wCN)
[COLOR=#252C2F][FONT=Helvetica]I think its a graphic card issue, but i have no idea what driver im using or how to remove it and install other[/FONT][/COLOR]

---

### Post by oldfred on 2014-03-26
Moved to Other OS since Elementary. 

Know nothing about Elementary or its video issues.

---

### Post by Stinger on 2014-03-27
Hi mauro4
Welcome to the Ubuntu forums. :)

I see you got some real trouble, can you still operate the terminal, type some commands I mean ?
If you can, try this one to reconfigure the x-server:
```
sudo dpkg-reconfigure xserver-xorg
```
And reboot to see if it has any effect.

Also I need a little info regarding your PC, make and model, hardware specs. etc.

---

### Post by mauro4 on 2014-03-27
> **Stinger said:**
> Hi mauro4
Welcome to the Ubuntu forums. :)

I see you got some real trouble, can you still operate the terminal, type some commands I mean ?
If you can, try this one to reconfigure the x-server:
```
sudo dpkg-reconfigure xserver-xorg
```
And reboot to see if it has any effect.

Also I need a little info regarding your PC, make and model, hardware specs. etc.
I can open the terminal with the short cuts
I did that and nothing happened the problem remains, im using a Lenovo Thinkpad x220
[TABLE="class: geekbox, width: 770"]
[TR="class: odd"]
[TD]Processor[/TD]
[TD]2.5GHz Intel Core i5-2520M[/TD]
[/TR]
[TR="class: even"]
[TD]Memory[/TD]
[TD]4GB, 1,333MHz DDR3[/TD]
[/TR]
[TR="class: odd"]
[TD]Hard drive[/TD]
[TD]320GB 5,400rpm[/TD]
[/TR]
[TR="class: even"]
[TD]Chipset[/TD]
[TD]Mobile Intel HM55[/TD]
[/TR]
[TR="class: odd"]
[TD]Graphics[/TD]
[TD]Intel HD 3000[/TD]
[/TR]
[TR="class: even"]
[TD]Operating system[/TD]
[TD][Windows 7]("http://www.cnet.com/products/microsoft-windows-7/") Professional (64-bit)[/TD]
[/TR]
[TR="class: odd"]
[TD]Dimensions (WD)[/TD]
[TD]12.0x8.3 inches[/TD]
[/TR]
[TR="class: even"]
[TD]Height[/TD]
[TD]0.8 - 1.4 inches[/TD]
[/TR]
[TR="class: odd"]
[TD]Screen size (diagonal)[/TD]
[TD]12.5 inches[/TD]
[/TR]
[TR="class: even"]
[TD]System weight / Weight with AC adapter[/TD]
[TD]3.3 pounds/4.0 pounds[/TD]
[/TR]
[TR="class: odd"]
[TD]Category[/TD]
[TD]Ultraportable[/TD]
[/TR]
[/TABLE]

---

### Post by mauro4 on 2014-03-27
Hello, i found the answer in another forum, you can see it here
[http://www.reddit.com/r/elementaryos/comments/21dfal/problems_after_update_help/](http://www.reddit.com/r/elementaryos/comments/21dfal/problems_after_update_help/)

---

### Post by oldfred on 2014-03-27
Another thread on Elementary video type issues.

[http://ubuntuforums.org/showthread.php?t=2213023](http://ubuntuforums.org/showthread.php?t=2213023)

---

### Post by Stinger on 2014-03-27
Ok thanks :)
Try runnig
```
glxinfo
```
You might have to install the mesa-utils package but it will tell you how.

Don't post the result but see if this line is present
> Gen6+ requires Kernel 3.6 or later.

To see what kernel you use run
```
uname -r
```

---

### Post by Stinger on 2014-03-27
Didn't see you found the answer already :)
So you can forget my post above.

You can use the LTS Enablement stack to solve your problem
```
sudo apt-get install --install-recommends linux-generic-lts-saucy xserver-xorg-lts-saucy libgl1-mesa-glx-lts-saucy
```
Remember to reboot to activate the new kernel and x-server.
[LTS Enablement Stack page]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

---

