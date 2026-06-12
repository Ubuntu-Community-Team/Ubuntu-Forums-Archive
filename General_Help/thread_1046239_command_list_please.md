---
title: "command list please?"
date: 2009-01-21
forum: General Help
---

### Post by fanmoko on 2009-01-21
i'm just an explorer to ubuntu and i'm not that "techy" person who knows the whats and hows of ubuntu. i just want to ask a list of commands (basic commands) that i can enter in the terminal just to have an appreciation and little knowledge of ubuntu.. For example, if i wish to shutdown the computer, the command that i'll enter in the terminal would be: shutdown -h now   ...so for other basic functions, kindly give me a list of the commands? thanks.

---

### Post by taurus on 2009-01-21
This, [http://www.ss64.com/bash/](http://www.ss64.com/bash/), could keep you busy for a while.

---

### Post by drs305 on 2009-01-21
Here are a couple to start you off:
Edit: Taurus beat me to the first link.  ;-)

[An A-Z Index of the Bash command line for Linux.]("http://www.ss64.com/bash/")

Ubuntu Cheat Sheet:
[http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/]("http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/")

---

### Post by oldos2er on 2009-01-21
> **fanmoko said:**
> i'm just an explorer to ubuntu and i'm not that "techy" person who knows the whats and hows of ubuntu. i just want to ask a list of commands (basic commands) that i can enter in the terminal just to have an appreciation and little knowledge of ubuntu.. For example, if i wish to shutdown the computer, the command that i'll enter in the terminal would be: shutdown -h now   ...so for other basic functions, kindly give me a list of the commands? thanks.

 ```
apropos shutdown
```

 will show you each command related to 'shutdown' in some way. Replace 'shutdown' with whatever you need info on. 

 Also, hitting Tab twice will display every possible command. Hit 'q' to exit the list.

---

### Post by Sprut1 on 2009-01-21
> **oldos2er said:**
> ```
apropos shutdown
```

 will show you each command related to 'shutdown' in some way. Replace 'shutdown' with whatever you need info on. 

 Also, hitting Tab twice will display every possible command. Hit 'q' to exit the list.

And when you get the commands type:

```
man shutdown
```

To see all options.

---

### Post by vanadium on 2009-01-21
If you search "introduction bash" or "linux terminal tutorial"some newbie-friendly tutorials will show up, pleasant to start learning. Excellent guides can be found here: [http://tille.garrels.be/training/](http://tille.garrels.be/training/) "Introduction to Linux: A hands on guide" is featuring for many years on the linux documentation project's site. It includes introductory chapters on bash and as a whole provides a comprehensive and already quite thorough overview of the gnu/linux operating system. If you are lucky and can read dutch, then there is a "light" version of these notes based off that work and tailored for Ubuntu.

---

