---
title: "[Alice American McGee's] Wine gives Installation iKernel.exe could not be installed?"
date: 2006-05-25
forum: Gaming &amp; Leisure
---

### Post by patrick295767 on 2006-05-25
[Alice American McGee's] Wine gives Installation iKernel.exe could not be installed?
  
I got such error msg : 
[http://patrick295767.sitesled.com/Linux/prob-alice-installation.png](http://patrick295767.sitesled.com/Linux/prob-alice-installation.png)
  via doing  : 
wine Setup.exe
  
Someone has already got such error msg ?
  
Thank you, 
 
Patrick

---

### Post by patrick295767 on 2006-05-25
I used cedega with /mnt/hdc/alice.exe
 
and got this better error msg 
[http://patrick295767.sitesled.com/Linux/cedega-cdrom-alice.png](http://patrick295767.sitesled.com/Linux/cedega-cdrom-alice.png)
  
how can I set / say that the original cdrom of alice game  is located at /mnt/hdc
to make it read like it could be under windows ??
  
Thank you !!

pat'

---

### Post by Ishamael on 2006-05-25
[QUOTE=patrick295767]I used cedega with /mnt/hdc/alice.exe
 
and got this better error msg 
[http://patrick295767.sitesled.com/Linux/cedega-cdrom-alice.png](http://patrick295767.sitesled.com/Linux/cedega-cdrom-alice.png)
  
how can I set / say that the original cdrom of alice game  is located at /mnt/hdc
to make it read like it could be under windows ??
  
Thank you !!

pat'[/QUOTE]
I have no idea how to do it in Cedega, but to fix this in Wine do:
1. Enter winecfg
2. Click drives
3. Make sure /cdrom is listed as a drive, otherwise add it to the list
4. Click "Show advanced", and set the type as CD-ROM

Not sure that is the problem, but it helped me when I had a similar problem.

---

### Post by patrick295767 on 2006-05-27
I have found !!
  
I need to play around with my ex_ files

[B]who has windows still ?? Could I have : 
[COLOR="Red"]unpack.exe[/COLOR] file ??[/B]
  
to unpack this ikernel.ex_ file 
  
Thnak you very much !!
  
Patrick
======== done !! :KS :-) ========
  
I found !! (no need of unpack.exe :-) !!) 
 I got expand.exe from installation cd of windows ...
  
then, did : 
  
1/  
wine expand.exe ikernel.ex_   ikernel.exe
  (no dosbox !!)
  (also for the seccond file finishing by _)  
  
2/ Made an ISO (trick conform) of the original cd of alice via K3B
Took with wine the program WINSO
I did re-build the ISO file of alice Mc gee program  cd01
  
3/
Then installation flied !!
  
4/ 
in the config file of cedega/wine 
(/usr/lib) 
we can modify the drives and add CDROM 
    
  Installation worked with working on it !!
  
GReetings

---

### Post by patrick295767 on 2006-05-28
Thread SOLVED !!
  
  =======================
By the way, that would be nice if programers add the :
          expand.exe
  
into the wine installation !
(apt-get install wine)  ...

---

### Post by Perfect Storm on 2006-05-28
Funny, when I had AAMG on Cedega I hadn't all the trouble. But it's a while back with another cedega engine.

---

### Post by patrick295767 on 2006-05-28
[QUOTE=Artificial Intelligence]Funny, when I had AAMG on Cedega I hadn't all the trouble. But it's a while back with another cedega engine.[/QUOTE]
  
Yes Indeed !!
  It worked fine finally after looking a bit in details (v4sthg).
   
====
Today, I am getting crazy with my nfs server/client
super slow
I need an expert in nfs !!
 I am getting crazy with that...
I am gonna make a new thead about it, cos I am out of any ideas ... nothg. 
I tried everythg.
You know a lot artificial int. about nfs ?
(my problems to be continued there : [http://www.ubuntuforums.org/showthread.php?p=1061694#post1061694](http://www.ubuntuforums.org/showthread.php?p=1061694#post1061694))

---

