---
title: "How to run X server commands remotely on other PC"
date: 2009-01-15
forum: General Help
---

### Post by MaximB on 2009-01-15
Hello.

I can connect to other machine using ssh and work on it.
I can even do "ssh XY" and run graphical programs - ON MY MACHINE.

But what if I want to connect to that other machine using ssh and run Xserver (graphical) commands on the remote machine ?

For example : when I use "ssh XY" and run the "xclock" command I see the graphical clock on my monitor which seems very logical, but what if I want the remote computer to "view" that graphical clock on his environment ?

---

### Post by Snow986 on 2009-01-15
did you try "ssh -X username@whatever"?

---

### Post by MaximB on 2009-01-15
> **Snow986 said:**
> did you try "ssh -X username@whatever"?

Same as XY , still runs on my monitor instead of the other machines monitor.

---

### Post by hyper_ch on 2009-01-15
what do you mean "run xserver commands remotely"?

If you do x11 forwarding for ssh yuo do run those remotely from the other computer.

---

### Post by MaximB on 2009-01-18
The X11 forwarding is enabled on both machines.
I just do not know if it's even possible to do what I want.

---

### Post by MaximB on 2009-01-20
I still need help, if possible.

---

### Post by hyper_ch on 2009-01-20
but what exactely do you want to do?

---

### Post by Slim Odds on 2009-01-20
I do this:```
ssh -Y name@host
```

And it works fine.

ssh will set the DISPLAY environment variable to point back to my machine. If I execute:```
xclock
```

It shows up on my local machine. I use it all the time.

---

### Post by Nepherte on 2009-01-20
It's not what he wants. He wants to ssh into a machine and run a program in a way so the gui is shown on the machine he logged in to. What he doesn't want is to ssh in a server and tunnel the gui to his own machine.

---

### Post by Slim Odds on 2009-01-20
> **Nepherte said:**
> It's not what he wants. He wants to ssh into a machine and run a program in a way so the gui is shown on the machine he logged in to. What he doesn't want is to ssh in a server and tunnel the gui to his own machine.

Sorry, misunderstood....

Use VNC

---

### Post by Ahadiel on 2009-01-20
When ssh'd into the machine
```
DISPLAY=:0.0 xclock
```

---

### Post by MaximB on 2009-01-21
Doesn't seems to work as expected.
I only see the Xclock on MY monitor.

> [maximb@xxx]$ ssh -XY root@mldev7
[root@mldev7 ~]# echo $DISPLAY
localhost:11.0
[root@mldev7 ~]# DISPLAY=:11.0 xclock  (works - but only on my monitor)
[root@mldev7 ~]# DISPLAY=:0.0 xclock
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: Can't open display: :0.0


---

### Post by Slim Odds on 2009-01-21
> **Ahadiel said:**
> When ssh'd into the machine
```
DISPLAY=:0.0 xclock
```

```
export DISPLAY=:0.0;xclock
```

Note: After you do this, everything X will be on remote display.

---

### Post by sedawk on 2009-01-21
In theory it works this way if user myuser is logged in to machine "remote"
and is running X11 there, e.g. has opened a Desktop enviroment:

```

ssh myuser@remote
export DISPLAY=:0.0
xclock

```

xclock will run on DISPLAY 0.0 on the machine "remote. Because
the user "myuser" is running xclock and X11 there should be no
security issues.
In the "good old times" this would have worked:
```

export DISPLAY=remote:0.0
xclock

```
xclock would run on your local machine but the clock is displayed
on the display of machine "remote".
This still works today, but you have to understand
X11 security and X11 must be configured to listen to the network.
(nowadays X11 by default doesn't accept incoming network connections).

(Things like ssh -X work because ssh does tricks with the DISPLAY
 variable.)

---

