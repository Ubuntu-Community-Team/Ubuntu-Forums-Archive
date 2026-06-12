---
title: "Run program in background"
date: 2009-06-19
forum: General Help
---

### Post by Magma828 on 2009-06-19
I want to run a program on my ubuntu machine remotely using SSH. I can do it by simply typing the command to the program but the output goes to the SSH client window, and as soon as I close the SSH client the program stops too.

I just want to be able to type a command, and leave the server to do it's job.

Like what you do when you start XAMPP, you type "/opt/lampp/lampp start", it tells you the server is starting and runs the server in the background.

Thanks for your time.

---

### Post by Lampi on 2009-06-19
check the programs helpsite for parameters forcing a startup in daemon mode. like this tasks continue when you close the shell

---

### Post by ewankho on 2009-06-19
try: command &

---

### Post by Magma828 on 2009-06-19
> **ewankho said:**
> try: command &
Did just the same as executing the program normally, but returned what appears to be a status code aswell - [1] 6267.

> **Lampi said:**
> check the programs helpsite for parameters forcing a startup in daemon mode. like this tasks continue when you close the shell
It's a Java application I made, can I make it enter daemon mode with a parameter?

---

### Post by nothingspecial on 2009-06-19
Use screen. I think its installed by default. If not

```
sudo apt-get install screen
```

Log into your server

run screen

```
screen
```

Start your process

Press Ctrl + A

Then Ctrl + D

This detaches your screen session but leaves the process running.

You can logout of your server and go to the pub.

When you are ready log into your server, from any machine anywhere and type

screen -r

Your process window will appear as if you`d never been away.

How cool is that?

You can run multiple detached screen sessions in which case when you type screen -r you will be presented with a list of pids just choose the right number for the one you want to reattach and the type screen -r pid (eg screen -r 2247)

There are loads of other things you can do with screen

Type man screen, I couldn`t run my server without it

---

### Post by Magma828 on 2009-06-19
Wow that's even more awesome than I needed, thanks a lot I'll sure have a lot of fun with screen.

---

### Post by DCBSupafly on 2011-08-07
I was trying to get this to work for a while, even read most of the man screen, but I couldn't figure this process out.  This did the trick, but I'm left wonder what ctrl A & ctrl D do.  Attach and detach?

---

### Post by JacobSchwartz on 2012-04-06
Read this page:
[https://help.ubuntu.com/community/Screen](https://help.ubuntu.com/community/Screen)
It explains the screen commands, including the ctrl + A ;)

---

