---
title: "gdm will not stop"
date: 2011-07-09
forum: Desktop Environments
---

### Post by Bre Ntt on 2011-07-09
I've been trying to stop gdm and quite the x server, so I can start a fluxbox session. but

sudo /etc/init.d/gdm stop

will not work, and the command line gives me some advice to use stop(8) because it's been converted to an upstart job. Have no idea what that means, but nothing like 

sudo stop gdm
or 
sudo stop /etc/init.d/gdm

works either. 

I installed fluxbox, but it is not giving me the option to run it on the session start up in lieu of the regular GNOME (as the Ubuntu docs say it should.) 

What is going on here?

---

### Post by matt_symes on 2011-07-09
Hi

Try 

```

sudo service gdm stop
```

Kind regards

---

### Post by Bre Ntt on 2011-07-10
Thank you, but Doesn't work. 

Oddly, the only thing that seems to sort of work is

pgrep Xorg
then taking the number from that and put it into a kill

Although, it leaves just a blinking cursor, and no terminal. (Didn't try ctrl-z on it though, maybe that would have gotten back to the terminal)

And I think that it doesn't actually kill the process because doing another pgrep gives me a procss number. I don't know, thought, maybe it does and I just don't understand how pgrep works.

---

### Post by BicyclerBoy on 2011-07-10
You are running those commands from a console login ??
<ctrl>+<alt>+<f1>
And not a X screen terminal..

---

### Post by matt_symes on 2011-07-10
Hi

That is the correct command i gave you to stop gdm and hence X. 

Follow BicylerBoys advice and run it from the console and not from a gnome-terminal.

Kind regards

---

### Post by koleoptero on 2011-07-10
You can also use a tool like top or preferably htop to terminate the gdm process. But again from a tty.

---

### Post by Michielc on 2011-07-10
if the xserver is not configured correctly, zenity will start up an display a popup. You can't stop gdm while the popup is up.

fastest way to stop gdm:
```

ps aux | grep -i X | less

```
find the PID of usr/bin/X (usually the at the top of the list)
```

kill -9 PID

```

---

### Post by matt_symes on 2011-07-10
Hi

> **Michielc said:**
> if the xserver is not configured correctly, zenity will start up an display a popup. You can't stop gdm while the popup is up.


An interesting point and one that i was not aware of. 

I have a question though. 

Does it have to be a sigkill signal sent or can you send a sigterm ? sigkill's are, obviously, messy.

```
sudo pkill -f /usr/bin/X
```

Would this work ?

Kind regards

---

