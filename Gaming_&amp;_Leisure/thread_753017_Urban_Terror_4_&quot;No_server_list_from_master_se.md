---
title: "Urban Terror 4 &quot;No server list from master server&quot;"
date: 2008-04-12
forum: Gaming &amp; Leisure
---

### Post by poisonblack on 2008-04-12
Hullo.!
Posting this here since both UrT forums and main site won't open up here from last 2-3 days.
I had UrT working fine in Kubuntu for about a week after downloading it.But it now shows "No server list from master server" whenever I try to get new server list.I tried all settings like modifying Punkbuster, GUIDS, etc. at the bottom of screen to get the list, but to no use.Any help.?

---

### Post by ioan123 on 2008-05-22
I have exactly the same problem - did you find any solution by any chance?
Ioan

---

### Post by Steve413z on 2008-05-22
I've noticed this problem in the past, it seems if you start a new game, (as a host) and then go to the server lists, I have this problem, but not if I go directly to the server list

---

### Post by soxs on 2008-05-23
This is a bug of UT itself.
Workaround: If you do not get any new serverlist by pressing <GetNewList>, close UT and start it again. Do NOT press multiple times on <GetNewList> until you get any error (otherwise every server will be shown twice or n-times instead only once). You may have to cloes/rerun this up to n times.
But if you got once a list, never ever again press <GetNewList>!!
Just update it,.. this is how it works for me atm.

---

### Post by Sf4tt on 2008-06-11
There is a simple way to fix this problem. When the UrT master server (master.urbanterror.net) don't return any server you can change your master server in the config. file.

The path should be /home/USER/.q3a/q3ut4/q3config.cfg

So:

```

sudo gedit /home/USER/.q3a/q3ut4/q3config.cfg 
```

Then search this string in that file:

```

seta cl_master "master.urbanterror.net"

```

Change it with:

```

seta cl_master "master.quake3arena.com"

```

Save.

The quake3arena's master server load also the servers of quake 3. So the game will need a little more time to load all servers. But your UrT GUI will show you the UrT servers ONLY.

Anyway, after a few days, I advise you to comeback to the urban terror master server (master.urbanterror.net). Usually this problem is solved in a short time. 

Have fun with UrT!

Bye!

---

### Post by Sf4tt on 2008-06-12
Good, i'm happy this is an useful post, bye!

---

### Post by cristo-father on 2008-07-27
Thanks.

---

### Post by perfran on 2008-08-21
> **Sf4tt said:**
> 
```

sudo gedit /home/USER/.q3a/q3ut4/q3config.cfg 
```

no need to sudo ;)

---

### Post by PopDog! on 2008-12-26
Also helps this if you going ingame menu and choose "Setings" -> "Restore defaults"... You get new server list. And you will write down your config into userconfig.cfg, then no problem with config will reset :P

And yes, dont click on Get new list or smth, only do update! :)

---

### Post by Dedoimedo on 2008-12-26
I've found the following to work:

Click only once on Get new list button. Wait ...
Restart UT ...
Shuffle the game type from all back to all and try again ...
Seems to work for me, without touching configuration files, and I play almost daily.

Dedoimedo

---

### Post by Logansky on 2009-03-27
Do any of these fixes work for Windows Vista PC's. I've tried everything so far but to no avail.

---

### Post by Dedoimedo on 2009-03-28
Do you have firewall rules in place that prevent UT from connecting to the server?
Dedoimedo

---

### Post by WanderingSnake on 2009-06-23
I too am having this problem. I've tried everything suggested in this thread and others, and nothing is working. The only option left is that it is because I am behind a router, but there is nothing I can do about this.

---

### Post by psmaster on 2010-01-23
try pressing tilde "~" at the menu
and type:
```

/cl_master master.quake3arena.com

```
This will set the master server from master.urbanterror.net to master.quake3arena.com
The reason this works is because the master.urbanterror.net master server changes IP addresses occasionally and because of ISP's DNS caching, it takes awhile to update it. the quake3arena.com master server is a bit slower, so you can try switching back to the urbanterror.net one in a few days

---

### Post by tomek_wap on 2011-11-20
hi,

none of the above solutions work for me.
tried diff. server lists, port is forwarded to my local IP add.
no local FW.

still nothing. the list is not loading. but it shows a message that it is loading an X number of servers, and that number changes, so there must be some connection to the internet/server list.

---

### Post by Perfect Storm on 2011-11-20
Please check the date of the thread.


Thread closed.

---

