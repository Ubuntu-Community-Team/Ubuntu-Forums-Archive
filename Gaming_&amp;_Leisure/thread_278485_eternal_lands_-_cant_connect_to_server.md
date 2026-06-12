---
title: "eternal lands - cant connect to server"
date: 2006-10-16
forum: Gaming &amp; Leisure
---

### Post by siman on 2006-10-16
i posted my problem in eternal lands, but only in newbie forum - and nobody answered. so maybe anyone here can help me:

I installed eternal lands with the .deb file I found on ubuntuforums (was 2-3 weeks old, but version number is up to date). Game starts, but then it says:

```

Connecting to Server...
Can't connect to Server
Press any key to try again.

```

I tried changing the Server URL from the default domain to the IP adresse I found in the eternal lands - doesnt help

Any Ideas?

And on a related topic: any other beginner-friendly MMO you would suggest instead?

---

### Post by Doctoxic on 2006-10-16
are you sure its the latest version - should be 132 - if you have an older version i don't think it will let you connect

Doc

---

### Post by siman on 2006-10-16
hm, allright it says 1.3.2 beta... maybe beta is the problem, will check it out

---

### Post by siman on 2006-10-16
i downloaded the only .zip for linux and tried that, it's the same 1.3.2 version and doesnt connect.

i changed the data path in the el.ini, didnt help. the update on the website is only for 1.3.0 users - nevertheless i applied it as well but nothing changes, still no connect.

hm.. i should have all the dependecies because i installed the .deb before and still have it installed.

edit - SOLVED: maybe it was my fault, but i got it working by deleting ~/.elc/el.ini .. dont know, maybe there was a conflict with the one in the game dir. the server-addresses were the same in both files.

---

### Post by Doctoxic on 2006-10-17
nice :)

Doc

---

### Post by squale on 2006-10-18
Eternal lands changed their server address, it was maybe your problem

---

### Post by siman on 2006-10-18
yes... i did research and it was posted in the forum only...

well.. works now

---

### Post by BlacKat_K on 2006-10-27
> **siman said:**
> i downloaded the only .zip for linux and tried that, it's the same 1.3.2 version and doesnt connect.

i changed the data path in the el.ini, didnt help. the update on the website is only for 1.3.0 users - nevertheless i applied it as well but nothing changes, still no connect.

hm.. i should have all the dependecies because i installed the .deb before and still have it installed.

edit - SOLVED: maybe it was my fault, but i got it working by deleting ~/.elc/el.ini .. dont know, maybe there was a conflict with the one in the game dir. the server-addresses were the same in both files.

I have the same problem,cant connect to server after installing to Edgy.It worked perfectly until now.What exactly did you delete?i cant find that .elc location...

---

### Post by siman on 2006-10-27
The ini file was in my home directory. try this:

```

rm -f ~/.elc/el.ini

```

But later I found out, that I had the wrong server name in this ini file, and the ini in the game root directory had the right one. I found this server change not very prominent in the eternal lands forums.

I think after starting the game this ini in the home directory gets recreated. Now it has those server settings, they are correct:

```


#server_address = game.eternal-lands.com
#server_port = 2000

```

hope that helps...

---

### Post by BlacKat_K on 2006-10-27
:| i changed the server...it just wont work...

---

### Post by BlacKat_K on 2006-10-27
Oh damn!Apparently el.ini had to be in the elc folder.it never had to be there before.how strange...well it works now, thanks siman :D

---

### Post by doobit on 2007-03-06
Ah, OK.

---

