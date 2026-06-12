---
title: "having problem using compiz"
date: 2011-06-29
forum: Desktop Environments
---

### Post by agrawalmohit1989 on 2011-06-29
some effects wont work.

and m unable to launch compiz fusion icon 

m using ubuntu classic

---

### Post by nzjethro on 2011-06-29
Hi there, and welcome to the forums. This is a very vague problem. Did it start after installing anything/upgrading etc? What were you doing when it started?

What happens when you run
```
compiz --replace
```

To provide us with more info, try these commands:
```
cd
wget http://blogage.de/files/4359/download -O compiz-check
chmod +x compiz-check
bash compiz-check
```

---

### Post by agrawalmohit1989 on 2011-06-29
[COLOR="red"]after using compiz --replace it gives[/COLOR]


compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png


[COLOR="Red"]after using compiz check it gives[/COLOR]

Gathering information about your system...

 Distribution:          Ubuntu 11.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
 Driver in use:         vesa
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card. 

[COLOR="red"]and one more thing after compiz replace mini max and close buttons disappeared from window toolbar..
[/COLOR]

---

### Post by FormatSeize on 2011-06-29
Install the proper drivers for your graphics card.

---

### Post by agrawalmohit1989 on 2011-06-29
have installed drivers 

first i installed it directly using "additional drivers"

still it was not running so i installed it manually also after downloading from ati site.

---

### Post by nzjethro on 2011-06-29
> **agrawalmohit1989 said:**
> [COLOR="red"]after using compiz --replace it gives[/COLOR]
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png


Does the file /usr/share/gdm/themes/Human/ubuntu.png exist? I'm not sure how this would affect the other plugins, but that's a fairly specific error message.

---

### Post by MG&amp;TL on 2011-06-29
I know this is going to sound depressing and reflect badly on Ubuntu, but graphics drivers/desktop effects can be really quite difficult to get working, so do you really need the effects? To this day, I still can't get mine to work, Ubuntu's a great system, but if you've tried what the Ubuntu documentation has to offer to get the effects working, it's probably a lot of bother; ignore the effects, file a bug report, come back to it in a month.;)

Of course, if you're like me, you'll not be able to keep your paws off anything that 'needs fixing', so make up your own mind. :D

I'm just saying it can be difficult, and I'm not convinced it's one of the better features of Ubuntu. 

Oh, and I'm a relative newbie, too, so if one of the real experts says something to the contrary, believe him/her.

---

### Post by nzjethro on 2011-06-29
> **MG&TL said:**
> I know this is going to sound depressing and reflect badly on Ubuntu, but graphics drivers/desktop effects can be really quite difficult to get working, so do you really need the effects?

I guess this makes me realise what I should have asked the OP earlier. Did you at some stage have Compiz up and running successfully, and then it crashed? Or has it never worked properly? The two problems will require quite different solutions. :)

---

