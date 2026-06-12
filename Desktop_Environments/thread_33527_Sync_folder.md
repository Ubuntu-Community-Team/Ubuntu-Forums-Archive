---
title: "Sync folder?"
date: 2005-05-11
forum: Desktop Environments
---

### Post by Heliode on 2005-05-11
Hey guys,

I was wondering... you see, I have this one folder called 'school' on tree different computers; my worksation, my laptop and my server. I but stuff I do for homework in it, and at school I work in it on my laptop. 
Now, it would be great if those three folders could be bundled into one. I know with NFS I could put the folder on the server and mount it on the other two PC's, but then I wouldn't have access to it at school. I could use it to mount it from my server to my workstation though. 
Now, what I would need for this to work, is some program that allows me to synchronize the 'School' folder on my laptop with the one on my server when I get back from school. That way I wouldn't have different versions of the same document hanging around everywhere and I wouldn't have to look where I put the latest etc. etc... 

So if anyone has any suggestions I would be very grateful! Thanks in advance!

---

### Post by Jej on 2005-05-11
*unison* is exactly what you need ! ([http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/))

apt-get install unison unison-gtk


--jej

---

### Post by Alexander Kirillov on 2005-05-11
[QUOTE=Jej]*unison* is exactly what you need ! ([http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/))

apt-get install unison unison-gtk


--jej[/QUOTE]
 I am using unison, too - and quite happy about it.

---

### Post by Heliode on 2005-05-14
Thanks for that! unison seems to work out fine for me!
I can't manage to sync with a folder not on my pc however.. I have to mount the 'sync' folder manually when I get home and then have unison sync my school folder with that folder... but hey! It works! Thanks a lot!

---

### Post by Jej on 2005-05-17
You should use the remote rsync method, via ssh. It's far quicker than relying on a mounted network share.

--jej

---

### Post by Heliode on 2005-05-17
I tried, but it gave me an error that it couldn't connect to server. Maybe my syntax was just wrong. It asks me for the passphrase just like when i'm ssh-ing through console, but when I enter the (correct!) passphrase it says "Lost connection to server'. :(

---

