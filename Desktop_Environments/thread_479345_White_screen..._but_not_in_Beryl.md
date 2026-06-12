---
title: "White screen... but not in Beryl"
date: 2007-06-20
forum: Desktop Environments
---

### Post by nikohs on 2007-06-20
I have the newest kernel of Ubuntu and partitioned off 15 gigs of my ample hard drive to test it out. In doing so I stumbled across a feature of the desktop much like running beryl (i.e. windows "wobble", cube desktops ...). As soon as I turned this feature on my desktop went white. I cannot get rid of the white, nor can I access my menus. I am able to get into my command line, but i dont know what to change!!!! HELP 

P.S. I already configured my video card... so thats not it!

---

### Post by tgoose on 2007-06-20
On the command line, try

```
ps -A | grep beryl
```

ps -A will list all running processes,

the | character "pipes" the output of this into grep

grep only returns lines that match whatever you write after it (i.e. "beryl" in this instance.)


So that command as a whole lists all processes running with beryl in them. In my case I get
```

 5699 ?        00:00:00 beryl-manager
 5794 ?        00:00:31 beryl

```
You shouldn't get beryl-manager, but if you do it probably doesn't matter. Your numbers will be different.

 You can then stop it from running by reading the number at the front and putting that into a "kill" command.

```
kill 5794
``` for me.

---

