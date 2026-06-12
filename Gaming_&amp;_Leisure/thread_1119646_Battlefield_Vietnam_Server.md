---
title: "Battlefield Vietnam Server"
date: 2009-04-08
forum: Gaming &amp; Leisure
---

### Post by SSamiK on 2009-04-08
I'm trying to install and run a BFV gameserver on one of my ubuntuboxes, however I'm having a couple of problems. First of, the .run file i've downloaded will not extract on the box I first planned to use, but it extracts as expected on another. (it fails with a MD5 error) Anybody else had this problem? 

Now for the real problem... On the box I've gotten it to extract and install it just wont start. 
Here is what I've done:


Started with downloading the server from [here]("http://www.fileplanet.com/138224/130000/fileinfo/Battlefield:-Vietnam-Dedicated-Linux-Server-v1.21")

Then I extracted/installed it like this:
```
chmod +x ./bfv_linded-v1.2-20041006.1506.run
$ ./bfv_linded-v1.2-20041006.1506.run
```
I choose to install into /opt/games/ 

Everything finishes as expected, and I edit mods/bfvietnam/settings/serversettings.con and mods/bfvietnam/settings/maplist.con

then I try to start the server:
```
$ ./start.sh +statusMonitor 1./start.sh: using dynamically linked binary
$ 

```

And nothing more happens... Any hints on what to do?

---

### Post by SSamiK on 2009-04-09
A small update... It does seem like it starts for a few seconds, but then it crashes or just quits. 

Nobody out there who still plays Battlefield Vietnam?

---

### Post by SSamiK on 2009-04-13
One last update from me:

I've gotten nowhere real fast with this one... I actually had to install windowze on a old box I had lying around and use the windows server that worked with no problem at all. Not at all what I wanted, but life isn't always just. ;) 

If, however, anyone out there do get the linux server running please share!;)

---

