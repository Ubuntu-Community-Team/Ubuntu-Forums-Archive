---
title: "Xubuntu, VNC, and a blank terminal window"
date: 2006-09-27
forum: Desktop Environments
---

### Post by Lunarbunny on 2006-09-27
After spending about 10-12 hours just to get the system up and running and running VNC properly, I've got a couple of issues:

The default terminal window that's up is blank. I can enter text (typing "thunar" then enter will start up the file manager), but the text is invisible. The prompt is invisible and whatever outputs is also invisible. I've tried changing colors on terminal and color depth, but it fails to help.

Is there any shortcut to bring up the terminal window if I somehow close it? The only thing I know to do right now is stop and start a new VNC desktop, which is hard because the computer doesn't have a permanent monitor (I took it down 2 floors from another computer so that I could get it running as a permanent VNC server)

Finally, is there some way to start XFCE desktop on a VNC desktop? Although I have little trouble getting to what I need to run (despite the blank terminal window's attempts to stop me), it'd be nice to use more of the GUI.

I should say that it's running on an old Compaq Presario 7470 ([specs]("http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&lc=en&product=94486&dest_page=product&cc=us&docname=c00012507")), except with 192 (184 available) MB of RAM, a different hard drive, and a Netgear FA311 NIC.

EDIT: Forgot to mention I'm using RealVNC

---

### Post by Lunarbunny on 2006-09-28
Well, this is part bump and part report.

Terminal still sits blank at me while the gears whirr away in the background. However I was able to start the desktop from terminal (as I don't know any other way, I start each of these in a seperate tab and leave that terminal window alone)

~$ startxfce4
~$ xfdesktop
~$ xfce4-panel

If file windows want to shut themselves:

~$ thunar

I have an issue with the menu not showing up in the upper left sometimes, but I can work around that using right-click on the desktop.

---

### Post by Lunarbunny on 2006-10-02
Well, I love the amount of support I'm getting...

I'm still stuck with a blank terminal window.

---

### Post by treris on 2006-10-02
I'm not exactly sure what you're trying to do, but ehm if you're trying to log in to another computer (aka server) from another computer (aka client) would you mind if I recommend FreeNX, it does sort of the same thing as VNC I gather, but I have found it very easy to use.

Try this [link]("https://help.ubuntu.com/community/FreeNX")

I hope this helps, and indeed you will need to configure it a bit to automatically start up the xubuntu gui when you log in remotely
this [thread]("http://www.ubuntuforums.org/showthread.php?t=201054&highlight=xubuntu+freenx") might help you

---

### Post by Lunarbunny on 2006-10-02
I'll give it a try when I have access to the server.

---

### Post by Lunarbunny on 2006-10-02
Well, it *almost* works perfectly. NX will give me issues if I try to suspend a session - it opens the desktop then leaves the open Xubuntu desktop rendered while the actual window turns into a tiny thing about 200px by 30px, and nothing works. The only thing to do then is kill the process and terminate the session on the server.

I'm accessing from Windows XP and Windows 2000 computers.

---

### Post by henryrhenryr on 2008-06-16
> **Lunarbunny said:**
> 
The default terminal window that's up is blank. I can enter text (typing "thunar" then enter will start up the file manager), but the text is invisible. The prompt is invisible and whatever outputs is also invisible. I've tried changing colors on terminal and color depth, but it fails to help.


I also have this problem.  I'm using tightVNC viewer on winXP and tightVNC server on my ubuntu dapper machine.  I have used the same setup on another ubuntu machine with exactly the same setup and it was fine.  The only difference is that the one that worked was an iMac (ie PowerPC).

I looked at FreeNX.  I really don't need a huge amount of functionality so I'm not sure I want to go installing a whole load more software.  Does anyone have any ideas to fix the problem?

---

### Post by Lunarbunny on 2008-06-16
I never fixed this issue, but I did try VNC on another machine without any issues, but that was with Ubuntu 7.10 and x11vnc. See if x11vnc fixes your problem.

---

