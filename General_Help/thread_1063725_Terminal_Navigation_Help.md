---
title: "Terminal Navigation Help"
date: 2009-02-08
forum: General Help
---

### Post by flashSnap on 2009-02-08
Hi - 

I'm new to ubuntu and having trouble with the terminal. I've installed an application (Flash Media Server) and would like to execute the start command on it. But the application default install location is on the File System node in my file browser and so I've been unable to navigate to it?

It appears that when I launch the terminal window it defaults to my user directory. When I try to navigate to the root and execute commands - they no longer appear to work? It seems as though the commands are only enabled for my user account?

How then can I invoke commands on an application from the root? Also, this program is supposed to run with Apache. Perhaps I need to run it via Apache? Thanks. 

Peter

---

### Post by Nepherte on 2009-02-08
To navigate to the root:
```
cd /
```
To see what's in the current directory:
```
ls -l
```
To get more information on a command (like cd):
```
man cd
```

---

