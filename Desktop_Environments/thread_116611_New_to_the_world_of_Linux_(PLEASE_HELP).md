---
title: "New to the world of Linux (PLEASE HELP)"
date: 2006-01-13
forum: Desktop Environments
---

### Post by zimele on 2006-01-13
Hey All i am what you call a converted person i had windows but now i joined Linux and chose Ubuntu and that makes me a genuine NEEWBIE now i need help in these questions

1.  I have an ADSL connection it works perfectly on my windows Based Computer but on my linux Machine it does not respond but the funny thing if i go to Network tools within linux and run a trace route it works fine i get a response in any of these tools, ping, netstat, tracert, etc. I am able to connect to other computers on my network but when i go to firefox to try to connect it does not connect to the webpage i want even though i can trace it. i tried using the pppoeconf command but after doing the search it tells me that the search is complete without finding any concerntrator of pppoe my current connection on my ADSL is pppoe thats what i use on my Windows Machine. please offer me a step by step guide.

2. i downloaded some tarballs now i want to be able to use these tools and i need to know the steps to follow to compile them and make them into that specific tool could you supply me with a breakdown on what steps to follow cause i did some research on this and i was able to extract and when i try to complie them using the -c command it gives me this (Acdtrux) what does this mean?

:smile: If you could please offer your assistence to me i will be greatful!:smile:

---

### Post by kaamos on 2006-01-13
Are you sure it is not just a firefox problem? Try some other programs to narrow down the possible causes.

For installing software, this link is pretty good: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by Sef on 2006-01-13
Two things you can do to check:

1) Open a terminal (Applications ----> Assessories ----> Terminal) and type this in:  ```
sudo apt-get update
``` and see if that fixes the problem.

2) The other thing to do is go download another browser - Konqueror.  To do that, do this: ```
 Applications ----> Add Applications -----> Internet -----> click on the arrow -----> click the other arrow to get into the submenu ----> scroll down to konqueror ----> check konqueror ----> click apply ---->click apply again.
```  

After it installs check to see if you can access the net with it or not.  If you can then firefox has a problem.  If you have to do the same thing as firefox to get it to work then the problem lies elsewhere.

---

