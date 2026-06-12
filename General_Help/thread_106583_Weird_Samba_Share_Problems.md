---
title: "Weird Samba Share Problems"
date: 2005-12-21
forum: General Help
---

### Post by Mike Eckman on 2005-12-21
I am running Ubuntu 5.1 AMD64 and have successfully setup file and printer sharing (Samba) between my Ubuntu box and my 2 WinXP computers.

I have no problem accessing the XP machines from Ubuntu and I can see my Ubuntu computer from my XP machines.  I mapped my /home folder and have access to the files in it.  I can see all the folders inside my /home folder and can access the files in some of them.

I have a /home/Music folder and a /home/News folder.

For whatever reason, I cannot see any of the files in there.  If I go into Nautilus and move them from those folders to /home, I can see them from the Windows machine.  

But I cant see anything in those two folders from my Windows computer.

I am using share level access in SMB.CONF and I have my Ubuntu user permissions set to 644.  I tried 777 and it made no difference.  I compared the permissions between a file I can see and one I can't see, and theyre the same.

What gives?  Please help me understand this.

---

### Post by zoiks on 2005-12-21
Does it have something to do with this? :

from [http://www.oreilly.com/catalog/samba/chapter/book/ch05_03.html](http://www.oreilly.com/catalog/samba/chapter/book/ch05_03.html)

[I]5.3.2.10 map hidden

DOS uses the hidden attribute to indicate that a file should not ordinarily be visible in directory listings. Unix doesn't have such a facility; it's up to individual programs (notably the shell) to decide what to display and what not to display. Normally, you won't have any DOS files that need to be hidden, so the best thing to do is to leave this option turned off.

Setting this option to yes causes the server to map the hidden flag onto the executable-by-others bit (0001). This feature can produce a rather startling effect. Any Unix program that is executable by world seems to vanish when you look for it from a Windows client. If this option is not set, however, and a Windows user attempts to mark a file hidden on a Samba share, it will not work - Samba has no place to store the hidden attribute! [/I]

---

### Post by Mike Eckman on 2005-12-21
> **zoiks]Does it have something to do with this? :

from [http://www.oreilly.com/catalog/samba/chapter/book/ch05_03.html](http://www.oreilly.com/catalog/samba/chapter/book/ch05_03.html)

[I]5.3.2.10 map hidden

DOS uses the hidden attribute to indicate that a file should not ordinarily be visible in directory listings. Unix doesn't have such a facility said:**
> 

None of my permissions were changed, but just to be sure, I added 

map hidden=no to my share section and it made no difference.

Any other ideas?

---

