---
title: "Login through remote desktop and show same desktop"
date: 2011-07-19
forum: Desktop Environments
---

### Post by stekre on 2011-07-19
I have set up a server running ubuntu desktop, and I'm able to logon through remote desktop (win 7). The problem is that if I logon from computer 1 and open some programs, I don't see these programs when I logon from computer 2.

I logon with the same user, so I find this strange. Is there some setting I have missed to be able to see the same from any computer (logon through remote desktop).

---

### Post by Kit Peters on 2011-07-20
> **stekre said:**
> I have set up a server running ubuntu desktop, and I'm able to logon through remote desktop (win 7). The problem is that if I logon from computer 1 and open some programs, I don't see these programs when I logon from computer 2.

I logon with the same user, so I find this strange. Is there some setting I have missed to be able to see the same from any computer (logon through remote desktop).
[FONT=Arial]
[/FONT][FONT=Arial][SIZE=2][COLOR=black][FONT=arial]Accessing Windows computer from another Windows computer is very easy using RDP, but when you want to access Windows computer from a machine that is running on Linux, it can be a challenging task.

Lucky you i had the same problem before and I saw an article where it can exactly show you how to use remote desktop. In this article, [/FONT][/COLOR][/SIZE][/FONT][http://www.techyv.com/article/how-use-remote-desktop-ubuntu-linux]("https://www.odesk.com/leaving_odesk.php?ref=http%253A%252F%252Fwww.techyv.com%252Farticle%252Fhow-use-remote-desktop-ubuntu-linux")[FONT=Arial][SIZE=2][COLOR=black][FONT=arial]****, It&#8217;ll show you how to access a windows computer from a remote machine running on Ubuntu Linux Operating System. 

Hope this helps mate. Good luck.[/FONT][/COLOR][/SIZE][/FONT]

---

### Post by dasan on 2011-07-20
which remote desktop client you are using ? Try VNC both win and lin compatible

---

### Post by stekre on 2011-07-22
I think I expressed myself badly. I'm sitting at a win7 computer logging on to a ubuntu desktop machine by using rdp from the win machine into vnc on the ubuntu machine. 

The problem is that if I log off from rdp on win7 computer nr.1 and log on with rdp from win7 computer nr. 2 (to ubuntu machine) I don't see the same programs that I opened from win7 computer nr. 1.

Isn't this strange when I use the same user to logon to the ubuntu machine? imo I should be able to log on to the ubuntu machine from whatever machine I like and still see the same desktop and open programs.

---

### Post by stekre on 2011-07-25
bump
Nobody that can help me with this? I see the programs I have started from computer nr.1 in the system monitor on computer nr.2, but how can I show the program itself (the GUI)?

For instance I have a minecraft server running. I started this from win 7 computer 1 and it runs in a terminal window. When I logon from win 7 computer 2 I can't see the terminal window, but the process is running and the server is up and running.

---

### Post by dasan on 2011-07-28
I didn't had such problems yet.
are you logging off the user or just closing the vnc window ?
from your problem description only i got such a doubt.

while logging off all the gui things will close but running servers will remains till reboot ;)

---

