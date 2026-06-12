---
title: "Problem with terminal"
date: 2009-04-08
forum: General Help
---

### Post by maruf10 on 2009-04-08
[I]hello
i have installed ubuntu 8.04.....but my terminal is not working properly....
it is printing invalid character when "enter"/"backspace" is pressed....how can i fix it..??.i have no internet connection....
thanks in advance[/I]

---

### Post by PreviousN on 2009-04-08
I think many may be confused with your question. I am. What exactly do you mean by invalid character?

But, anyways, you could try restarting the computer and choosing system maintenance from GRUB when you boot. This will give you access to a root console. See if it happens there. If so, it could be a problem with your keyboard.

---

### Post by maruf10 on 2009-04-08
[I]its just printing `D` when enter is pressed...
backspace is not working.....

one of my friends having internet connection have solved the same problem using "sudo apt-get install vim-full"

without having net...how can i solve it...???[/I]

---

### Post by PreviousN on 2009-04-08
Never heard of that problem. But if you say that installing vim-full fixes the problem (I don't see why it would, vim is a command line text editor), then here's how to install it without having an internet connection. 

Option 1, using only install cd, and GUI:
* Insert the cd you used to install ubuntu. Open System --> Administration --> Software sources --> check "installable from cd"
* Open system --> Administration --> Synaptic package manager --> search for vim-full, check, then hit apply.

Option 2, using a friend's internet access:
* Have a friend download the vim-full package from ubuntu's repositories. Here's a link: [http://packages.ubuntu.com/intrepid/vim-full](http://packages.ubuntu.com/intrepid/vim-full)
* Put that on a flash drive, copy to your computer, and double click on the file. Or, using a terminal, type "dpkg -i vim-full.deb" (or something like that, use tab completion). 

I'm still confused as to what may be causing your problem. It sounds *very* weird. Since you JUST installed the os, I can't think of any reason why this would be happening. Did you try restarting and booting via grub into the system recovery mode?

---

### Post by KeyserSoze93 on 2009-04-09
Just a hunch, but try typing:

```
TERM=xterm
``` followed my Control-M

This should make sure you have the right terminal type set, so you keys and escape codes are recognized right, and Control-M should do the same as return.

---

### Post by lvleph on 2009-04-09
The only way I can see vim-full fixing this issue, is if you are not describing the issue correctly. The vi that is preinstalled on Ubuntu does not have the backspace character mapped correctly. I have never had the same issue with enter. However, this can be fixed by installing vim-full. But none of this has anything to do with terminal except that vim is run through the terminal.

---

