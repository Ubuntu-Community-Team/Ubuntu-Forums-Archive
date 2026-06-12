---
title: "60Gb hardrive"
date: 2006-10-07
forum: Desktop Environments
---

### Post by stealth75711 on 2006-10-07
Hello,

I have a 60 gig hd and was wondering if i set
up the partitions right for ubuntu ill enclose
a screen shot.

And if i didnt can someone tell me what the appropriate
size is for a 60 gig hd?

---

### Post by lemonsCC on 2006-10-07
Are your trying to dual boot?  Just do a normal Ubuntu install?

---

### Post by bulldog on 2006-10-07
You should make a 10Gb /
             swap 1-2GB
Home partition as you like

You should end with three partitions if you only install Ubuntu.

---

### Post by rogier.de.groot on 2006-10-07
I've never heard of any good reason not to make only a / partition and a swap partition, so I recommend doing that. Make the swap twice the size of the computer's RAM.

---

### Post by Ramses de Norre on 2006-10-07
I am soo glad that I've got a seperate /home, because I can reinstall the OS without any problems and I've allready encountered filesystem damage due to a power outlet and it always affected my / but not my /home.
So I think it's a lot safer to have important data (/home) on a seperate partition and not with all the rest of the OS.

---

### Post by rogier.de.groot on 2006-10-07
Hmm... I've never heard of that before... I guess that's a good idea then... On the other hand, all my important data is in a remote subversion repository anyway...

---

### Post by CatKiller on 2006-10-07
It's alright, I guess. A number of people, especially in the past, have had seperate /boot /home and / partitions, which I guess is what you're doing there. How much you want to do it that way is up to you. A number of people (myself included) seem to do OK with just / and swap.

---

### Post by stealth75711 on 2006-10-07
So how much / and swap should i do
for a 60gig hd

30gig / and 30 gig swap?

---

### Post by CatKiller on 2006-10-07
God, no. Some people recommend that you have twice as much swap space as you have RAM. Hopefully you won't need to use much of it at all.

---

### Post by stealth75711 on 2006-10-07
Catkiller can you reccomend what my
numbers should be for no problems?
the / and swap space.  And do i need
to erase everything and reinstall it?
my laptop is making crackling noises

---

### Post by CatKiller on 2006-10-07
The initial setup did seem fine. Or you could have 1 Gig as a swap partition and the rest as an ext3 partition for /. I think that the installer has a sensible default when you tell it to use the whole disk.

I don't know why it's making noises.

---

