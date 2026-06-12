---
title: "gnome-terminal: search and select all"
date: 2007-10-27
forum: Desktop Environments
---

### Post by mikec13 on 2007-10-27
There are a few things with gnome-terminal that frustrate me, so I figured I'd throw them out here and see if there are any solutions that I'm unaware of.

First, I'd like the ability to do a find on the data that's in the terminal.  For example, if I'm looking at my firewall access list, which is fairly large, I'd like to do a find based on ip address to check if a certain entry exists.

The second issue kind of plays off of the first one.  Since I can't do a find, I copy and paste the whole access list into a text editor so that I can do the find from there.  However, I don't see a way to "select all".  Instead I drag my house and highlight everything to the top of the buffer.  Is there any better way to do this?

---

### Post by ecschiel on 2007-10-31
I'm not sure what's your problem, so if you can post the command you use to display the list would be nice.
Maybe this could help you. For example if you use iptables you can do something like this:
```

sudo iptables -L | grep 192.168.1.10

```
Change the IP for something more usefull for you. Again, I'm not sure what's your problem, so if you can light me maybe can help you better.

---

### Post by luke2760 on 2007-10-31
Generally, the best solution probably a grep, as he suggested. It's a lot faster than trying to do some sort of find command in the gnome part of the terminal, and it also works equally well without X (useful when gnome goes down.)

If you really want to look at it in a text-editor like environment, pipe it into less or more. i.e.

sudo iptables -L | less

Will put the output into less, which takes plenty of emacs commands, most vi commands, and the obvious like pageup/down, etc. 

If you're not familiar with vi search:

Hit ' / ' to activate search (think of as ctrl+f)
Hit 'n' to cycle to the next option.
Hit 'N' to cycle backwards.

If you want to work with the output, redirect it into a file and open that file.

sudo iptables -L > iptables.out
emacs iptables.out
(or vi, or gedit, or nano, or oowriter, whatever)

---

### Post by mikec13 on 2007-10-31
Thanks for the responses, guys.  I do use grep or searches within vi/less when I'm doing stuff from my local computer.  However, my problem is when I'm ssh-ed into one of my PIX firewalls (or something like that).  Some of these devices have grep-like functionality built in, but sometimes they don't.  

When I'm using the terminal in my OSX box, I can just do a find right in the terminal.  When I'm using putty, I can do a copy-all and put it into a text editor and do a find or just quickly copy off the config file.  But when I'm in gnome-terminal, the only way I see that I can do it is to scroll and highlight.

Anyways, thanks again for the responses!

---

### Post by bingoUV on 2007-11-01
It may not suit you, but why don't you try mrxvt? It is much faster, and has a very useful built in short cut. Press ctrl / , and it opens the whole current tab in vim in a new tab. From here you can search all you want. Quit this vim, and the newly opened tab vanishes.

---

