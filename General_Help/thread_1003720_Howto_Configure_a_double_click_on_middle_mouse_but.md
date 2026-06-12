---
title: "Howto: Configure a double click on middle mouse button"
date: 2008-12-06
forum: General Help
---

### Post by quadra on 2008-12-06
This is a **short** guide on how to configure your mouse such that the middle button (scroll wheel) generates a double click.

[LIST]
[*]**Install packages xautomation and xbindkeys** (download size only ~ 30 kB each; use Synaptic package manager or “sudo apt-get install xautomation” / “...xbindkeys”)

[*]**Create the file “.xbindkeysrc”** in your home directory (gedit ~/.xbindkeysrc)

[*]**Paste the following two lines** (2 stands for middle mouse button, at both occurrences), save the file:
[/LIST]

```
"/usr/bin/xte 'mouseup 2' 'mouseclick 1' 'mouseclick 1' &"
b:2
```


[LIST]
[*]To **test the setup** and get diagnostic info, type “xbindkeys -n -v” in a terminal. Ctrl+C to exit.

[*]To **start xbindkeys every time you log on**: System - Preferences - Sessions - Add - “xbindkeys”, command = xbindkeys
[/LIST]

---

### Post by quadra on 2008-12-06
Some explanations:

*xbindkeys* is a tool which grabs keys and mouse events. *xautomation* includes the command-line tool *xte* which we use to send input to the kernel. Our configuration file specifies what we send (a double click) when the button is clicked.

This seems to be the easiest solution at present. The former solution using btnx does no longer run in Ubuntu 8.x; and just editing xorg.conf does not seem to make the double click possible. (Please let us know if you have better solutions...!!)

For a more extensive guide, check **[http://ubuntuforums.org/showthread.php?t=316441](http://ubuntuforums.org/showthread.php?t=316441)** (that's where this post is inspired from;))

If you don't like this kind of command-line solutions, vote for the idea to enhance this here: 
**[http://brainstorm.ubuntu.com/idea/120/](http://brainstorm.ubuntu.com/idea/120/)**

---

### Post by sergeych on 2011-09-08
Tried it with 10.04, didnt work. xbindkeys reported that it is likely unable to capture all required events. well enough, it really wasnt. any other ways to simulate double click?

---

### Post by quadra on 2011-09-09
Thanks for pointing me to this, the guide was written for Ubuntu 8.04, and actually I encounter the same issue as you when testing it on 10.04. Sorry but I can't figure out the reason right now. Some incompatible package apparently.

---

### Post by stinkeye on 2011-09-09
> **sergeych said:**
> Tried it with 10.04, didnt work. xbindkeys reported that it is likely unable to capture all required events. well enough, it really wasnt. any other ways to simulate double click?

You can simulate a double click using the middle button with
easystroke and xdotool.

Use the method shown [**_[COLOR="DarkRed"]here[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10495426&postcount=11") to assign a mouse button to a command.
The command to use is
```
xdotool click --repeat 2 1
```


Install easystroke and xdotool
```
sudo apt-get install easystroke xdotool
```


[B]***The default gesture button for easystroke is the middle button.
I changed this to the right button.[/B]

---

### Post by pansmanse on 2011-09-11
Thanks, Stinkeye, this is very helpful.  However I can't make it work.  Easystroke recognises my mouse button, but nothing happens.  Either  I am misunderstanding your code (and the documentation at [http://www.semicomplete.com/projects/xdotool/xdotool.xhtml](http://www.semicomplete.com/projects/xdotool/xdotool.xhtml)), or xdotool does not recognise the 'repeat' option.  I have tried entering 'xdotool click --repeat 2 1' directly in a terminal and get this message 'usage: click <button> // You specified the wrong number of args.'

---

### Post by stinkeye on 2011-09-11
Yep,your right, I did this on my Ubuntu 11.10 install and it appears the **--repeat** option
isn't in previous versions of xdotool.

man page for 11.10 version of xdotool
> click [options] button
 Send a click, that is, a mousedown followed by mouseup for the given button with a short delay between the two (currently 12ms). 

 Buttons generally map this way: Left mouse is 1, middle is 2, right is 3, wheel up is 4, wheel down is 5. 
--clearmodifiers
 Clear modifiers before clicking. See CLEARMODIFIERS below. 
**--repeat REPEAT**
 Specify how many times to click. Default is 1. For a double-click, use '--repeat 2'


This command on Natty will do a double click.
```
xdotool click 1 && xdotool click 1
```

---

### Post by parmenpj on 2012-01-05
Excellent, stinkeye.  Thank you.

---

### Post by rbscairns on 2012-06-28
The instructions in the original post worked perfectly for me inUbuntu 12.04 with my 3-button generic mouse.

Thanks a lot!

PS: I spoke to soon. On reboot, the 3rd button (wheel) double-click did not work. Back to the drawing board.

---

### Post by Elfy on 2012-06-28
Old thread closed.

---

