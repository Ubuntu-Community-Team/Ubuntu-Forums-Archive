---
title: "Restore ATI default Xorg?"
date: 2010-09-16
forum: Desktop Environments
---

### Post by Cuco3 on 2010-09-16
Can someone guide me through restoring the default Xorg settings for ATI cards?

---

### Post by Grenage on 2010-09-16
Hi there,

What problems are you having, or what config do you need?  One can generate a default config using:

```
sudo Xorg -configure
```

It probably won't work with X running, so you'll need to shut that down first.

---

### Post by Cuco3 on 2010-09-16
Thanks. I won't bother describing the problem since last time I did no one ever responded and it's pretty complicated, so I'll just ask for the help I need and hopefully you guys will be kind enough to answer.

Just know that I'm trying to get my xorg file back to the ati defaults.

How would I shut down X?

---

### Post by Grenage on 2010-09-16
Ctrl-Alt-F1 and log in.  Think I 'think' it can be done with:

```
sudo service gdm stop
```

Feel free to describe your problem, and I'll offer any help I can.

---

### Post by Cuco3 on 2010-09-16
doesn't get it back to default but thanks anyway.

---

### Post by Grenage on 2010-09-16
It should create a new xorg.conf.new (I think).

If you can elaborate on the problem, we can work out a custom config.

---

### Post by Cuco3 on 2010-09-16
I think my ATI xorg settings are conflicting with the gnome-display-properties xorg settings. I'm pretty sure that's the problem because when I log in I get a message from gnome-display-properties saying that the resolution couldn't be configured or something.

I'm trying to get a dual monitor setup going. I had it working fine before, main monitor in the left and spare monitor on the right. I switched the monitors around on my desk and need to get the monitors configured so that it's main on the right and spare on the left.

I'm pretty much giving up hope already. I mean, who is the genius that said "let's allow two different programs to write to Xorg so we can see our users have fun troubleshooting with their display settings in order to add to the Linux experience."

Want to know something even better? Apparently there's two different monitor display settings on my computer: one for the login screen and one for my user account. more troubleshooting for me, yay...

---

### Post by Cuco3 on 2010-09-16
thanks for leaving right after I told you I won't explain it because the other guy just left after I explained it to him.

what a jerk some people are...

---

### Post by realzippy on 2010-09-16
You did not mention using the FGLRX driver..
(had a look at your other thread).
There is a ATI GUI for monitor settings (Catalyst Control Center or something)....why using Gnome's display GUI tool?


BTW Gnome's display tool does not write to *xorg.conf*.It is *monitors.xml*..

---

### Post by Grenage on 2010-09-16
Ah I see, ATI dual monitor fun.  I assume you used the catalyst tool to modify xorg.conf?  While I've only got Nvidia machines with dual screens, I'm happy to bungle my way around with you, to try and work something out.

Most of the xorg.conf settings are easy, but I'm not sure what the ATI commands are for the dual-screen section, under Display.

> **Cuco3 said:**
> thanks for leaving right after I told you I won't explain it because the other guy just left after I explained it to him.

what a jerk some people are...

Seriously?  I'm at work, and reply to posts during down-time.  Few of us can sit here pressing *refresh* every 5 seconds.

---

### Post by 3rdalbum on 2010-09-16
Just delete the /etc/X11/xorg.conf file to go back to defaults.

---

### Post by realzippy on 2010-09-16
> **3rdalbum said:**
> Just delete the /etc/X11/xorg.conf file to go back to defaults.
OP runs fglrx.....

---

### Post by Grenage on 2010-09-16
> **realzippy said:**
> OP runs fglrx.....

I agree; if it wasn't being used before, it would explain a lot.

---

