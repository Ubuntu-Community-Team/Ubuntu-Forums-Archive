---
title: "GDM will not stop - GDM is already running"
date: 2006-06-05
forum: Desktop Environments
---

### Post by ironfistchamp on 2006-06-05
I want to shutdown gdm and just get into console. I know I can use Ctrl Alt F1 but I need to stop gdm to install some drivers. When I issue the command gdm -stop it says 

   GDM is already running. Aborting!!

This happens with any gdm command I issue. What's going on.

Also what are kernel source/headers and where do I get them? I'm using the 2.6.15-23-386 kernel. Can anyone help?

Thanks 

Ironfistchamp

---

### Post by NESFreak on 2006-06-05
it's gdm-stop (without the space)

---

### Post by ironfistchamp on 2006-06-05
hmm I did that and it said unknown command. I'll try again knowing me I mistyped. Thanks for the reply. What about the source/headers thingy?

Thanks 

Ironfistchamp

---

### Post by NESFreak on 2006-06-05
i just copied it from
man gdm

---

### Post by sparkov on 2006-06-05
Try:

```
sudo /etc/init.d/gdm stop
```
to stop, and

```
sudo /etc/init.d/gdm start
```
to start.

---

### Post by linear on 2006-06-06
"sudo /etc/init.d/gdm stop" doesn't work in Dapper; this is a confirmed [bug]("https://launchpad.net/distros/ubuntu/+source/gdm/+bug/47320").

Try "sudo killall gdm" to stop gdm, or "sudo killall -HUP gdm" to stop and restart.

---

### Post by ironfistchamp on 2006-06-07
Thanks for the help.

Ironfistchamp

---

### Post by sparkov on 2006-06-07
```
sudo /etc/init.d/gdm stop
```

appears to work fine for me, however just

```
/etc/init.d/gdm stop
```

does not.

I also have no problem restarting it after stopping using sudo contrary to what is pointed out in that link.  I didn't even know you could stop gdm without using sudo to be honest.

---

