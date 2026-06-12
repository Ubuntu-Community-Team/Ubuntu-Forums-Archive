---
title: "How do i get Emerald manager in ubuntu"
date: 2009-11-08
forum: Desktop Environments
---

### Post by psyboy55 on 2009-11-08
i have the extra effects on but i cant get the emerald manager. I looked for it in add/remove programs but i cant find it. i think i need to add a repostitory what do i add? what do i do after that? i have ubuntu 8.04. do i need to change the repository if i upgrade?

---

### Post by howefield on 2009-11-08
Fire up Synaptic Package Manager and install from there.

---

### Post by psyboy55 on 2009-11-08
What do i look for? i searched for beryl and emerald and it came up with nothing.

---

### Post by howefield on 2009-11-08
You said you were on 8.04 ?

Should be in the default repository.

Load up Synaptic and press the reload button, then search for emerald. If it still doesn't come up, you can download the .deb file from here

[http://packages.ubuntu.com/hardy/emerald](http://packages.ubuntu.com/hardy/emerald)

and install. You might need one or two dependancies also, which you can also get from the link above.

---

### Post by psyboy55 on 2009-11-08
Ok i still cant find it. Do u think it will hurt if i upgrade to 8.10 and maybe to 9.04 then 9.10? im gonna try the download option

---

### Post by psyboy55 on 2009-11-08
ok when i downloaded it and tryed o install it, it had an error.

Error: Dependency is not satisfiable: libemeraldengine0

---

### Post by howefield on 2009-11-08
Download it from here,

[http://packages.ubuntu.com/hardy/libemeraldengine0](http://packages.ubuntu.com/hardy/libemeraldengine0)

Like I said above, there might be one or two dependancies you will need if they are not already installed.

---

### Post by oldos2er on 2009-11-08
> **psyboy55 said:**
> ok when i downloaded it and tryed o install it, it had an error.

Error: Dependency is not satisfiable: libemeraldengine0

 Make sure you have the universe repository enabled.

---

### Post by psyboy55 on 2009-11-08
Yes it worked! i made sure the universal thing as checked and i downloaded emerald. Now how do get the 3d cube and stuff? i dont think emerald will do that. what do i need?

---

### Post by howefield on 2009-11-09
Assuming you have a graphics card which supports the desktop effects...

Install compizconfig-settings-manager with Synaptic Package Manager.

Navigate to “System > Preferences > CompizConfig Settings Manager.
Click on “General Options” and then the Desktop Size tab, Change the first slider to your required number of desktops. 

Then check the Desktop Cube option. and the Rotate Cube option. You can choose the indivual settings for each of these as well.

Click on Cube Reflection and Deformation to set the cube to sphere or cylinder if you prefer, or leave unchecked if you want the cube.

---

### Post by psyboy55 on 2009-11-09
Ok i figured everything out. thanks everyone!

---

