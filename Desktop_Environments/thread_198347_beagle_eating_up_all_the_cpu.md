---
title: "beagle eating up all the cpu"
date: 2006-06-17
forum: Desktop Environments
---

### Post by jordilin on 2006-06-17
I don't know why beagle is consuming all my cpu. I do a top command and beagled is eating 100% of cpu. I installed Dapper Drake the day it was released and I haven't had any problem until now. 
Is anyone experiencing the same problem?

---

### Post by jongkind on 2006-06-17
This may be related to an issue with indexing of MSWORD files (WV1 issue). Below you can find a link with more info. Unfortunately Dapper does not offer an update version of wv or wv1,

[http://www.beagle-project.org/Optional_prerequisites]("http://www.beagle-project.org/Optional_prerequisites")

---

### Post by jordilin on 2006-06-17
It could be, but I don't have any M$ Word file in my computer. I only use OpenOffice. so,....One thing is that I just installed the mplayer mozilla plugin, and perhaps this could be the reason; but I've desintalled it and I'm experiencing the same problem.

---

### Post by jongkind on 2006-06-17
One thing you can verify is whether the WV package is installe (Synaptic wv version 1.0.2-0.1). If so, remove it and verify whether you have same high CPU usage.

Another point is that the performance of Beagle increases by adding extende attributes in the fstab file. See: [http://www.beagle-project.org/Enabling_Extended_Attributes]("http://www.beagle-project.org/Enabling_Extended_Attributes")

If this all does not work you can consider to remove the hidden .beagle folder from your home directory. The consequence is that everything has to be indexed again

---

### Post by jordilin on 2006-06-17
Well, I haven't anything named wv installed. So, I've regenerated the .beagle folder and it has worked again. It has to reindex everything again, but it doesn't eat all my cpu. It seems as if something went wrong in the .beagle folder. 
thanks

---

### Post by Mike-97470 on 2006-07-08
I had the same problem with beagled eating my CPU.  I just trashed .Beagle and logged out/in-- the .Beagle was back, but the CPU is idling at 0% instead of humming at 100%.

---

### Post by jordilin on 2006-07-11
This issue appears every now and then. The solution is killing the beagle daemon and then deleting the folder .beagle. Once done, switch on the beagle daemon and solved. The main problem is that it has to reindex all your home again, but it's not a big issue though.

---

### Post by matrix3D on 2006-09-11
I can't believe that here we are MONTHS after Dapper has gone "final" and this problem still exists.

---

