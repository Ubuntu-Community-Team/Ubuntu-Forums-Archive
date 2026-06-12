---
title: "Can not enable Visual effects PLEASE HELP!!!"
date: 2008-02-28
forum: Desktop Effects &amp; Customization
---

### Post by Punkshot on 2008-02-28
hey guys, it's my first time using ubuntu, and i truely do like it, i would really like to enable these visual effects though.

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)


thats whats coming up for my graphics card...

please help!!!!

---

### Post by Kasa on 2008-02-28
tell us the problem, and how it happens.
the more info the better.

---

### Post by Punkshot on 2008-02-28
well the problem is that when i go into my propteries or what not to enable my custom visual settins it will start to load them then say the desktop settings can not be applied.

so i have compiz and want to use it's effects but i cant till i enable the effects, but it will not allow me to do so.

---

### Post by Yellow Pasque on 2008-02-28
Make sure your /usr/bin/compiz is set up properly. See the first part of this post: [http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

Then, go to the terminal and type 'compiz'. This should give you a much more specific error  message if the above tip does not fix your issue.

---

### Post by Punkshot on 2008-02-28
its not compiz thats my problem.

even if i didnt have it installed it would still give me the error that my desktop settins could not be applied whenever i try to enable visual effects.

---

### Post by Punkshot on 2008-02-28
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by Kasa on 2008-02-28
What gfx card are you running ?

---

### Post by Punkshot on 2008-02-28
i posted what graphics card it was up top if thats what your asking.

---

### Post by Yellow Pasque on 2008-02-28
Hmm, both the intel and i810 driver should be whitelisted. Can you post your /etc/X11/xorg.conf and the output of this command:
```
cat /usr/bin/compiz | grep WHITE
```

---

### Post by Kasa on 2008-02-28
Did you install the Driver ?
I would say envy but your not using a Nvida or a ATI
To understand whats happening I will look up your card for info.
Someone els might of had problems with that card.

---

### Post by Punkshot on 2008-02-29
WHITELIST="nvidia intel ati radeon i810"
        for DRV in ${WHITELIST}; do

thats what i got for the command you gave me.

---

### Post by Job_314 on 2008-02-29
I was having issues with that earlier today as well. The Ubuntu "accelerated" drivers didn't do squat... so I fragged them and used Envy instead. Worked great. Compiz looked beautiful.

But! after installing a Compiz patch, my desktop effects got disabled yet again, and wouldn't re-enable. At that point I downloaded Emerald, and Fusion-Icon. After I installed Fusion-icon, I right clicked it on the taskbar, and went to "*Compiz Options* ->" and checked "*Indirect Rendering*" and they enabled right away :)

Good luck!
-Austin

**Edit:** here's the [link to Envy](http://www.albertomilone.com/nvidia_scripts1.html). Just in case you're interested.

---

### Post by Punkshot on 2008-03-09
even after i got envy, and all those other things listed its still not enabling

---

### Post by smartboyathome on 2008-03-09
I had a ton of problems with my intel 940 and compiz. It doesn't work real well with in imo.

---

