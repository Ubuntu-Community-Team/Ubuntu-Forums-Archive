---
title: "[SOLVED] What the hell are those .EXEs and .DLL doing inside my Warsow folder?"
date: 2008-06-06
forum: Gaming &amp; Leisure
---

### Post by Dan_Dranath999 on 2008-06-06
Downloaded a Warsow zip from their website. I 've been playing an hour (No problems, just had to make the scripts executables)

But i noticed there's plenty .EXEs and .DLLs files in the folders. I suppose i can remove al the MS stuff, since ubuntu can't use them ¿right?

---

### Post by Sockerdrickan on 2008-06-06
yes, probably cross platform archive not 3 archives with different OS support.

---

### Post by DM was on fire! on 2008-06-06
Technically, Ubuntu can use them if you run the game in Wine.

But yeah, it sounds pretty safe to delete them to me. :)

---

### Post by Ozor Mox on 2008-06-06
Yes you can delete them if you want. Nexuiz does the same thing and packages the binaries for all platforms in one archive. Confused me a little at first, because I didn't spot the Linux executables on my first scan over the files!

---

### Post by Dan_Dranath999 on 2008-06-06
i'm gonna do it, man, i'm gonna do it, i swear i'll delete those little binary bastards with their little binary dumb smiles -they keep telling "oh, we are necessary files, don't remove us, your system will be useless" but i don't believe them, i don't believe a single word, they are just little binary LIERS who deserve to be erased along with their little dumb smiles! i will erase them! i swear i will!

---

### Post by Sockerdrickan on 2008-06-06
lol

---

### Post by lisati on 2008-06-06
The "one archive covers all OSes" might have a certain appeal in some situations (when you're personally responsible for multiple systems with multiple platforms) but surely it makes better sense to keep them separated, even if it means using some kind of directory/folder structure in the archive?

I've visited websites which have some degree of smarts about which OS and which browser I'm using, why not other software?

---

### Post by Vadi on 2008-06-06
It's laziness / lack of care on the packagers part to split up the archives, which is a really trivial thing to do.

---

### Post by Phenax on 2008-06-06
The reason they do that is because binaries are trivially small while data is 99% of the package. Why take twice the space on your web-server and make things more complex when you don't have to?

---

### Post by Vadi on 2008-06-07
Compared relatively to the other parts of the website, it's a pitifully small size. And having 3 archives to link instead of 1 I wouldn't describe as "more complex". You just press the link button 2 more times, lol.

---

### Post by Dan_Dranath999 on 2008-06-07
Well, if they are gonna make a "multi-OS-good for all" package, there should be a small "read me" text file with something like this...

a.- Windows users, you can delete these <file names> if you need to. 
b.- Linux users,  you can delete these <file names> if you need to.
c.- Mac users,  you can delete these <file names> if you need to.

---

### Post by Jedah on 2008-06-07
I wish I had this "problem" only...
There are some more serious issues with the Warsow universal archive:
[http://ubuntuforums.org/showthread.php?t=821387](http://ubuntuforums.org/showthread.php?t=821387)

---

### Post by Vadi on 2008-06-07
Just get it from getdeb: [http://www.getdeb.net/app/Warsow](http://www.getdeb.net/app/Warsow)

---

