---
title: "Neither Compiz or Beryl works for me."
date: 2007-08-22
forum: Desktop Effects &amp; Customization
---

### Post by donteatsoap7 on 2007-08-22
I have them both installed with the managers and all that but neither one works.
What do I do to have amazing desktop effects?

---

### Post by creedog on 2007-08-22
do you have 3d acceleration working..... try running glxgears and tell me what happens

---

### Post by donteatsoap7 on 2007-08-22
I pressed Alt F2 and typed that in but nothing happened.

---

### Post by Dark Star on 2007-08-22
What's you system specs ? What error ? or did you get WSOD ?  Plz be clear while asking :)

---

### Post by donteatsoap7 on 2007-08-22
Well, I don't really know my specs but I know I have 250 MB of memory and an Intel Pentium 4 processor with 2.2 GHz, I'm using a Dell Inspiron 2400, and it's old.
I didn't get any erros and idk what WSOD is.

---

### Post by Dark Star on 2007-08-22
WSOD is white screen of death :) Btw That's a minimum requirement of Gnome .. So running Beryl should be difficult.. The thing stucks now on the VGS if you have 64 MB VGA like mine then it will else it is difiicult.. Though we have similar spec in ram but my VGA is decent for CF/Beryl ;)

---

### Post by donteatsoap7 on 2007-08-22
So basically I can't run either one?

---

### Post by Dark Star on 2007-08-22
Not impossible.. but depends on VGA :) Beryl should run fine.. Early I was geting WSOD in Beryl but now it runs fine on same specs even Cf runs gr8 here ;)

---

### Post by donteatsoap7 on 2007-08-22
Alright. So...how do I do it?

---

### Post by Dark Star on 2007-08-22
Do have beryl / Cf installed ? If so try opening 1 at a time.. Start with Beryl then .. If everything works fine test it by Ctrl+Alt+ Mouse 1 so that to see if its active or not :) The Desktop will turn into cube and vice versa :)

---

### Post by donteatsoap7 on 2007-08-22
I opened the settings and configured what I wanted but nothing happened.

---

### Post by Dark Star on 2007-08-22
Naa do not open settings open Beryl Manager :) not settings manager :D

---

### Post by donteatsoap7 on 2007-08-22
This is all that comes up when I right click the diamond.

---

### Post by Dark Star on 2007-08-22
Now Press Ctrl+ Alt+Left Mouse Button and move it .. See the desktop is moving into Cube or not :)

---

### Post by donteatsoap7 on 2007-08-22
No. It' doesn't move.

---

### Post by fantasyspirit91 on 2007-08-22
Are you using dual monitors?

None of the effects worked for me when I had 2 monitors, but when I disabled one of them, they worked again. If you are using 2, trying disabling one.

---

### Post by donteatsoap7 on 2007-08-22
Nope. Only one monitor.

---

### Post by donteatsoap7 on 2007-08-22
Bump...

---

### Post by donteatsoap7 on 2007-08-22
I just unistalled both of them and only installed compiz this time but I still get the error message:

donteatsoap7@ubuntu:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

---

### Post by zero244 on 2007-08-22
Beryl may not be turned on.....right click on the diamond and scroll down to select desktop manager. Make sure beryl is selected.
If Beryl and Compiz wont start its probably because you don't have 3d support running.
One way to get 3d support is download and install Automatix2.....click on drivers and install them. Then reboot.
Type Glxinfo in terminal and see what it shows.
You can also type beryl in terminal and get some info.
Good Luck hope you can get it to work. Beryl is super cool and fun to use.
Plus you can really impress the girls with all the desktop tricks you can do.

---

### Post by donteatsoap7 on 2007-08-22
donteatsoap7@ubuntu:~$ Glxinfo
bash: Glxinfo: command not found

---

### Post by creedog on 2007-08-22
> **donteatsoap7 said:**
> I pressed Alt F2 and typed that in but nothing happened.


do it in a terminal window so that you can see the output of the command...

---

