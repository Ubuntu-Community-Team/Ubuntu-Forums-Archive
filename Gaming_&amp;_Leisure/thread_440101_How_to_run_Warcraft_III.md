---
title: "How to run Warcraft III?"
date: 2007-05-11
forum: Gaming &amp; Leisure
---

### Post by danny71 on 2007-05-11
Hi there,

Does anybody know how to run Warcraft III with Wine?

When I do it after instalation, the system collapses. ](*,)

---

### Post by tgm4883 on 2007-05-11
Any error messages?  I have it installed just fine on my system

---

### Post by Corlyn on 2007-05-11
Make sure that you check winhq if there are some tricks to install. Also make sure that you have the latest version of wine(helped me with C&C 3). [http://appdb.winehq.org/appview.php?iAppId=897](http://appdb.winehq.org/appview.php?iAppId=897)

---

### Post by danny71 on 2007-05-12
There are no error messages, the system simply collapses after the screen resolution have changed automatically a few times so I have to set it again as 1280*1024.

---

### Post by tgm4883 on 2007-05-12
Did you remove the movies folder?

---

### Post by danny71 on 2007-05-12
I didn't remove the movies folder.

---

### Post by danny71 on 2007-05-12
After removing the movies folder, the game runs very slow, and I cannot see the mouse cursor.

---

### Post by tgm4883 on 2007-05-12
But it's progress, right?

---

### Post by tgm4883 on 2007-05-12
Do you have your 3d driver loaded?

---

### Post by danny71 on 2007-05-12
> **tgm4883 said:**
> Do you have your 3d driver loaded?

How can I know this? Only I know that my system has an ATI X600 RADEON card.

---

### Post by Enverex on 2007-05-12
Have you read the AppDB page? I'm sure that'll tell you what to do if you need to do anything special to get it to work. As TGM said you also need to make sure you have fully accellerated graphics card drivers loaded else the system will just crawl.

---

### Post by tgm4883 on 2007-05-12
do this in terminal and post the results

```
glxinfo | grep direct 
```

---

### Post by danny71 on 2007-05-12
> **Enverex said:**
> Have you read the AppDB page? I'm sure that'll tell you what to do if you need to do anything special to get it to work. As TGM said you also need to make sure you have fully accellerated graphics card drivers loaded else the system will just crawl.

I read it, and I downloaded the new version of Wine, but I don't know how to install it after download.

---

### Post by danny71 on 2007-05-12
> **tgm4883 said:**
> do this in terminal and post the results

```
glxinfo | grep direct 
```

home@home-desktop:~$ glxinfo | grep direct
Unknown device ID 5B62, please report. Assuming plain R300.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
direct rendering: Yes

Does it mean something?

---

### Post by tgm4883 on 2007-05-12
Are you running the 3d driver from the repos or from the ati website?

---

### Post by tgm4883 on 2007-05-12
also run winecfg and see if on the graphics tab that direct3d support is hardware and not something else

---

### Post by danny71 on 2007-05-12
> **tgm4883 said:**
> Are you running the 3d driver from the repos or from the ati website?

I downloaded ATI drivers from ATI site, but I don't know how to install it.

---

### Post by danny71 on 2007-05-12
> **tgm4883 said:**
> also run winecfg and see if on the graphics tab that direct3d support is hardware and not something else

Direct3d support is hardware.

---

### Post by Rizado on 2007-05-12
Tried to run it in opengl mode? It'll probably work alot better than in d3d mode.

```
wine war3.exe -opengl
```

---

### Post by danny71 on 2007-05-12
> **Rizado said:**
> Tried to run it in opengl mode? It'll probably work alot better than in d3d mode.

```
wine war3.exe -opengl
```

The message I receive after typing this is:

home@home-desktop:~$ wine war3.exe -opengl
wine: could not load L"c:\\windows\\system32\\war3.exe": Module not found

---

### Post by tgm4883 on 2007-05-12
Hmm, my money is on the driver for your 3d card not recognizing all the features correctly, which I think can be remedied by installing the fglrx driver from the ati site.  You will have to search for a guide on doing that as i have a nvidia card.

---

### Post by raeb on 2007-05-12
> **danny71 said:**
> The message I receive after typing this is:

home@home-desktop:~$ wine war3.exe -opengl
wine: could not load L"c:\\windows\\system32\\war3.exe": Module not found

Try changing your present directory to the wine directory and then doing
wine war3.exe -opengl

---

### Post by Rizado on 2007-05-13
> **danny71 said:**
> The message I receive after typing this is:

home@home-desktop:~$ wine war3.exe -opengl
wine: could not load L"c:\\windows\\system32\\war3.exe": Module not foundOkey you really need to learn how to use wine. Read this: [http://winehq.org/site/docs/wineusr-guide/index](http://winehq.org/site/docs/wineusr-guide/index)

In short what you need to do is cd to the warcraft directory and run the command.

---

