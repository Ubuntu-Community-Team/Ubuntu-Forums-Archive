---
title: "Problem to remot unix with tsclient+xnest through Xdmcp"
date: 2006-10-02
forum: Desktop Environments
---

### Post by onandon on 2006-10-02
i try to remote unix server with tsclient+xnest through xdmcp. i could see the login window, but the fonts looks bad. After i input the username and passwd to log in, it shut down and the client shows some font errors. I guess it was because of lacking OTF, CID and TTF fonts. I tried to intall mkcfm and reconfigure x-ttcidfont-conf and fontconfigure with dpkg-reconfigure. But still it does not work.

Any idea how to slove this problem? Or how to install OTF CID TTF fonts? Thanks.

By the way, I could remote the unix server through the xdmcp connector from the login window.

---

### Post by lall on 2007-03-21
Hi onando
I have the same problem when connecting against an SUN server.
Did you solve it and and want to share? :)

Thx
/Tim

edit:
Seems that my SUN server has the following installed /usr/openwin/xfs (X Font Server)
Works fine to connect with a windows/cygwin, is that maybe because it is special fonts just for windows?

So the question remains..

---

### Post by onandon on 2007-11-08
> **lall said:**
> Hi onando
I have the same problem when connecting against an SUN server.
Did you solve it and and want to share? :)

Thx
/Tim

edit:
Seems that my SUN server has the following installed /usr/openwin/xfs (X Font Server)
Works fine to connect with a windows/cygwin, is that maybe because it is special fonts just for windows?

So the question remains..

Hi, Tim.
sorry to reply so late.
I found out the problem. the font error comes from the bug of xnest, about font path. do not use tsclient since it uses the default setup of xnest.
use command line or write a bash to execute xnest to remote to sun server.
specify the font path in the command, e.g. use the X font server.
here is my command
> Xnest -query <server name or ip> -geometry 1280x960+0+0 -sync -class TrueColor -depth 24 -fp <local font path 1>, <local font path 2>,<font server>  :1 & 
font sever is set like this: tcp/<server name or up>:<port number>  typically 7100
some more
> 1. Among the font pathes, you should have "misc" as least, either locally or from font server. otherwise you cannot connect to server.
 2. you may need to modify the font.alias file in the font dirctory to make the font looks nice, if you use local font path.(for me, i can only use local font only. No font server avaialbe) You can refer to relevant files in windows. I added some information to fonts.alias for 75dpi and 100dpi seperatly. I referred to the fonts.ali in xmanager's font directory under windows.  OR you can refer to the copy the fonts from the server. i think it should work. but  I did not try it ^_^
Hopefully it can help.

rgds
onandon

---

### Post by onandon on 2007-11-09
I would like to summarize how to remote to solaris/sun server from xubuntu for those new to linux and not clear about x server and x client. Personally, I was confused about server-client relationship and suffered a lot when I tried to remote to the server. (one reason is that our server is setup by someone else long time ago and the server manager do not how to setup it. My labmates use xmanager under windows to connect to it. Everything works well. When I swithed to linux, lots of troubles.)

When you remote to the server(e.g. solaris) from your local machine(e.g. xubuntu), try to start some software and display in your local machine. Now: your local machine(e.g. xubuntu) is X-server and the remoted server(e.g. solaris) is client. You need to set up both X-server (your local machine) and X client (the server) to work properly.

In the server machine(X- client), in the terminal type "echo $DISPLAY". it should display sth like "<your local machine address>:0".
otherwise use "setenv DISPLAY <your local machine address>:0" to set it.

Personally I use 3 ways to remote to sun/solaris server. 
> 1. Use ssh or telnet connect to sun/solaris server and use command line to start the applications
What you should do in your local machine (X server)
1)allow your sun/solaris server to connect to local machine
ues "xhost +<sun/solaris server name or IP>" to temperately allow connection or add sun/solaris server name or IP to /etc/hosts.allow to allow connection permanently
Also, remember setup your firewall correctly if you have one. Firestarter is good option if you would like to setup it.
2)enable gdm/xdm to accept tcp connection
there are 2 options
a. modify /etc/gdm/gdm.conf-custom 
in security section, set DisallowTCP=false. it will looks like
[security]
[COLOR="Red"]DisallowTCP=false[/COLOR]
b. go to settings>>Login window>>Security, uncheck "Deny TCP connections to x server"

Then, it should work.
2. Use Xnest (if the sun/solaris server accepts XDMCP connection)
1)make sure your firewall allow the remote server to connect.
2) use the command in terminal or make a bash
the bash file looks like
[quote]#!/bin/sh
Xnest -query <remote server address> -geometry 1280x960+0+0 -sync -class TrueColor -depth 24 -fp <font path1>,<font path 2>  :1 &
make sure you add misc font to the font path

3 connect from the login windows (if the sun/solaris server accepts XDMCP connection)
at the login windows, press F10, some options will pop up. choose xdmcp to connect the server.
[/quote]
I prefer the 1st method. Its speed is the best. 
If you have some problem with fonts, you can refer to my previous post.

If there is any error or mistakes, plz point it out. I would appreciate it.
Thanks
onandon

---

