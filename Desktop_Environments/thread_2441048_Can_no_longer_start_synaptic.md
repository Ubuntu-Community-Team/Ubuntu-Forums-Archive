---
title: "Can no longer start synaptic"
date: 2020-04-18
forum: Desktop Environments
---

### Post by pgte32 on 2020-04-18
Need help correcting... I can no longer start Synaptic:

peter@meerkat:~$ sudo synaptic
[sudo] password for peter: 
Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: Could not connect: Connection refused


(synaptic:16917): Gtk-WARNING **: 10:03:25.535: cannot open display: :0

Note: Ubuntu 18.04.4 LTS

---

### Post by ajgreeny on 2020-04-18
In 18.04 you should not use ***sudo synaptic***; sudo is for command line utilities only (until 19.10 or later, where it will work apparently without potential problems).

Try either using the menu system, where synaptic should be found, or go to ***Applications*** if using gnome.

If you want to try terminal again use command ***synaptic-pkexec*** which is what the menus use.

---

### Post by pgte32 on 2020-04-18
Thanks for the quick reply. Still get the same error:

peter@meerkat:~$ sudo synaptic-pkexec
[sudo] password for peter: 
Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: Could not connect: Connection refused


(synaptic:18521): Gtk-WARNING **: 10:31:43.628: cannot open display: :0

Note: I am starting it from the command line because starting from an icon, prompts for a password and then does nothing.

---

### Post by ajgreeny on 2020-04-18
No, not ***sudo synaptic-pkexec***, just ***synaptic-pkexec***.

Try that, or why not the menu/Applications system as I suggested.

I am assuming you can use sudo for other commands such as ***sudo apt update*** and that you are an admin user to whom sudo is available.

Show us the output of command ***groups***

---

### Post by pgte32 on 2020-04-18
[COLOR=#000000]I am starting it from the command line because starting from an icon (menu/applications) , it prompts for a password and then does nothing.

[/COLOR]
Here is the output from the most recent attempt:

peter@meerkat:~$ synaptic-pkexec
Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: Could not connect: Connection refused


(synaptic:19011): Gtk-WARNING **: 10:52:25.369: cannot open display: :0

---

### Post by tea for one on 2020-04-18
> **pgte32 said:**
> Need help correcting... I can no longer start Synaptic:

peter@meerkat:~$ sudo synaptic
[sudo] password for peter: 
Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: Could not connect: Connection refused


(synaptic:16917): Gtk-WARNING **: 10:03:25.535: cannot open display: :0

Note: Ubuntu 18.04.4 LTS

Are you running a session **Ubuntu on Wayland**?

If you log out and select an Ubuntu session (using the gear wheel), hopefully Synaptic will load normally.

---

### Post by pgte32 on 2020-04-18
Ah, good tip. That seems to work!

 A few questions... What is the difference between selecting Ubuntu or Wayland? How would I tell which one I am using while logged on?

---

### Post by tea for one on 2020-04-18
Open a terminal and try this

```
echo $XDG_SESSION_TYPE
```

As for the differences between an Ubuntu session and an Ubuntu on Wayland session, I wish I could help succinctly but, regrettably, it is above my level of technical incompetence.;)

---

### Post by pgte32 on 2020-04-18
Thanks for your help... synaptic now working when logged on using Ubuntu as opposed to Wayland. I will carry on...

---

### Post by tea for one on 2020-04-18
> **pgte32 said:**
> Thanks for your help... synaptic now working when logged on using Ubuntu as opposed to Wayland. I will carry on...

Splendid - Please mark the thread as solved to help others with the same problem.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

