---
title: "What user does program run as ??"
date: 2005-10-17
forum: Desktop Environments
---

### Post by dbee on 2005-10-17
Is there a quick way to find out what user my program runs as ...

I am interested in Nvu as it can't write to some directories I want it to write to. 
How can I find out quickly what user it runs as ? 
I've searched /etc/passwd 

Also, if I want it to be able to write to apache directories - belonging to the apache user and group, then I should just include nvu in the apache group ???

thanks

---

### Post by manicka on 2005-10-17
If you start it normally it starts as the user you have logged in as. If you start it with sudo or gksudo it will run with root priviliges

---

### Post by dbee on 2005-10-17
I think that maybe top is the best way, now that I come to think of it

the only problem is though that my top reading doesn't have any nvu value

---

### Post by Stormy Eyes on 2005-10-17
[QUOTE=dbee]Is there a quick way to find out what user my program runs as ...[/quote]

Under normal circumstances, any programs you run will run with your user ID. Exceptions include programs marked as SUID (set user ID) root, and daemon processes like Apache, who are given their own usernames and group.

[QUOTE=dbee]I am interested in Nvu as it can't write to some directories I want it to write to.[/quote]

That's because you don't have the appropriate permissions.

[quote=dbee]Also, if I want it to be able to write to apache directories - belonging to the apache user and group, then I should just include nvu in the apache group ???[/QUOTE]

That is not a good idea. If you made nvu part of user apache, then you might not be able to run it without root privileges. 

Instead, create a "public_html" directory in your home directory, and put the files there. Apache will handle them from there, and you should be able to test them by punching **[http://127.0.0.1/~user/](http://127.0.0.1/~user/)** into your browser.

---

### Post by dbee on 2005-10-17
Thanks guys,

I'm just wondering though, how I can put .php/.html pages into my local apache, then serve  them to the world and not have the world able to 'rwx' them ?

---

### Post by Stormy Eyes on 2005-10-17
[QUOTE=dbee]I'm just wondering though, how I can put .php/.html pages into my local apache, then serve  them to the world and not have the world able to 'rwx' them ?[/QUOTE]

Are you asking if it's safe to put them in $HOME/public_html? I'm pretty sure that the default Apache config lets you put HTML and PHP files into that directory without the world being able to meddle with those files' permissions, but I am not an Apache guru.

---

