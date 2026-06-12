---
title: "Remote Installation and Setup"
date: 2009-09-26
forum: Desktop Environments
---

### Post by buntuxxx on 2009-09-26
I have a server at a remote location, far away from physical reach, that is running [FONT=Helvetica][SIZE=2][COLOR=#333333][FONT=Helvetica][SIZE=2][COLOR=#333333][FONT=Helvetica][SIZE=2][COLOR=#333333]Ubuntu Server 8.04.[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

[FONT=Helvetica][SIZE=2][COLOR=#333333][FONT=Helvetica][SIZE=2][COLOR=#333333][FONT=Helvetica][SIZE=2][COLOR=#333333]I have root access to it via SSH. I am new to command line so I really need baby steps that will allow me to set this server up for REMOTE DESKTOP PROTOCOL, perhaps running ubuntu desktop environment.[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

[FONT=Helvetica][SIZE=2][COLOR=#333333][FONT=Helvetica][SIZE=2][COLOR=#333333][FONT=Helvetica][SIZE=2][COLOR=#333333]I assume that once it is working, I would have to use VNC to get connected to it but getting there is a worry.[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

[FONT=Helvetica][SIZE=2][COLOR=#333333][FONT=Helvetica][SIZE=2][COLOR=#333333][FONT=Helvetica][SIZE=2][COLOR=#333333]Please help![/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by buntuxxx on 2009-09-27
48 VIEWS and no response.  Please community!

---

### Post by Lars Noodén on 2009-09-28
If you install a graphical desktop on the machine, then it becomes a remote desktop and not a sever anymore.  Keep in mind that the more pieces you have, and depend on, the more likely that one of them is broken at any given time.  

I would very strongly encourage you to learn the shell. You'll want a paper notebook to keep notes in and a section for 'recipes'.  A lot of money has been spent getting people to call the shell the 'command line' and more money on disparaging the 'command line'  IMHO, the term implies just-in-case requirements and that one must master the whole before starting.  However, it is really scripting and that's programming.  And since programming is learn-as-you-go or learn-as-you-need that's how the shell should be approached.  

Additionally, anything you do in shell is already a script so automation is the added step of saving the lines in a file.  

The shell is a very advanced, tried and true low latency user interface from which you can run programs (not 'commands').  The programs do different things and can be tacked together like Lego Blocks to build just what you need.  

So.  

What are the first system administrative tasks you wish to handle remotely?

---

### Post by macooper on 2009-09-28
If you really want an easier to use interface than the shell have you considered using webmin ? [http://www.webmin.com/](http://www.webmin.com/)

---

### Post by Lars Noodén on 2009-10-01
Webmin is good for secondary admins.  However, when something that webmin depends on is down, like the web server, you still have to know your way around shell scripting.  Shell scripting is not that much harder than webmin, just a lot different and more complex.

---

### Post by karlson on 2009-10-01
> **buntuxxx said:**
> I have a server at a remote location, far away from physical reach, that is running [FONT=Helvetica][SIZE=2][COLOR=#333333][FONT=Helvetica][SIZE=2][COLOR=#333333][FONT=Helvetica][SIZE=2][COLOR=#333333]Ubuntu Server 8.04.[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

[FONT=Helvetica][SIZE=2][COLOR=#333333][FONT=Helvetica][SIZE=2][COLOR=#333333][FONT=Helvetica][SIZE=2][COLOR=#333333]I have root access to it via SSH. I am new to command line so I really need baby steps that will allow me to set this server up for REMOTE DESKTOP PROTOCOL, perhaps running ubuntu desktop environment.[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

[FONT=Helvetica][SIZE=2][COLOR=#333333][FONT=Helvetica][SIZE=2][COLOR=#333333][FONT=Helvetica][SIZE=2][COLOR=#333333]I assume that once it is working, I would have to use VNC to get connected to it but getting there is a worry.[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

[FONT=Helvetica][SIZE=2][COLOR=#333333][FONT=Helvetica][SIZE=2][COLOR=#333333][FONT=Helvetica][SIZE=2][COLOR=#333333]Please help![/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

Why run X on the server?  If you are trying to run X/KDE/GNOME based tools from the server connect using ssh -X <server> and run the tool displaying back to your workstation.

---

