---
title: "Hey where i can get OpenGL ?"
date: 2009-04-03
forum: General Help
---

### Post by ariedry on 2009-04-03
Hey where i can get OpenGL ?  or somethng else like directX

Thank You.

---

### Post by ariedry on 2009-04-03
> **ariedry said:**
> Hey where i can get OpenGL ?  or somethng else like directX

Thank You.

i wanna run private server of flyff but when im runing , that happen :

  

[COLOR="Red"](its private server without GameGuard so no problems with GameGuard)[/COLOR]

                         [IMG]http://i301.photobucket.com/albums/nn61/ariedry/screenshot2.png?t=1238772987[/IMG] !                           

[COLOR="#ff0000"](its private server without GameGuard so no problems with GameGuard)[/COLOR]


**[COLOR="Lime"]SORRY FOR DOUBLE POST !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!![/COLOR]**

---

### Post by Therion on 2009-04-03
Have you tried Googling something along the lines of, say... Gosh, I dunno... "OpenGL download" maybe?

---

### Post by ariedry on 2009-04-03
yea i tried >_>
but i dunno if that the right 1 
and i only found somethng for windows and somethng cost money O.o
so...if any1 can post a link >.<
and not "Gosh, I dunno... "OpenGL download" maybe?"

---

### Post by Simian Man on 2009-04-03
To get the latest version of OpenGL, all you need to do is download the latest drivers for your video card.  The libraries themselves (libgl.so and so on), should already be installed.

---

### Post by ju2wheels on 2009-04-03
Opengl libraries and headers if you are compiling code:

```

sudo apt-get install freeglut3 freeglut3-dev glut3 glut3-dev libgl1-mesa-glx libgl1-mesa-dri libglu1-mesa libglut3

```

Are you getting any errors on the command line when you start it up? If you arent starting it from the command line then I would recommend doing so to see if it outputs any errors.

You can also run the following to see if you are missing dependencies:
```

ldd /full_path/flyff

```

---

### Post by ariedry on 2009-04-03
> **Simian Man said:**
> To get the latest version of OpenGL, all you need to do is download the latest drivers for your video card.  The libraries themselves (libgl.so and so on), should already be installed.


when i want to download the drivers its this does not support your operetaion system O.o

---

### Post by ariedry on 2009-04-03
Reading package lists... Done
Building dependency tree       
Reading state information... Done
freeglut3 is already the newest version.
E: Couldn't find package glut3

is that ok?


---------------------------------------------------------




[COLOR="Red"]_***Okay is see nothing help >_>***_[/COLOR]

---

### Post by Simian Man on 2009-04-03
> **ariedry said:**
> when i want to download the drivers its this does not support your operetaion system O.o

What graphics card do you have?  Did you enable restricted drivers with the little restricted drivers application?  Post the output of:
```

glxinfo | grep rendering

```

---

### Post by ariedry on 2009-04-03
its says "yes"

---

### Post by Simian Man on 2009-04-03
> **ariedry said:**
> its says : "direct rendering: Yes"

Then it sounds like you have OpenGL installed correctly.  I just searched for 'flyff' and its download link says it needs Windows.  If you're running this through wine, your problem almost certainly has nothing to do with OpenGL.

In fact, on the [wine page for this app]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=3253"), all of the tests are marked "garbage" which makes me think you will not be able to make this work.  Sorry about that.

---

### Post by ariedry on 2009-04-03
hmmm but its nothing to do with GameGuard so its should work , (its private server , its not eFlyff [The regular 1])
most of the online games cant work because of the GameGuard...

---

### Post by philinux on 2009-04-03
> **ariedry said:**
> hmmm but its nothing to do with GameGuard so its should work , (its private server , its not eFlyff [The regular 1])
most of the online games cant work because of the GameGuard...

Have you got any drivers enabled in system>admin>hardware Drivers.

You dont say which graphics card you have.

---

### Post by ariedry on 2009-04-03
its found Broadcom STA wireless driver and its not active

should i active it?

---

### Post by ariedry on 2009-04-03
omg same problem with GuildWars its should work great with wine O.o

---

### Post by asuastrophysics on 2009-04-03
i think the real question here is, where can you download directx for linux?

but the answer is no where of course :icon_frown:

ahhh i really wish microsoft hadn't bought out directx. who knows what linux would look like if it had directx support...
i can only dream

---

### Post by ariedry on 2009-04-03
dude...read all the topic then post

---

### Post by Simian Man on 2009-04-03
As I said, your problem is related to wine and not OpenGL or DirectX (which wine includes).  I'd suggest starting a new thread on why you can't get GuildWars to work.


[QUOTE=asuastrophysics]ahhh i really wish microsoft hadn't bought out directx. who knows what linux would look like if it had directx support...
i can only dream[/quote]

Most games use DirectX because of convenience and guaranteed graphics card support (ATI sucked at OpenGL until recently).  It's not really anything special.

---

### Post by ariedry on 2009-04-03
so i should reinstall wine? O.o

---

### Post by ariedry on 2009-04-03
Ok this is too much !!!!!!!! Its not even working for nexuiz !!!!!!!!!!!! Always the same problem with that weird screen!!!!!!!!!!!

---

### Post by ariedry on 2009-04-03
Heeelllppp!!!!!!!!!!!!

---

