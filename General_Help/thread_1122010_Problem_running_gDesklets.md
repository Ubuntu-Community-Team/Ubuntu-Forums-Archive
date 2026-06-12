---
title: "Problem running gDesklets"
date: 2009-04-10
forum: General Help
---

### Post by Shawn425 on 2009-04-10
Hello, I've recently installed FluxBox on my Ubuntu 9.04 system, and I'm enjoying it so far, I stumbled upon a program that allows me to run other programs on my desktop, like clocks and system monitors,
I installed it via the Synaptic Package Manager, and all went well
but now when I use the "gdesklets" command in the terminal I get this error: bash: /usr/bin/gdesklets: /usr/bin/python2.5: bad interpreter: No such file or directory
I've tried Googling it and I couldn't come up with anything about this, so I decided to ask these forums, and hope that you can help me. I'd like to thank you for reading my thread.

-Sean.

---

### Post by cschulte22 on 2009-04-23
You can fix this by just installing python2.5.  Type this in a terminal window:

```
sudo aptitude install python2.5
```

Now gdesklets should run without a problem.

---

