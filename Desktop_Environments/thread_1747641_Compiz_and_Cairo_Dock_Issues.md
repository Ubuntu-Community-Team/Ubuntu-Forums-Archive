---
title: "Compiz and Cairo Dock Issues?"
date: 2011-05-02
forum: Desktop Environments
---

### Post by jporter328 on 2011-05-02
First of all, Compiz doesn't work at all. For example, I check wobbly windows and I shake several windows and none of them will wobble. I also tried the water affect and several other things and none of them work. I have uninstalled and reinstalled several times.

Also, Cairo dock has a nasty black box around it, with or with out Open GL.

Could it be possible cairo dock has a black box because compiz isn't working properly? I've seen that people say you need compositing turned on for it to work, and since compiz isn't cooperating, maybe thats it? Help is greatly appreciated.

I have an Nvidea card and the ubuntu recommended driver for it.

---

### Post by Version Dependency on 2011-05-02
Sounds like Compiz isn't running.  Your probably falling back to Metacity.  What version of Ubuntu?  What desktop environment?  What Nvidea card?

---

### Post by jporter328 on 2011-05-03
> **Version Dependency said:**
> Sounds like Compiz isn't running.  Your probably falling back to Metacity.  What version of Ubuntu?  What desktop environment?  What Nvidea card?

Sorry for the lack of info thought my account here is a year old I didn't use ubuntu alot until now. 

11.04 latest release 
I'm not using Unity, so Classic Ubuntu
and Nvideo 7130m? I'm not quite sure on the number but its the mobile graphics card. My laptops about 3 years old.

---

### Post by jporter328 on 2011-05-04
no body can help me?

---

### Post by 23dornot23d on 2011-05-04
As a start point ..... Enter this in a terminal ...... and post the results

**/usr/lib/nux/unity_support_test -p**

also

**uname -a**

This is what mine shows ........
```

keith@keith-Aspire-7730ZG:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9300M GS/PCI/SSE2
OpenGL version string:  3.3.0 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
keith@keith-Aspire-7730ZG:~$
keith@keith-Aspire-7730ZG:~$ uname -a
Linux keith-Aspire-7730ZG 2.6.39-020639rc4-generic #201104191410 SMP Tue Apr 19 15:45:56 UTC 2011 i686 i686 i386 GNU/Linux


```Then we can go from there ...

---

### Post by jporter328 on 2011-05-04
Ok here is /usr/lib/nux/unity_support_test -p

```
acob@jacob-HP-Pavilion-dv2700-Notebook-PC:~$ /usr/lib/nux/unity_support_test -pOpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7150M / nForce 630M/PCI/SSE2/3DNOW!
OpenGL version string:  2.1.2 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

```
 and the other one:
```
Linux jacob-HP-Pavilion-dv2700-Notebook-PC 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux

```

---

### Post by 23dornot23d on 2011-05-04
ok when you get into the desktop ..... can you run Nvidia-Settings

and do a screenshot ...... or let me know if its working

Menu

Administration >>> Nvidia X server settings

should look something like this

[IMG]http://img36.imageshack.us/img36/8157/nvidiag.jpg[/IMG]

---

### Post by THE CARTER on 2011-05-04
I had the same issue.  You might want to make a ubuntu 11.04 live cd and upgrade your existing 11.04 install to a factory default 11.04 install. This fixes any compiz issues.

I had the same problem and this is the only fix I could find.

---

### Post by jporter328 on 2011-05-04
ok i didn't know which tab to screenshot so here is the main one 


[IMG]http://i52.tinypic.com/1z2g2so.png[/IMG]

---

### Post by 23dornot23d on 2011-05-04
ok you have it running ..... thats good ..... it tells me you are running in the right mode to run compiz.

if you do this ...... what happens

alt + f2

compiz --replace


I can get wobbly windows and the cube ..... on my system but it disables others ...... you may have to
make some compromises here ....... until they get everything sorted .....

---

### Post by jporter328 on 2011-05-04
yes! it seems to be working now.. thank you very much! :D :D :D

---

### Post by 23dornot23d on 2011-05-04
Ok good to know ....... ;) 

can you mark it as solved in the **[COLOR=Red]Thread Tools[/COLOR]** at the top of this page please

---

### Post by hossdozero on 2011-05-06
is there a way to have "compiz --replace" run at startup?

---

### Post by belkinsa on 2011-05-07
> **hossdozero said:**
> is there a way to have "compiz --replace" run at startup?

You can just make a start-up thingy in the Start-up Programs.  System<Prefs.< Starup Apps

---

