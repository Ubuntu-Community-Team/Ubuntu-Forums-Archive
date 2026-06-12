---
title: "Conky on mini 9 with 8.04"
date: 2009-02-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Arndtwe on 2009-02-19
Hi, so I have recently installed and been playing with Conky. Nifty little thing. And I wanted it to start when my computer turns on, so I put it in my start menu. All seems to go well, when I boot up, Then login. The stage between loging in and loading the desktop, I see Conky loading. It shows up while the screen is still black. It is loading before my desktop. Doesn't seem like a problem, till the desktop loads. Now its gone. If I open my processes it is running, but if I want to be able to see it I have to end it the process, then restart it. It's almost as if the desktop "sits" on top of conky, it's still there and running, I just can't see it. Amnyone have any suggestions or solutions?

---

### Post by notwen on 2009-02-19
Conky is loading before your DE/WM finishes loading.  What we will do to get around this is make a simple bash shellscript to make conky wait XX seconds before starting.

Open Gedit and copy/paste the following into your new file:
**note: change 5 to the # of seconds you want to wait before conky starts and if you use a conky config other than the default you will need to change conky to conky -c .yourconfig**
```

#!/bin/sh
sleep 5
conky &

```

Save this new file as say **.conkystart** in your home folder.

Now let's proceed to make this shellscript executable, open up a terminal and copy/paste the following:

```

sudo chmod a+x .conkystart

```

Once this is done, you can add your .**conkystart** shellscript to the startup processes and reboot.  Please post if you have any questions and/or problems.  =]

---

### Post by Arndtwe on 2009-02-19
Thank you so much!! This worked perfectly :-). You guys here on the forums are great!

P.S. this thread can be marked as [SOLVED] how ever you do that!!

---

### Post by notwen on 2009-02-20
Np, glad it worked for you.  =]

---

