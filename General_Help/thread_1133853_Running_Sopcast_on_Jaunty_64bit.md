---
title: "Running Sopcast on Jaunty 64bit"
date: 2009-04-23
forum: General Help
---

### Post by empty_spaces on 2009-04-23
I downloaded the deb files for sopcast from this link-
**[http://code.google.com/p/sopcast-player/](http://code.google.com/p/sopcast-player/)**

It worked perfectly in Intrepid64, but in Jaunty64, nothing happens when I run it.
I tried to run it from the terminal to see what the error was, and this is what I got:

[B]user@Jaunty64:~$ sopcast-player
RuntimeError: Bad magic number in .pyc file
[/B]

What could be the problem here? Different version of Python maybe?

---

### Post by empty_spaces on 2009-04-24
bump

---

### Post by ptemple on 2009-04-25
For now, type:
python /usr/share/sopcast-player/lib/sopcast-player.py

This will work until he has fixed the .pyc files.

Phillip.

---

### Post by NoXiS on 2009-04-25
It seems to be an incompatibility with Python version 2.6 (which is likely your default version).

Make sure you have Python version 2.5 installed (don't worry multiple versions can be installed safely side by side).

```
sudo apt-get install python2.5
```

The executable /usr/bin/sopcast-player is just a script that runs the 'real' python program. You can edit this file and amend it to use Python v2.5.

```
sudo nano /usr/bin/sopcast-player

```

Change it so it looks like this.

```
#!/bin/sh
/usr/bin/python2.5 /usr/share/sopcast-player/lib/sopcast-player.pyc $@
```

Note the "2.5" after the "/usr/bin/python" at the start of the line. This just makes sure that Python v2.5 is used to run the sopcast-player. This works perfectly for me and all your menu shortcuts etc. will continue to work perfectly.

Hope this helps.

---

### Post by empty_spaces on 2009-04-25
Awesome, that worked out great.
ptemple, I tried your way and it worked.
Then I made the changes as per NoXis's post and now Sopcast works fine via the menu option.
So thanks to both of you.

---

### Post by soro2005 on 2009-04-25
Gsopcast would be an alternative that works just fine in Jaunty: [http://code.google.com/p/gsopcast/](http://code.google.com/p/gsopcast/)

---

### Post by joanmunoz on 2009-04-26
Thx NoXiS!!

I had the same problem and now sopcast works perfect.

Regards

Joan

---

### Post by ade234uk on 2009-04-30
Managed to get Sopcast working with these instructions in Ubuntu 9.04.

Works perfectly, not only that it seems to work better than it did in Windows too. Thank you.

---

### Post by Lezzer on 2009-05-02
Thanks NoXiS.  Installed python 2.5 like you said and edited the launcher and what do you know?  Worked first time!

Thanks

Lezzer

---

### Post by Lupi on 2009-05-19
> **NoXiS said:**
> It seems to be an incompatibility with Python version 2.6 (which is likely your default version).

Make sure you have Python version 2.5 installed (don't worry multiple versions can be installed safely side by side).

```
sudo apt-get install python2.5
```

The executable /usr/bin/sopcast-player is just a script that runs the 'real' python program. You can edit this file and amend it to use Python v2.5.

```
sudo nano /usr/bin/sopcast-player

```

Change it so it looks like this.

```
#!/bin/sh
/usr/bin/python2.5 /usr/share/sopcast-player/lib/sopcast-player.pyc $@
```

Note the "2.5" after the "/usr/bin/python" at the start of the line. This just makes sure that Python v2.5 is used to run the sopcast-player. This works perfectly for me and all your menu shortcuts etc. will continue to work perfectly.

Hope this helps.

Thank you. It works very well now. 

Just one more question: how do I associate the Sopcast links in Firefox with Sopcast? For now, I have to manually copy the links and paste them in Sopcast.

---

### Post by bit2 on 2009-05-19
Thanks a lot

---

### Post by alex30002 on 2009-06-05
> **ptemple said:**
> For now, type:
python /usr/share/sopcast-player/lib/sopcast-player.py

This will work until he has fixed the .pyc files.

Phillip.

this worked for me too.i'm using 9.04.
thnaks

---

### Post by flyguy97 on 2009-09-20
All,

SopCast Player version 0.3.0 fixed the problems associated with running SopCast Player under Python 2.6. It is no longer necessary to use the prescribed workarounds. Thank you for your diligent efforts.

Cheers,
Jason

---

### Post by ssdt on 2009-11-09
One question does gsopcast play channels that i click on the browser? such as from myp2p.eu

---

### Post by flyguy97 on 2009-12-07
> **ssdt said:**
> One question does gsopcast play channels that i click on the browser? such as from myp2p.eu

I don't know if you are interested in using SopCast Player but I added that functionality in version 0.3.3. Either way, you can use the instructions at the bottom of [http://code.google.com/p/sopcast-player/wiki/Installation]("http://code.google.com/p/sopcast-player/wiki/Installation") to add sopcast link handling in Firefox.

Cheers,
Jason

---

