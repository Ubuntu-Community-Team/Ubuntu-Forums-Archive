---
title: "[TIP] CompizFusion and Dual Monitor: no decorations on second monitor?"
date: 2007-09-06
forum: Desktop Effects &amp; Customization
---

### Post by techstop on 2007-09-06
I have an nVidia 6600GT and 2 x 17" LCD monitors which I have set up as independent monitors. I could get CF installed, but I was always missing window decorations on the secondary monitor. 

I use a script that is run at startup to start compiz as well as emerald (I'm sure many of you have a similar script). The problem was that emerald was only being started on the primary screen. This was driving me nuts until I figured out how to start emerald on both screens. Here is the contents of my script;


```
#!/bin/bash
compiz --replace &
sleep 5
**emerald --replace --display :0.1 &**
sleep 5
emerald --replace
```

The bolded line is where I specify to start emerald on the secondary display. The last line starts it on the primary display. Save the script in your home directory (eg call it start-compiz) and make it executable;

```
chmod +x start-compiz
```

Then go to System -> Preferences -> Sessions. Click on "New" to add a new startup program and browse to the script you just made. Reboot and you're done!

I couldn't find this info anywhere, it was very frustrating to solve, hope it helps someone... :)

---

### Post by forestpixie on 2007-11-12
thanks - it certainly helped me \\:D/

---

### Post by hihihi on 2007-11-12
you could also make the script look like this:


#!/bin/bash
#switch between compiz 2 screens or 1 screen
VIDEOCARD1=`/bin/cat /var/log/Xorg.0.log |grep -c TV-0`
if [ "$VIDEOCARD1" = 0 ]; then
sleep 0
else
compiz --replace &
sleep 5
emerald --replace --display :0.1 &
sleep 5
emerald --replace
fi


this tells the PC to do this ONLY when a TV screen is detected.
you could change this according to your xorg.log
IT spares you abot 10 seconds on start when second screen (mine is a TV) is NOT connected. hope you like it.

---

### Post by forestpixie on 2007-11-12
I shall put this thread in my list of 'things'

When I get some time I'll start looking at the whole business of scripts and the rest of what you can do if you put your mind to it.

As it is I'm just pleased to have got this far without windows, it's been a good 6 months - and I've managed to help people as well - yea my second screen is a tv as well, but it's always connected.

Thanks for that

---

### Post by woodsby on 2007-11-23
What worked for me is adding "emerald --screen 1" to my list of startup programs in System>Preferences>Settings.  It was so simple, it only took me 4 weeks to figure out...

---

### Post by Louis Cypher on 2008-01-16
> **woodsby said:**
> What worked for me is adding "emerald --screen 1" to my list of startup programs in System>Preferences>Settings.  It was so simple, it only took me 4 weeks to figure out...

This helped me get window decorations on my TV!! THX

---

