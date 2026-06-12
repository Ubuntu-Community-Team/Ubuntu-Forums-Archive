---
title: "[SOLVED]Ubuntu 64 bit &amp; Nvidia GTX 670 &amp; Steam OpenGL is not working!"
date: 2015-05-24
forum: Gaming &amp; Leisure
---

### Post by patrikmellq on 2015-05-24
Hello, i have search the internet and try different things, but can not get a working solution.
Here is some information about my issue with pictures.

First i wrote the following code to see what would happen:
```

glxinfo | grep version

```

And this is the output i got:

```

patrik@patrik:~$ glxinfo | grep version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL core profile version string: 4.3.0 NVIDIA 331.113
OpenGL core profile shading language version string: 4.30 NVIDIA via Cg compiler
OpenGL version string: 4.4.0 NVIDIA 331.113
OpenGL shading language version string: 4.40 NVIDIA via Cg compiler

```

This is how my Nvidia settings look like:

[IMG]http://i60.tinypic.com/2nav994.jpg[/IMG]

And this is the message i got from Steam:

[IMG]http://i62.tinypic.com/1zvrgnd.png[/IMG]

I would be very happy if i can get suggestions what to do and try to get a working solution.
Many thanks!

---

### Post by patrikmellq on 2015-05-25
**NOTE I reinstall Ubuntu LTS 64 bit and the Nvidia 331 recommended drive  before i made this changes, last i install Steam after i made the  changes and it works great with no errors.**

The key is that steam (and any other 32-bit program, for that matter)  need to load the 32-bit libGL.so library. However, the nvidia driver  packages in Ubuntu Raring 64-bit (such as nvidia-304,  nvidia-304-updates, nvidia-319, etc.) don't properly configure ldconfig  to use the nvidia version of libGL.so for 32-bit programs (like steam  and tf2). So steam and games like tf2 will end up loading some other  non-nvidia graphics library. This causes steam to warn you about not  using direct rendering (because you're using software rendering instead)  and games like tf2 to fail to start altogether. Fortunately, the fix  for this is really simple:

1.) In /usr/lib, there is a directory called something like nvidia-304  or nvidia-304-updates or nvidia-319 etc., which holds the nvidia OpenGL  libraries.
If that directory is called nvidia-304, for instance,  you'd want to, as root, edit the file /usr/lib/nvidia-304/alt_ld.so.conf  (which you'll notice is currently blank) and add the lines:

```

/usr/lib32/nvidia-304
/usr/lib/nvidia-304

```

If that directory is something else, like /usr/lib/nvidia-304-updates  you'd want to edit the file /usr/lib/nvidia-304-updates/alt_ld.so.conf  as root and add the lines:

```

/usr/lib32/nvidia-304-updates
/usr/lib/nvidia-304-updates

```

And if your directory is /usr/lib/nvidia-<something else>, you'd  want to edit /usr/lib/nvidia-<something else>/alt_ld.so.conf as  root and add the lines:

```

/usr/lib32/nvidia-<something else>
/usr/lib/nvidia-<something else>

```

You get the idea...
 
2.) In the linux terminal, run the command:

```

sudo ldconfig

```

3.) Restart steam/Install Steam. You'll notice that there's no warning about not using  direct rendering anymore. You'll also be able to play games like tf2  again.

Above you need to use Nono to change the alt_ld.so.conf file.
For example:

```

sudo nano /usr/lib/nvidia-331-prime/alt_ld.so.conf

```

When you add the two lines you save the input with "ctrl o" and Enter and Exit Nano with "ctrl x"

---

### Post by MikeCyber on 2015-05-26
I had no problems updating using the download directly from Nvidia.

---

### Post by patrikmellq on 2015-05-26
What do you mean by having no problems? - did you download Nvidia driver direct and Steam work with out any modifications as i describe in the topic above?

---

### Post by MikeCyber on 2015-05-26
I've installed Nvidia and Steam with 14.04. For 15.04 I've downloaded from Nvidia the latest driver and simply run the installer after 15.04 update.
All fine.
But anyway your description surely helps some people.

---

