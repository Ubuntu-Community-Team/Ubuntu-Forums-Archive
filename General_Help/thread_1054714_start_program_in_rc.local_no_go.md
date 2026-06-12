---
title: "start program in rc.local no go"
date: 2009-01-30
forum: General Help
---

### Post by tullmejs on 2009-01-30
I wanted to start vncserver after boot, so I typed

vncserver

into /etc/rc.local. That's what I use to type to start it manually. Vncserver does not start, and that is the qualifying reason for me to exasperate: why?

---

### Post by spcwingo on 2009-01-30
Have you tried writing a start script putting a symlink to it in rc5.d?  The script should look something like this:

```
#!/bin/sh

(&& vncserver) &
```

save it as vncserver.sh, create a symlink, and place it in rc5.d.  As far as naming the symlink, here's the readme from rc5.d:

> The scripts in this directory are executed each time the system enters
this runlevel.

The scripts are all symbolic links whose targets are located in
/etc/init.d/ .

To disable a service in this runlevel, rename its script in this directory
so that the new name begins with a 'K' and a two-digit number, where the
number is the difference between the two-digit number following the 'S'
in its current name, and 100.  To re-enable the service, rename the script
back to its original name beginning with 'S'.

For a more information see /etc/init.d/README.

I hope this helps you out.

---

### Post by tullmejs on 2009-01-30
Ah, the complexity. I hoped that what is written in rc.local was simply treated as if it was typed into Terminal after boot. 

I know that works for "mount", but that's different, I guess.

I ended up trying this approach instead - it came across as slightly less intimidating. [http://tillamookrage.blogspot.com/2007/12/autostart-programs-in-xfce-hardcore-way.html](http://tillamookrage.blogspot.com/2007/12/autostart-programs-in-xfce-hardcore-way.html)

Thank you.

---

### Post by spcwingo on 2009-01-30
Wow, I didn't know there was another autostart there too.  I had completely forgot, but there is also a way to do the same thing in your home folder (it just starts after you log in).  It should be under /home/yourname/.config/autostart.  That is exactly how I autostart wbar.

---

### Post by tullmejs on 2009-01-30
I see. Maybe that is more logical. But I'll keep this for now as it works :-) Thanks!

---

### Post by dcstar on 2009-01-30
> **tullmejs said:**
> I wanted to start vncserver after boot, so I typed

vncserver

into /etc/rc.local. That's what I use to type to start it manually. Vncserver does not start, and that is the qualifying reason for me to exasperate: why?

Programs that use the graphical system cannot be started in the non-graphical sub system without specific parameters relating to the graphical system.

---

### Post by tullmejs on 2009-01-30
Thank you. 

But hmm, in this case, starting VncServer by typing [FONT="Fixedsys"]vncserver[/FONT] in Terminal does work, and that would surely be considered non-graphical?

---

