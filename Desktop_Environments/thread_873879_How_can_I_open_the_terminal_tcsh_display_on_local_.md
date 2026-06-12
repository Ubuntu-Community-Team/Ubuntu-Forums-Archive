---
title: "How can I open the terminal tcsh display on local Ubuntu X11 display"
date: 2008-07-29
forum: Desktop Environments
---

### Post by bbspeterlee on 2008-07-29
[COLOR="Blue"][B][SIZE="6"]How can I open the terminal tcsh display on local Ubuntu X11 display?
[/SIZE][/B][/COLOR]

I use ssh to log on to the Ubuntu server. The default terminal on the Ubuntu server is -tcsh, and my local Ubuntu terminal is -bash.

So how can I transfer the server display to local Ubuntu X11 display?

Thank you so much.

---

### Post by bbspeterlee on 2008-07-30
I got the answer from somewhere else:
[http://www.linuxsir.org/bbs/showthread.php?p=1880455#post1880455](http://www.linuxsir.org/bbs/showthread.php?p=1880455#post1880455)

Let me share with you guys:

Q022. How can I open the server GUI display on local X11 display (using SSH terminal or not)?

A022.
Enables trusted X11 forwarding.

Case A: Local is Linux, using SSH to connect to the server
##########################################################
- ssh -Y user@hostname

Case B: Local is Windows, using PuTTY (SSH) to connect to the server
##########################################################
(1) Install Xming server ([http://www.straightrunning.com/XmingNotes/);](http://www.straightrunning.com/XmingNotes/);)
(2) Turn on the Xming server from "Start --> Xming --> Xming";
(3) Run PuTTY and configure it as:
a) Session --> Host Name (or IP address), Port: 22
b) Session --> Connection type: SSH
c) Connection --> SSH --> X11 --> Enable X11 forwarding: Checked
(4) Done.

Case C: Local is Linux, using non-SSH to connect to the server
##########################################################
local > xhost +
local > (connect to user@hostname using non-SSH)
server-tcsh > setenv DISPLAY LocalIP:0
OR:
server-bash > export DISPLAY=LocalIP:0

More see also:
[http://www.peterlee.com.cn/blog.php?getArticleID=53](http://www.peterlee.com.cn/blog.php?getArticleID=53)

---

