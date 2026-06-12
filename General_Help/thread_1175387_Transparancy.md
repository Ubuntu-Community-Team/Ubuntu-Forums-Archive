---
title: "Transparancy"
date: 2009-06-01
forum: General Help
---

### Post by NIKE. on 2009-06-01
I'm struggling to work out how to use transparancy on Ubuntu.
I have the newest version and can't work out how to do it.
I downloaded the Emerald Theme Manager and I load a them into it and double click it but  nothing happens..

:(

---

### Post by Legace on 2009-06-01
Does Compiz work for you?

---

### Post by mcduck on 2009-06-01
> **NIKE. said:**
> I'm struggling to work out how to use transparancy on Ubuntu.
I have the newest version and can't work out how to do it.
I downloaded the Emerald Theme Manager and I load a them into it and double click it but  nothing happens..

:(

You will also have to set Compiz to *use* Ememrald. Simply installing it will not do the trick.

Press Alt-F2 and run "emerald --replace" to start it.

If that works, you can then open CompizConfig Settings Manager (install it if you haven't done that already), go to window Decoration-plugin's settings and set the "Command" to "/usr/bin/emerald" to make Compiz use Emerald as it's default decorator.

---

### Post by NIKE. on 2009-06-01
> **mcduck said:**
> You will also have to set Compiz to *use* Ememrald. Simply installing it will not do the trick.

Press Alt-F2 and run "emerald -replace" to start it.

If that works, you can then open CompizConfig Settings Manager (install it if you haven't done that already), go to window Decoration-plugin's settings and set the "Command" to "/usr/bin/emerald" to make Compiz use Emerald as it's default decorator.
I did that and it's still the same.. When I double click a theme in Emerald nothing happens.

Is there meant to be a save button on Compiz???

---

### Post by mcduck on 2009-06-01
> **NIKE. said:**
> I did that and it's still the same.. When I double click a theme in Emerald nothing happens.

Is there meant to be a save button on Compiz???

Sorry, that's "emerald --replace" (with two dashes).

You might also have to run that *after* you have changed the theme in Emerald Theme Manager. I remember when I used Emerald it wouldn't refresh the theme without reloading Emarald.

If you still have problems you can try running that command in a terminal to see the error messages (but be aware that if you do this Emerald will close as soon as you close the terminal window).

---

### Post by NIKE. on 2009-06-01
Still not working. D:

---

### Post by nikgare on 2009-06-01
Which garphic card do you have?
If it's a newsih ati or nvidea, you'll need to install the proprietry drivers via **System->Administration->Hardware Drivers**
This wil download and install the driver for you, and then after a reboot you enable effects via the Appearences option.

---

### Post by mcduck on 2009-06-01
> **NIKE. said:**
> Still not working. D:

Are your desktop effects (System/Preferences/Appearance, Visual Effects-tab) working otherwise?

Did you try running the command in a terminal to catch the error messages? Could you please post them here, as simple "not working" doesn't really give us any information to work with.. :)

---

### Post by NIKE. on 2009-06-01
> **mcduck said:**
> Are your desktop effects (System/Preferences/Appearance, Visual Effects-tab) working otherwise?

Did you try running the command in a terminal to catch the error messages? Could you please post them here, as simple "not working" doesn't really give us any information to work with.. :)
Visual effects are on none. 
I get message; "Desktop effects could not be enabled" when trying to change it.

My card an Intel 82865G Integrated Graphics Controller. Is this why it's not working?

---

### Post by tad1073 on 2009-06-01
You need to enable the driver in:
```
Menu>System>Administration>Hardware Drivers
```

---

### Post by NIKE. on 2009-06-01
It says "No proprietary drivers are in use on this system.".

---

### Post by mcduck on 2009-06-01
> **NIKE. said:**
> It says "No proprietary drivers are in use on this system.".

Yes, you need to get the desktop effects working to be able to use Emerald.

I've understood that there are some problems with Intel graphics drivers in 9.04, see this thread for more info & help about that: [http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

After you got the graphics driver sorted out you should be able to enable desktop effects and Emerald will start working as well.

---

### Post by nikgare on 2009-06-01
This might help, it has various ways to fix the problem:
[http://webupd8.blogspot.com/2009/05/reverting-xorg-video-intel-driver-of.html](http://webupd8.blogspot.com/2009/05/reverting-xorg-video-intel-driver-of.html)

---

