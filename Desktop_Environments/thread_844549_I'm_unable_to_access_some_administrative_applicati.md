---
title: "I'm unable to access some administrative applications."
date: 2008-06-29
forum: Desktop Environments
---

### Post by brodae on 2008-06-29
I'm unable to use software sources, as well as the update manager. I've been having problems with this for a while, but I was able to find some workarounds. Those aren't working anymore. They consisted of going into administrative applications that I COULD open, unlocking them with the "unlock" button, followed by opening the program I wanted to open in the first place.

I also learned about sudo synaptic, as well as sudo apt-get install early in the game, and applied those methods to yield the results I desired. But, now, I'm screwed. It's just not working, and I have a myriad of updates available, and it won't let me download them when I click "Install Updates."

:(

---

### Post by brodae on 2008-06-29
Just so you know, I learned I'm able to access these applications through the terminal. I discovered their commands via the search applet, and in the terminal I just added sudo to the beginning of them. However, I want to access them through the GUI which shouldn't be a problem.

---

### Post by aysiu on 2008-06-29
I don't know if this is related or not, but for graphical applications, you should use *gksudo* and not *sudo*. So it would be ```
gksudo synaptic
``` not *sudo synaptic*. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Can you paste the command ```
gksudo synaptic
``` in the terminal and then post back any error messages you get back here?

---

### Post by brodae on 2008-06-29
Actually, when I use gksudo, it does the same problem as before. Sudo, however, does work.

---

### Post by aysiu on 2008-06-29
> **brodae said:**
> Actually, when I use gksudo, it does the same problem as before. Sudo, however, does work.
What's the error message you get?

---

### Post by brodae on 2008-06-29
I don't get an error message. It just says, "Starting Administrative Application" and then stops and doesn't do anything.

---

### Post by aysiu on 2008-06-29
What do you mean by *doesn't do anything*?

Does it go to the next prompt in the terminal? That is, something like this? ```
username@ubuntu:~$ **gksudo synaptic**
username@ubuntu:~$
```

---

### Post by brodae on 2008-06-30
It says "Starting Administrative Application" and then that taskbar item goes away, and nothing else happens. It doesn't go to the next prompt. It just sits there waiting for the application.

---

### Post by brodae on 2008-07-17
Well, it's fixed now. I don't know what did it, but it's working. It was probably fixed by a system update.

---

### Post by Kouki on 2008-07-18
And now I have your problem.  Yes, flashes up in the taskbar and then nothing.  Problem is that I've not updated in a while and I think the source I was using is no more.  Therefore I can't update until I change my update server using the software sources application and choosing best server.

---

### Post by phantomjoker on 2008-07-18
try launching the program from the termial - that way it will tell you why it doesnt open.

---

### Post by Kouki on 2008-07-19
I'm afraid I don't know how to open 'software sources' from the terminal

---

### Post by Kouki on 2008-07-19
Hopefully this fixes it, I've logged in as root and the upgrade manager had the option of upgrading to 8.04 so I clicked upgrade and it seems to be downloading now.  Hopefully it will sort itself out following the dist upgrade.

I'm also hoping my laptops wireless card will automatically work following the upgrade to the latest distribution.

---

