---
title: "Corrupted GUI after update Ubuntu 10.04"
date: 2012-02-17
forum: Desktop Environments
---

### Post by juankenny on 2012-02-17
Hello, I'm new in the forum, and I come here hoping to find a solution to a quite rare problem.

First I'll tell I've done with my operating system:

1. Yesterday, Instalation of Ubuntu 10.0.04 64bits

2. With a new and fresh installation of Ubuntu, then install everything you to run CUDA (nVidia geforce GT520M) with a tutorial (I don't know if i can paste a link to another page, if you want to see the tutorial for some reference, please tell me.)

3. After reboot, a message in a gray window appeared, "Linux is running in low graphics mode, blah blah" (I think you know what gray window I mean), I select the option "Reconfigure graphics", then, "Create new configuration", and "restart X". Everything continue normal. Then, I made a new "guest" account, then, I went to sleep.

4. Today, when I try to run CUDA in terminal, an error appeared that said:

"Xlib:  extension "GLX" missing on display ":0.0"."
"freeglut (./smokeParticles): OpenGL GLX extension not supported by display ':0.0'"

So, I look for some solutions on the Internet. The solution that I found was run nvidia-xconfig, and that was I did.

5. To finish, I run Update Manager, obviously, to update my system... REBOOT :(

6. Again, a gray windows appeared after reboot that said some error about loading nVidia driver. (driver not found, I did the same thing that the previous gray windows)

.. and that is what I get after reboot and login

[IMG]http://2.bp.blogspot.com/-PLH8nTJsuzo/Tz7bqhEH-dI/AAAAAAAAA68/Lp3FNbgv3W4/s1600/Screenshot-1.png[/IMG]

The weird part of this is that, when I login in my account the desktop background appears correctly, and after 2 or 3 seconds it turns upside down.

When I login in the guest session, everything is OK... Why? Is an error in a configuration file in the main account?

Thanks in advance for the support.

---

