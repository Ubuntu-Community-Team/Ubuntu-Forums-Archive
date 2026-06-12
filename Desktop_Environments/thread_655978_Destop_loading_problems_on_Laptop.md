---
title: "Destop loading problems on Laptop"
date: 2008-01-02
forum: Desktop Environments
---

### Post by cmittle on 2008-01-02
I have a Toshiba Satellite A15-S129 laptop that I got for free from a friend, about 6 months ago.  Since I recently switched my desktop to Ubuntu I decided to do the same with this laptop.  I had it working normally for a long time, but now I'm having a problem on startup.

When I start my laptop it makes it to the login screen just fine, but when I login my desktop background will load and no toolbars will appear, no clicking on the desktop will work.  I've tried launching a terminal from my keyboard shortcuts, and the window appears but with a blue title bar and I can not see a command line.  If I press Ctrl Alt BkSp it brings me back to the login screen and from here I shut down and press the power button to try again.  The next time I login it may work,  It is hard to predict which time I start my computer it will actually work, it may be the first time or the third time.  Usually it takes no more than three tries.

One thing that I have noticed is that if I hear the drum roll when the login screen appears I know that it will work, and the rest of the music will play and the desktop will load as usual.  If I do not hear this drum roll, my background picture will load as I listen to the silence, and I get the symptoms described above.

I do not know what application, possibly X, that plays this music but I'm sure that this is directly related to my problem.
Could someone please tell me where to look for error logs and I will post them if that will help with diagnosis?

I would appreciate any help with this problem.
Thank you,
Cory

---

### Post by maher on 2008-01-02
Hi
Can you do the following
- ctrl+alt+F1
- Type your login  and then your password
- post the contents of the file  .xsession-errors
- you could also  try stopping gdm and then launching your desktop manually:
```

/etc/init.d/gdm stop
startx

```Also check the file /var/log/syslog for 
errors.

---

### Post by cmittle on 2008-01-02
My .xsession-errors shows a lot of this message
```
(update-notifier:8206): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
```

My /var/log/syslog file has a lot of the following message
```
Jan  2 17:54:53 cory-laptop kernel: [  836.992000] acx: got IV_ICV_Failure (crypto) IRQ(s)
```

After running /etc/init.d/gdm stop and then startx I saw the x for mouse cursor, and an even sprinkling of pixels had the light brown desktop color, and it froze there.  I could not do anything then so I had to hard shut down.  

Can anyone decode these error messages for me, or give me more ideas what I can do to try and diagnose this problem?

I would appreciate any help,
Thank you,
Cory

---

### Post by cmittle on 2008-01-04
Somebody has to be able to tell me what one of these errors means.

Please help me fix my laptop startup problems.

Thank you,
Cory

---

### Post by cmittle on 2008-01-08
Because the music associated with the graphical login of my GNOME system directly indicated whether or not it will load appropriately I think that there must be something wrong with one of the files associated with GDM on my computer.  Does anyone know what sequence of events happens when GDM is started?  Maybe this will get me started down the right path?

Thanks,
Cory

---

