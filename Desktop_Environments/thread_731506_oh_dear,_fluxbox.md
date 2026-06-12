---
title: "oh dear, fluxbox"
date: 2008-03-21
forum: Desktop Environments
---

### Post by employeeno5 on 2008-03-21
So I like the looks of fluxbox. 

Ubuntu is my first distro. I've been playing with more distros and learning allot about Linux in the past six months. I had not used fluxbox on any though. 
So I decided to install fluxbox on Ubuntu 7.10.  I installed from the repositories and logged out and logged back in under a fluxbox session.

All I got was a blank desktop with a tool bar. That's ok. I was expecting that. What I wasn't expecting was not being unable to bring up any menu of any kind. 

Clicking or right-clicking anywhere on the desktop did not bring up any little menu. No clicking on the tool bar did anything. A right click on the tool bar brought up the tool bar options. The tool bar options were the only response I got out of the desktop.

I couldn't figure out any way that I could have opened any kind of file or program without knowing something like a pre-set hotkey or something wacky like that.
I couldn't even figure out how to open a terminal. 

What am I doing wrong? How can I get started? Even just pointing me towards getting a terminal running would be enough and I'm sure I could work things out eventually from there. 
Right now though, I couldn't even logout, I had to hard powerdown my computer.

Please help. I've searched around and from what I've read and from what I've seen of fluxbox on other computers, I thought that I should be getting some kind menu when I click my mouse over the desktop. I guess I was wrong and am in need of a little help.

---

### Post by aysiu on 2008-03-21
This is why I recommend IceWM. My impression is that Fluxbox is for more advanced users than me.

---

### Post by FuturePilot on 2008-03-21
IceWM is very nice. It's minimalistic but very usable at the same time. I've always found Fluxbox too confusing for me.

But if you want to get a menu in Fluxbox
```
sudo apt-get install menu
sudo update-menu
```

---

### Post by employeeno5 on 2008-03-21
I will check out ice as well, however I'm still interested in learning to use fluxbox. I'm not looking for something to just work, I'm able and very willing to learn even if it's a challenge. I just do not know where to begin.
 My reading prior to trying it out led me to believe that I should at least get some kind of menu when I click my mouse. I get no response. 
In fact I checked out a how to on these forums for new fluxbox users about adding things to your menu and learning to customize certain config files, etc, yet even that seemed to be working off of the assumption that certain basic things like a menu of some kind were already in place. 

A terminal is all I'm asking for.

Oh, hi future pilot, I missed your reponse while writing the above.
Thanks for the info, but I can't even type in the install commands given that there's no apparent way for me to even open a terminal. Thank you though.

---

### Post by herbster on 2008-03-21
Seriously?

[http://www.google.ca/search?hl=en&q=fluxbox&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=fluxbox&btnG=Google+Search&meta=)

What you're looking for specifically is right there: [http://fluxbox.sourceforge.net/docbook/en/html/](http://fluxbox.sourceforge.net/docbook/en/html/)

Also, you don't need to power down, you just need to hit CTRL+ALT+BACKSPACE to get back to GDM and log in to Gnome or whatnot.

Been using fluxbox for quite some time, it's by miles my favourite WM. I can't say I consider myself "advanced" :)

---

### Post by Brunellus on 2008-03-21
See my signature for a link to the ubuntu fluxbox howto.

---

### Post by p_quarles on 2008-03-21
> **aysiu said:**
> This is why I recommend IceWM. My impression is that Fluxbox is for more advanced users than me.
But this behavior is not how Fluxbox was designed. It's one of two known flaws that make many users find it more difficult than it actually is.

@employeeno5: To open a console interface (rather than a terminal program), press ctrl-alt-F1. You can try FuturePilot's commands there.

If that doesn't work, there is another common problem with the fluxkeys component of fluxconf.

---

### Post by employeeno5 on 2008-03-21
Wow, thanks for the fast responses to everybody.

I think I have all I need to get started. The terminal, that's mainly what I wanted. I'm very comfortable navigating via the command line until I manage to work out any other features I might want. 

Hopefully I'll be able to report back in a couple days with happy thoughts.

---

### Post by FuturePilot on 2008-03-21
Good luck and have fun with Fluxbox, it's always fun to try out new WMs. :)

---

