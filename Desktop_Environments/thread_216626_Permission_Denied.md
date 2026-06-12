---
title: "Permission Denied ?"
date: 2006-07-15
forum: Desktop Environments
---

### Post by AsRock on 2006-07-15
Hi,

i'm trying to run a game server but it keep saying Permission Denied.  Do i need to be Super-User ?

If so how do i do that ?

If not whot the hell lol.

Thank You!...

---

### Post by HereInOz on 2006-07-15
Are you trying to run a file to install a program, or are you trying to access a game server.  What are you attempting to do when you get the "Permission Denied"?

---

### Post by AsRock on 2006-07-15
Trying to run a game server as i said.

---

### Post by HereInOz on 2006-07-15
Sorry, perhaps I am being thick here.  Are you trying to set up your computer as a game server, or are you trying to run a multi player internet game on your machine, or what.  If you can explain it in full language, I will do my best to help.  I am not into gaming at all, so please expand on what you mean by "Run a game server"

My interpretaion of that is that you wish to set your machine up as an internet game server, giving access to others, for the purposes of internet gaming.  Is that what you are doing?

---

### Post by AsRock on 2006-07-15
Yes thats whot i am doing.  Trying to setup a dedicated server so ppl can join.

---

### Post by HereInOz on 2006-07-15
OK, so at what point are you getting the Permission Denied?  When you try to run the program to set up the server, or you have set up the server and you now get Permission Denied,  or have you set up the server, can get in to it yourself, but when others try to log on to the server, they get Permission Denied.

It would make it a lot easier if you could give us more information rather than a 1 line reply.  I understand that English may not be your native language, but give us as much information as you can.

For instance, we don't know what you have already achieved, what software you are using, whether it is an http server or a server set up by a particular game.  At the moment, all we know is that you are wanting to set up a game server, and at some point in the process, whatever that process is, you are getting a permission denied.

If it is when you are trying to execute a file that you have downloaded that you are getting "Permission Denied" then you will need to open a terminal, Applications > Accessories > Terminal, and change the permissions on the file.  If you know how to use the command line in Linux, then that will be easy.  If you don't, then I will need to give you more information.

Please tell me as much as you can, and I will help you as much as I can.

Alan

---

### Post by AsRock on 2006-07-15
well i don't blame my language i blame me for dumping on Linux 6 years ago and using M$OS's lol.


BUT anyways program is ran though the Konsole ( terminal ). And thats were the error happens.

whot it says

./ofpserver: line 30: /var/run/ofp_server.2302.run: Permission denied

this is the command used in the console ./ofpserver start

Thank you for your responces

---

### Post by Cooner750 on 2006-07-15
Try this:

```
sudo ./ofpserver start
```

---

### Post by AsRock on 2006-07-15
Yeah that seems to work.  Cheers

asks for a pw and says starting OFP server...   but don't actualy start.

---

### Post by AsRock on 2006-07-26
Hello,

Starting last night i started to get Permission Denied again. Is there a way that would make me administrator so i can temperly get past it so i can run my program again.

would is be usefull to post the whole script i am using here ?

Only part i can see in the script that is not in the server game folder is nohup </dev/null >/dev/null $0 watchdog &

More info

I'm trying to run a Operation Flashpoint server. It was running mid yesterday and last night it started to say Permission Denied. As far as i know nothings been changed any idea's ?

sudo ./ofpserver don't work. it just says Permission Denied
Thank You....

---

