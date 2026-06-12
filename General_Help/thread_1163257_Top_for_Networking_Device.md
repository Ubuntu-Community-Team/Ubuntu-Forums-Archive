---
title: "Top for Networking Device"
date: 2009-05-18
forum: General Help
---

### Post by yaroto98 on 2009-05-18
Is there any small script or binary out there that acts like top but for a networking device?  I've tried stuff like ntop, but they all seem way too bloated and more geared for servers, or business-like network management. All I want is something that can tell me what program is accessing the internet when my network monitor spikes (and preferably not have to set 20 different flags to do so). If there's something that sounds like what I'm looking for please let me know. If not I'm looking at making a script that does it for me. Currently just use netstat

```
netstat -tcp
```

and that usually helps out. But it's not the best looking output. Any help would be appreciated.

---

### Post by adrianx on 2009-05-18
I use *nethogs* for that purpose.

Install:
```
sudo apt-get install nethogs
```To run it:
```
sudo nethogs
```
You may want to run *nethogs -h* first and read through the instructions (only 9 lines to read :D)

---

### Post by yaroto98 on 2009-05-22
Nice! nethogs seems to be a good program. It has half of the functionality I've been looking for (caching # of bytes sent by what programs). Is there one out there that will tell you how much of your connection/pipe a program is using? I have grand ideas of making (and then giving to the community) a program that'll do both simultaneously.

---

