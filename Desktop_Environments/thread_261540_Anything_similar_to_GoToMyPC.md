---
title: "Anything similar to GoToMyPC?"
date: 2006-09-20
forum: Desktop Environments
---

### Post by mssm on 2006-09-20
I woud like to access my Ubuntu desktop machine at my office from some web browser(say firefox) outside my office(e.g. home or cafe). There are two softwares available readily in Windows for this purpose : GoToMyPC and LogMeIn. I hope many of you have tried them. They are really cool. Are their any linux equivalents of these softwares? They are really helpful. A program which comes close to this(and I use it heavily) is freenx/nomachine client. However, it requires its own client to be installed on the remote machine. It doesn't work through web browser. I am not interested in vnc like softwares. I tried them -- they are very slow and not secure.

I would like to have a gotomypc like software in Edgy. Many thanks in advance.

---

### Post by kidders on 2006-09-20
I know this isn't really what you want to hear, but imho VNC-style solutions are best ... after all, they are extremely widely supported. If you tunnel your VNC conenctions over SSH and spend a little while tuning the graphics performance, it can be quite impressive ... and impenetrably secure.

Sorry for posting the one suggestion you specifically discounted! I guess I was just wondering how it worked out so badly for you.

---

### Post by mssm on 2006-09-21
> **kidders said:**
> I know this isn't really what you want to hear, but imho VNC-style solutions are best ... after all, they are extremely widely supported. If you tunnel your VNC conenctions over SSH and spend a little while tuning the graphics performance, it can be quite impressive ... and impenetrably secure.

Sorry for posting the one suggestion you specifically discounted! I guess I was just wondering how it worked out so badly for you.

Hi kidders, thanks for youe reply. Actually vnc didn't turn out bad for me. But my point was different; think of either of these two situations : suppose you go to a cafe which have pc's with basic softwares installed and do not give users administrative priviledge. Or, as often happened to me : I go to a conference without my laptop. There are some unix/linux terminals avialable. I can access my office machine only through non-graphical ssh. Can I start vnc over ssh on such machines? Probably not.

Second, after using freenx/nomachine server and client, I was blown away and never ever looked back to vnc. Have you tried that? It's way faster and more user-freindly than vnc. It's like I am just sitting next to my office desktop -- no delay, nothing. However, when I am at some other places than home where I can not have the support of the nxclient, I can access it with ssh but no graphics. If I can install a linux client like gotomypc or logmein in my office ubuntu box, I could have accessed it from anywhere even without nxclient. VNC through ssh tunnel I have tried but it is no comparison to nxclient. Frankly, if you haven't tried the latter, give it a try. Here is the link for quick setup :

[http://ubuntuforums.org/showthread.php?t=241651&highlight=freenx](http://ubuntuforums.org/showthread.php?t=241651&highlight=freenx)

---

### Post by kidders on 2006-09-21
Thanks for the link ... I'm looking forward to trying it after the praise you gave it!!

> Can I start vnc over ssh on such machines?
The main reason I wind up using VNC a lot is that most machines I use already have the required software on them ... even if they're not mine. Tunnelling over SSH is the only way I ever make such a connection.

I'll post back if I come across a better option :-)

---

