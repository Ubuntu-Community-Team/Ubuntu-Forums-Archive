---
title: "Printer and sound problems"
date: 2006-02-14
forum: Desktop Environments
---

### Post by syklitengutt on 2006-02-14
Hi... Long time sinse Ive asked any questions now.
I have now completly settled with ubuntu over windows and anything else.
I almoust start crying when I have to reeboot my computer to do some windowsing...

But anyhow. The problems.
I have really big problems with my soundmixer.
I thought I used alsamixer as soundmixer, but it doesnt look that way.
I use xfce. Perhaps that is using arts as default I dont know.
Im able to play music trough xmms but if I then get a sysmessage or something I get this error showed on the image.
If I try to open mplayer or totem It very often freeze (when mplayer is running)
and I know thats because it crashes with the sound.


and secound problem. I have a HP Descjet 720C printer.
Ive tried using pnm2p and cups, but I really cant get it to work. If I try to connect to [http://localhost:631/admin](http://localhost:631/admin) trough my webrowser Im asked for a password Ive never set....
Its not a usb printer its a old analog printer using a big cable... 
(lol... dont know what that one is called)

So sorry for a messed up message but if anyone can manage to help me 
I would be wery pleaced...

-Chris-

---

### Post by matthewv on 2006-02-14
Are you using 5.04 or 5.10...??

Sorry if this sounds stupid, but that sound problem was apparently very common in 5.04, but fixed in 5.10...

---

### Post by syklitengutt on 2006-02-15
I have 5.10.
Sorry for not mention that...

---

### Post by slux on 2006-02-15
The cups web interface can be enabled by adding the cupsys user to the shadow group and the username/password it asks are for a superuser account. (well, I guess something less might suffice if another account has the rights to the files it wishes to touch but I haven't tried) So to get in you need to make the cupsys user part of the group shadow and set a root password. You should be able to use the graphical printer configuration application for basic cups config as well and that's the preferred ubuntu way though.

In order to make CUPS work it should be able to use the pnm2ppa driver you mention but I guess whether it does can be seen in the driver/printer list when you are adding your printer.

---

### Post by syklitengutt on 2006-02-15
lol... sorry but shadow group etc was compleetly greek to me.

---

### Post by syklitengutt on 2006-02-15
update on the sound issue.
I cant play any sounds trough video anymore.
I can only play trough xmms, wich I have set to use the alsa output and to hardware 0.1 wich does not exist.
If I try to use those settings on other progs I get and error that sais hw0.1 does not exist.

If I type artsshell in a shell I get this error:
chris@chris:~$ artsshell
unix_connect: can't connect to server (unix:/tmp/ksocket-chris/localhost.localdomain-50fa-43f3110d)
unable to connect to sound server

but how can I set the system to use different mixers as default.
(ex change form arts to alsa and visa verca)

---

### Post by slux on 2006-02-15
Do you have a special reason you'd like to specifically use the cups web "interface? Or something specific you're thinking of looking at there?

How have you configured the printer previously, thru the graphical printer configuration tool or something else?

If you do, "sudo usermod -G shadow cupsys" will take care of the shadow group issue, "sudo passwd root" will let you set a root password to use in the login.

---

### Post by syklitengutt on 2006-02-15
I have configured the prointer troug gnome printer and xfce printer managment.
In gnome I get a green v at the printer pnm2p,
but it doesnt work.

The reason for the interface was that I could possibly edit something there to get it to work

---

### Post by syklitengutt on 2006-02-15
heres an explainig image(its modified):

---

### Post by syklitengutt on 2006-02-16
bumping this printer and sound still unsolved

---

### Post by syklitengutt on 2006-02-17
bumping again

---

### Post by syklitengutt on 2006-02-18
bumping once more

---

### Post by syklitengutt on 2006-02-19
bumping again---

---

### Post by syklitengutt on 2006-02-20
have to bump this again...
4 days and  no answers

---

### Post by syklitengutt on 2006-02-21
bumping this again...
bump bump bump

---

### Post by syklitengutt on 2006-02-22
bump

---

### Post by syklitengutt on 2006-02-23
bump

---

