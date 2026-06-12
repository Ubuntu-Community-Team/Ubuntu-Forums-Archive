---
title: "Omg!  I Feel Like I'm Going To Explode!"
date: 2006-08-22
forum: Gaming &amp; Leisure
---

### Post by Mazehero55 on 2006-08-22
Okey okey let me calm down... ah..

Okey now. So I download a bunch of games from the packages.ubunulinux.org and everything ( from windows, I can't get on the internet from ubuntu). I got what I needed for each game. And well let me just show you the seed of my frustration.

I try powermanga.deb it says: dependency powermanga-data not met

so I try to do powermanga-data.deb instead, like it said:             dependency powermanga not met

OMG!!!!!

THEN HOW AM I SUPPOSED TO INSTALL IT THEN!!!!

I try one it asks for another, so I try that one and it asks for the one that asked for it!!!!

Can somebody please help me with it, so my headache can recead. 
Please help me

---

### Post by leech on 2006-08-22
Simple.  You just install both at once.  Like so.

```
sudo dpkg -i powermanga_0.79-4ubuntu1_i386.deb powermanga-data_0.79-4ubuntu1_all.deb
```

By the way, from the topic heading of this thread, I thought you had discovered a new way to browse porn. :D

ok, bad joke, but funny all the same.  Hopefully no offense.

Leech

---

### Post by Mazehero55 on 2006-08-22
lol hahaha... 

Thanks:-D 

that was a good one:rolleyes: 

simple, funny, yet slightly offensive

genius:twisted: 

Now finaly powermanga will work

---

### Post by Mazehero55 on 2006-08-22
nope still didn't work. I tried it and it's a no go. 
I did what you said and it just got errors and nothing happened.

Is there any other way to do this?

Oh and when when I try to do certain packages it says broken cache
or something like that

I did what you said and it just got errors and nothing happened.

---

### Post by jimmygoon on 2006-08-22
Seeing as they are in the ubuntu repositories... it would probably be easier to simply:

delete the files you downloaded and then...

"sudo apt-get install powermanga powermanga-data"

enjoy!

---

### Post by Mazehero55 on 2006-08-22
I wish I could do that, but like I said before in () ubuntu won't work with my modem so I have to download them all with a windows partition then move them.
So thats no good.
anything else? anybody?

---

### Post by s_h_a_d_o_w_s on 2006-08-22
Whats wrong with ubuntu? If  yourcables are connected properly, it should work. If not, 

sudo pppoeconf

should help

---

### Post by missmoondog on 2006-08-22
i guess i have to ask. why would you have an operating system that you can't even get online with installed? especially since it sounds like you're dual booting. those simpleton games in ubuntu can't be worth that?!

---

### Post by Mazehero55 on 2006-08-22
I'm still in the process of getting my modem to work. I've even followed howto's for my specific modem and ubuntu and it still won't work for somereason. it's an   Intel 537ep which I need a driver for.
But oddly enough ubuntu lists it as a different modem chipset, but I know it's a 537ep.
I just don't really know that much on setting up a modem for the internet anyways so it might take a while. 
If anyone knows anything about this in particular do you know what to do?

As for why I'm using it without internet, I'm trying to ween myself off of windows. I don't like windows, it''s just too unstable and spyware and virus friendly for my taste.

but anyways back to the topic when I try to install a game it asks for another package but that one asks for the one that asked for it. Confusing does anyone know how to get this working?

oh and what does broken cache mean and how do I fix it?

---

### Post by viciouslime on 2006-08-23
I've not had a broken cache error before, but, one idea for solving this problem is to copy the two deb files you have downloaded to /var/apt/cache and then goto synaptic and install them as you would any other package, then, when it goes to download them it will see they are already in the cache and just go straight to installing them.

However, since you are experiencing a broken cache error at the mo, that might not work. Maybe try it and if it doesn't look around for how to fix your cache before trying again.

---

### Post by leech on 2006-08-23
I would try 'sudo apt-get -f install' then try to dpkg -i them.  The -f install usually will fix any conflicts, you can also try to just do a 'sudo apt-get clean' which will clear your cache.

Leech

---

### Post by Mazehero55 on 2006-08-25
hmmm. I'll try it.

What is a cache anyways?

By the way I got zsnes working somewhat, I'm having problems with glx or something like that.

---

### Post by leech on 2006-08-26
The cache is basically just like a temp folder.  They keep files in there for installation, generally Ubuntu clears the cache automatically, but you can force it with 'apt-get clean'.

What graphics hardware do you have?  We can try getting glx working for you.

Leech

---

