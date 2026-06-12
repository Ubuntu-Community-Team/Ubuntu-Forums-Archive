---
title: "Kate crashing"
date: 2005-06-14
forum: Desktop Environments
---

### Post by davide on 2005-06-14
I was engaged with Kate but recently we split up!
Seriously has anyone the same problem:
 i cannot open Kate from terminal on a sudo session, it won't open due to a crash...

lemme now...

Best wishes

Davide Trapani

---

### Post by dolny on 2005-06-14
The same happens for me.

---

### Post by Xian on 2005-06-14
Opening kate with sudo from a terminal session is a no go.
However, you can substitute kwrite and that will work fine.

---

### Post by Curlydave on 2005-06-14
I had Kubuntu installed briefly, and I couldn't get kate working either.

---

### Post by dolny on 2005-06-14
[QUOTE=Xian]Opening kate with sudo from a terminal session is a no go.
However, you can substitute kwrite and that will work fine.[/QUOTE]

Hah, thanks;)

---

### Post by rosslaird on 2005-06-14
I had a kate crash issue, but rebooting automagically fixed it.

---

### Post by cwaldbieser on 2005-06-14
Try:
```

$ kdesu kate
```

That seems to work even though sudo causes kate to crash.

---

### Post by nickless on 2005-08-29
This sucks seriously...
can't use kate or kwrite :(
> root@meanmachine:/ # kwrite
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kwrite: cannot connect to X server :0.0
root@meanmachine:/ # kate
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kate: cannot connect to X server :0.0
kate: ERROR: KUniqueApplication: Registering failed!
kate: ERROR: Communication problem with kate, it probably crashed.


---

### Post by nickless on 2005-08-30
Whats going on? :(

> root@meanmachine:/ # kedit
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kedit: cannot connect to X server :0.0


---

### Post by tonysathre on 2005-08-30
ya i had the same problem to so i just used kwrite

---

### Post by ManLord on 2005-08-30
cwaldbieser is right, use "kdesu kate filename"

Or you can right click a textfile in konqueror and Actions -> Edit as root, that's the same effect.

Actually i prefer kedit with sudo, sudo kedit works fine. The editor isn't that advanced as kate but good for small tasks.

sudo apt-get install kedit

---

### Post by nickless on 2005-08-30
Interessting: Using sudo su and then starting kate or kedit will produce nothing more than an error msg. sudo kedit or sudo kwrite works... :)

---

### Post by craigmac on 2005-09-13
I have the same hassles with KATE. Is there any way to fix it - I can't bear things not being perfect - drives my wife crazy  :roll: 

I have had good success with KWRITE though. I like that right-click edit as root option too. Perfect for changing one parameter in a file.

Will also be apt-getting kedit tonight. Thanks ManLord

---

### Post by agm642 on 2005-09-13
[QUOTE=nickless]This sucks seriously...
can't use kate or kwrite :(

 root@meanmachine:/ # kwrite
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kwrite: cannot connect to X server :0.0
root@meanmachine:/ # kate
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kate: cannot connect to X server :0.0
kate: ERROR: KUniqueApplication: Registering failed!
kate: ERROR: Communication problem with kate, it probably crashed.[/QUOTE]
I had the same problem once but it was fixed by rebooting...

---

### Post by geearf on 2005-10-03
[QUOTE=nickless]Interessting: Using sudo su and then starting kate or kedit will produce nothing more than an error msg. sudo kedit or sudo kwrite works... :)[/QUOTE]
for sudo su, and kate
you need to gain root privilege on X too, to do that you need to play with xhost or .Xsessio :

[http://www.debian.org/doc/manuals/reference/ch-tune.en.html#s-ss-xsu](http://www.debian.org/doc/manuals/reference/ch-tune.en.html#s-ss-xsu)


For sudo kate, it works fine on my computer.

---

### Post by katu on 2005-10-03
I had this problem sometime ago, but it seems that recent updates fixed some of it. Meaning **sudo su** and then **kate** works for me. 
> kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
this part of the problem is that the root user doesn't have acces to the xsession. try typing 
```
xhost +
``` 
as a user, and then try kate as the root user.
**sudo kate**   though, gives me:
kate: ERROR: Communication problem with kate, it probably crashed.

---

