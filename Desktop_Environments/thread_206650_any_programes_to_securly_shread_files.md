---
title: "any programes to securly shread files"
date: 2006-06-30
forum: Desktop Environments
---

### Post by cosmoshell on 2006-06-30
what program "if there are any" should i use to shred my importent files

---

### Post by neutro on 2006-06-30
Maybe "shred" could do the job. :roll:  :wink:

---

### Post by raptros-v76 on 2006-06-30
use dd

dd if=/dev/null of=<file>

---

### Post by jakez on 2006-06-30
"wipe" , its in the repositories, and there is also a nautilus script for easy handling:
[http://rob.pectol.com/myscripts/](http://rob.pectol.com/myscripts/)

greetz

---

### Post by anthro398 on 2006-06-30
Shred is not particularly secure.  If you'd like to learn more about secure deletion, you can see the [post]("http://forums.suselinuxsupport.de/index.php?showtopic=17430&hl=") I wrote on the Suse forums some time ago.  It discusses both secure deletion of files and overwriting free space.  I should have mentioned that the consensus seems to be that wipe is the top contender for secure deletion, metadata et al notwithstanding.

---

### Post by spnoe on 2007-01-26
From reading the threads and comments made, there would seem to be a real security risk.

It seems that we who are now using Ubuntu, could do with a good tool for deleting confidential information and ensuring that our computers can be secured.

In Windows I used Evidence Eliminator, which not only seemed to rid the computer of all information but freed up space.

It would be great to have a tool such as this. I for one would be most willing to pay for such a tool.

I would be intetrested to know if some one is working on this.

I am not very competant in Lynux and Ubuntu, so scripts are a no. no for me. I would much prefer a configured tool.
Any one be of help.

Thanks Steve

---

### Post by lopx8101 on 2007-01-27
I have had ubuntu installed for a couple of weeks now, just out of curiosity I thought I would visit Shields Up. What it showed came as a surprise. I am still pretty new to Linux and still have a lot to learn, and security seems to be at the forefront. How can I make my machine mere secure? Any ideas? The open ports are listed below.

[IMG]http://www.imagestation.com/album/pictures.html?id=2096162673[/IMG]
Port:111
Name: 	sunrpc
Purpose: SUN Remote Procedure Call
Description: 	
This port is used as a well-defined means for determining the ports upon which other services in the system are running. It is referred to as a "portmapper" because it provides a directory, or "mapping" between available services and their ports. This is similar to Microsoft's infamous DCOM DCE port 135.

Port : 621
Name: 	
escp-ip
Purpose: 	
ESCP
Description:

---

