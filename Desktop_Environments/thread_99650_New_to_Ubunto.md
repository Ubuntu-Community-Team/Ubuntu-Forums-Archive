---
title: "New to Ubunto"
date: 2005-12-06
forum: Desktop Environments
---

### Post by clarenjon on 2005-12-06
Just intalled Ubuntu on an old box and I have a question. Ubuntu is asking for a command after I enter a user id and password. Is this normal ? Checked the FAQ and I did'nt see anything surrounding this. Authenication appears to be quite simple, although I cannot. What am I missing here ?
Thanks in advance for any assistance !!

---

### Post by Qrk on 2005-12-06
Was your login graphical? If not, the command is 
```
startx
```
which may cause some error messages; depending on how old your system is.

Assuming I understood your question, it shouldn't be normal. After logging in, Gnome should start up. However, if your system is too old for a graphical desktop, or if you preformed the server installation, you will be brought to the command line. 

If you did get a graphical login, then I don't understand your question at all. Please explain a little more. ;)

---

### Post by clarenjon on 2005-12-06
After entering my user id and password I get:userid@unbunto:~$ 
Is it asking for a command to authenticate ?

---

### Post by clarenjon on 2005-12-06
The system I've installed to really isnt so old.... HP vectra P3. Thanks for the reply. What's your take ?

---

### Post by funkydan2 on 2005-12-06
No - you've already logged in.

Try the command "startx" and tell us what happens.

---

### Post by clarenjon on 2005-12-06
and no it wasn't graphical. Just text. Didn't get a response with start x

---

### Post by clarenjon on 2005-12-06
startx = command n found :(

---

### Post by funkydan2 on 2005-12-06
Right at the beginning of the installation, did you type anything at the first screen or just press enter?

I'm not 100% sure, but I think you may be able to move forwards by running
"sudo apt-get install ubuntu-desktop" (or "sudo apt-get install kubuntu-desktop if you've installed from the kubuntu CD).

---

