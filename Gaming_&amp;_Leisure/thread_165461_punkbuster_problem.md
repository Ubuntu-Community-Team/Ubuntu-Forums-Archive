---
title: "punkbuster problem"
date: 2006-04-24
forum: Gaming &amp; Leisure
---

### Post by Smokemare on 2006-04-24
everything was fine but now it says i dont have permission to go into .q3a/pb 
dont know how to fix.how can i set the permissions on this folder to allo it to update?](*,)

---

### Post by johso on 2006-04-24
[QUOTE=Smokemare]everything was fine but now it says i dont have permission to go into .q3a/pb 
dont know how to fix.how can i set the permissions on this folder to allo it to update?](*,)[/QUOTE]

I remember having this problem with Enemy Territory.
First try this (from your home folder):
```

 sudo chmod -R 777 .q3a/pb

```
If that doesn't work, I think the thing I did was to start the game from a terminal as super user, updated it and exited again. Then it all worked out.
However, most people discourage to run programs like root, though, but I don't think it presents a big risk as long it's just for an update...

---

### Post by Smokemare on 2006-04-26
tried it but no go thanks anyways.
it looks as though it does but then reverts back and won update and says i dont have permission to do so.

---

### Post by R3linquish3r on 2006-04-27
[QUOTE=Smokemare]tried it but no go thanks anyways.
it looks as though it does but then reverts back and won update and says i dont have permission to do so.[/QUOTE]

sudo chown (username) /home/name/.q3a/pb

also you need to run quake with sudo to have punkbuster run. If ya ever want to play me my name is zP::Osama and I usually play on the Seen Your Huevos Excessive Plus server.

---

