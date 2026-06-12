---
title: "Error when starting program from command line"
date: 2006-07-19
forum: Desktop Environments
---

### Post by DX 00 on 2006-07-19
I just recently got Home Bank [http://www.gnomefiles.org/app.php?soft_id=1424](http://www.gnomefiles.org/app.php?soft_id=1424) 

I extracted the content into my desktop and there was an application file. When I clicked the file, it opened the program and everything worked well. Then I wanted to put it into /usr/share/homebank and create a menu link that would point to it.
After creating the link on my menu and I open the program, the program starts but the images that the program uses don't show up.

I tried running the program from the command line and I get the same error. The program dosn't crash and it works well, just the images don't get loaded. When I open the file manager and go to /usr/share/homebank and double click the application file, the program starts working with graphics. 

I don't know what could be the problem. I change the permissions of all the files under the homebank to 777 and I still have the same problem. Anybody got a hint?

Thx in advance.

---

### Post by Sinner on 2006-09-27
The binary package is just for evaluation purpose.
The exe contained in try to find images and locale in . directory, this is why you have trouble.

Please install properly from source code:
./configure
make
make install

:mrgreen:

---

### Post by DX 00 on 2006-09-27
Thx, i'll try that.

---

