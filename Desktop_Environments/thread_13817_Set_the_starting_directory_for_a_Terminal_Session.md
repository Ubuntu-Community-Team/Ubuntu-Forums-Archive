---
title: "Set the starting directory for a Terminal Session"
date: 2005-02-02
forum: Desktop Environments
---

### Post by mattisking on 2005-02-02
Man I hate asking dumb questions like this, so I'm sorry in advance.

I FINALLY got the Array3 Hoary install to give me back my XWindows. There's some bad bugs in there...  somehow in that process, I managed to screw up my Terminal settings in some undefined way so that from within the Ubuntu Desktop.

When I right-click the desktop and choose New Terminal, my starting prompt begins in /media/cdrom0 instead of my natural $HOME directory (which is set properly). Where can I change this? I thought maybe it would be in .bashrc or some such place but I simply can't find it. It's making me nuts.

---

### Post by Wim Sturkenboom on 2005-02-03
It's only under X? Or with a normal commandline login as well?

---

### Post by mattisking on 2005-02-03
If I go to Applications->System Tools->Terminal it comes up normally in my home directory.

If I right-click on the desktop and say "Open Terminal" it comes up at /media/cdrom0.

If I Ctrl-F2 and log in with the non-gui command line it comes up normally in my home directory. 

This happened when I was troubleshooting my xorg.conf. I had copied a manually created xorg.conf onto a CD from my other PC and had to mount the CD to get the file. I think it's possible I ran 'startx' when testing it out from /media/cdrom0 and that somehow that's related.

As a temporary workaround, at the bottom of my .bashrc I stuck in a 'cd ~' but I hate to do that. I want to fix it properly, not put in some dumb hack.

---

### Post by Levander on 2005-02-03
[QUOTE=mattisking]
This happened when I was troubleshooting my xorg.conf. I had copied a manually created xorg.conf onto a CD from my other PC and had to mount the CD to get the file. I think it's possible I ran 'startx' when testing it out from /media/cdrom0 and that somehow that's related.

[/QUOTE]

Is it possible that you're still running the X-server started from the /media/cdrom0 directory?

1.) Kill your X-server, with Ctrl-Alt-Backspace.  
2.) Change the directory to some other random directory,  
3.) Run startx from within that other directory
4.) Open a terminal from the desktop menu like you were before.

Are you now in the random directory from 2.) above?

If so, need to figure out which command that menu is actually running, and replace it without whatever command the Applications menu using to launch a terminal.  Note that this paragraph is probably true whether the rest of my guess here is correct or not.

Good Luck.

---

### Post by mattisking on 2005-02-03
I can't seem to kill X. Every time I try Ctrl Alt Backspace it boots me out of Gnome right back to the graphical greeter which doesn't offer an option to boot into anything other than GNome. Am I missing something?

---

### Post by Wim Sturkenboom on 2005-02-04
That is what <ctrl><alt><bs> does :lol: 

*ps -ef |grep X* will give you the pid of the X-server. You can stop it with the *kill _pid_* command. Later you can issue a startx.

You can restart the X-server using *kill -HUP _pid_*. This is the same as <ctrl><alt><bs>, but you can do this from a specific directory.

I should run these commands from a terminal (e.g. <ctrl><alt><f2>).

Note: this is not to solve to problem, just to kill/restart X

---

### Post by joethecomputer on 2008-07-19
i just want to mention that all of the required packages are available in The Synaptic Package Manager, just do a search for g15

---

