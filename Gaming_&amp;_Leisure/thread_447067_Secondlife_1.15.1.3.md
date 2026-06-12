---
title: "Secondlife 1.15.1.3"
date: 2007-05-17
forum: Gaming &amp; Leisure
---

### Post by sharperguy on 2007-05-17
Hi, I've been on second life for some time now

Yesterday, I downloaded the new version (1.15.1.3) and it doesn't work.

When I try to run it I just get a black window :(

I know I should really look on the secondlife linux client forums but they wont let me on because of damn payment info

anyways thanks for any help

---

### Post by eye208 on 2007-05-18
Delete the hidden folder ".secondlife" from your home folder, then try again. This will give you the default configuration and an empty cache. If it still doesn't work, open the startup script "secondlife" in a text editor. There are three lines that control the usage of OpenGL extensions:

```
#export LL_GL_NOEXT=x

export LL_GL_BASICEXT=x

#export LL_GL_BLACKLIST=abcdefghijklmno
```

Change those lines to look like this:

```
export LL_GL_NOEXT=x

#export LL_GL_BASICEXT=x

#export LL_GL_BLACKLIST=abcdefghijklmno
```

This will disable all OpenGL extensions in the viewer. If it still doesn't work, roll back to the previous version of the viewer. ;)

---

### Post by sharperguy on 2007-05-19
Right thanks,  I rolled back and that was fine, I had already tried deleting .secondlife but i'll try your configuration way now.

---

### Post by foormea on 2007-05-22
version 1.15.1.3 of the binary does not work on my ubuntu either. works with other distro on the same computer however.

i've been looking for an older binary of secondlife but i really can't find it anywhere. where could i find it? or could anyone send it to me on my ftp?

thanks.

---

### Post by eye208 on 2007-05-23
> **foormea said:**
> version 1.15.1.3 of the binary does not work on my ubuntu either. works with other distro on the same computer however.
Version 1.15.1.3 works just fine here on Ubuntu 7.04. I suppose there is either a difference in the configuration of your viewer or a difference in the driver setups of your distros. For example the viewer won't work at all without direct rendering.

Rolling back to a previous version is not an option any more because version 1.16 will be released today as a mandatory upgrade.

---

### Post by sharperguy on 2007-05-23
argh thats annoying

The grid is down at the moment but the beta grid one isn't working.

I tried the advice you gave me to no avail

edit: It was cool yesterday though because James Linden was on talking about the new updates :P

edit edit: I suppose it might help to say what graphics card I'm running etc:

nVidia GeForce 7600 GS&#65288;256MB)

I have the latest nvidia-glx from the feisty repos

---

### Post by foormea on 2007-05-29
hey

i had the same problem with 1.15.1.3 and the freshly released 1.16.0.6, black screen when trying to launch

i've located where the problem on my computer was coming from: scim. secondlife (at least the version available directly from secondlife.com ; i haven't tried with a .deb package) won't run if the chinese input is enabled. gotta disable it then it'll run

---

### Post by sharperguy on 2007-05-29
a ha!

Right then how do i disable scim?

It's different in Feisty

---

### Post by foormea on 2007-05-30
do you use scim to input weird languages such as japanese, korean, chinese, hindi or stuff? well anyway even if you don't maybe you've got scim activated

i had to disable the "support to enter complex characters": ubuntu menu / system / administration / language support    then untick the enable blahblah :)

however secondlife seems to be buggier than ever, on my box at least.

---

### Post by eye208 on 2007-05-30
This is strange. I have scim and scim-tables-ja installed but Second Life runs just fine here.

---

### Post by foormea on 2007-05-30
the problem seemed to come from fonts, as secondlife just hanged in the terminal when loading fonts. i tried removing msttcorefonts, french support and chinese support and i could isolate that only the support to enter complex characters was causing the problem. i could try removing chinese support and installing japanese support and see what happens. i'll do that later today

is secondlife buggy on your side?

---

### Post by eye208 on 2007-05-30
> **foormea said:**
> is secondlife buggy on your side?
So far there are only two bugs that I run into (not counting server-side bugs):

1. Ogg audio streams on parcels. The viewer cannot play them. Any attempt to do so will make it freeze. MP3 streams are fine though.

2. After several hours on the grid, the sound will mess up. No crash, but I need to quit and restart the viewer to fix it.

Other than that the Linux viewer has been surprisingly stable for me. I know quite a few folks who experience more trouble with SL on Windows.

---

### Post by EdThaSlayer on 2007-05-30
Has this version got the "changing appearance" to work? I can't seem to change the way my person looks like(I'm walking around with a naked female avatar :( )

---

### Post by eye208 on 2007-05-30
Try pulling an outfit from your library folder onto your avatar. You can't change your look unless you actually wear something to change. (Shape and Skin count as clothes too!)

This is not a viewer bug.

---

### Post by sharperguy on 2007-05-31
I have it working now.

I removed scim and that worked.

As for the naked thing I never had that in any version :/

---

### Post by ELMIT on 2007-12-12
I finally got it to work with version 1.18.5.3!!!

However, I do have some problems/questions:

1. The sound is occupied by starting SL, no other program may use sound anymore. How can I change that?

2. I would like to start the program multiple times with different avatars. What do I need to take care of?

bye

Ronald

---

