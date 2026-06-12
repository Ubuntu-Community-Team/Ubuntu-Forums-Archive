---
title: "Where should I put applications I want available as commands?"
date: 2008-12-10
forum: General Help
---

### Post by OneSeventeen on 2008-12-10
I downloaded Eclipse from their website and it works great, but I'd like to actually store the application files somewhere other than my Downloads folder.

Where would be an ideal place to put the Eclipse folder so all I have to do is type "eclipse" to launch it?

(Plus I'd like it to be in the same place as other apps, for consistency)

I'm assuming I'll probably need to make a symlink to the actual eclipse script in a specific place as well.

Thanks in advance!

---

### Post by sayakb on 2008-12-10
Type:
```
echo $PATH
```That shows all those directories which are searched for executables. 
To add a folder to $PATH:
```
export PATH =$PATH:/new/path/to/add:/other/new/path
```

---

### Post by taurus on 2008-12-10
If you are the only one user on your system, then you can install it in your ~/bin and add that to your PATH in ~/.bashrc so you don't have to run the "export PATH=$PATH:~/bin" everytime you open a terminal.

---

### Post by HydroModeler on 2008-12-10
I followed this how-to from step 2 on (because I already had the java stuff installed) to install eclipse.  It work great and is clean and easy to understand.  Only problem was with the Icon path in the eclipse.desktop file, I had to change it, but I don't recall to what.

[http://www.ubuntued.com/?p=40](http://www.ubuntued.com/?p=40)

---

### Post by OneSeventeen on 2008-12-12
How do I add something to my .bashrc PATH?  (There isn't a default/example PATH varialbe in my .bashrc, at least not that I've found yet, I could be overlooking it)

I wound up just putting the entire eclipse folder in ~/bin/eclipse and I just put a launcher on the desktop for ~/bin/eclipse/eclipse

I'd still rather "install" my own files a little better, then again if I cared that much maybe I should learn how to build packages?

Thanks again!

---

