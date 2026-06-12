---
title: "UT2k3 and Ubuntu problem."
date: 2005-02-01
forum: Gaming &amp; Leisure
---

### Post by oddabe19 on 2005-02-01
So, i went to install Unreal Tournament 2k3 via linux installer on 3rd disc (as i've done many times in the past) copied the linux_installer.sh to my desktop... did a chmod +x to it... and off i went.

Put everything into /home/oddabel/ut2003 etc...

so i go to run it and this happens

```
oddabel@ubuntu:~/ut2003 $ sh ut2003
fcntl: Operation not permitted
fcntl: Operation not permitted
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
OpenGL renderer relies on DXTC/S3TC support.

History:

Exiting due to error
oddabel@ubuntu:~/ut2003 $
```

I get the splash screen and that's it.... GLXgears work great... and Steam works great.  I can't seem to figure it out.

Anyone?

PS- i also have my nvidia drivers installed via their site.

---

### Post by dhonn on 2005-02-02
When you run:
glxinfo | grep direct

Does it say yes?

If not, edit /etc/X11/xorg.conf and where it says **Driver "nv"** insert **Driver "nvidia"**

restart your xserver with CTL+ALT+BKSPC

Just maybe the video drivers aren't loading.  Or maybe your gfx card is old.  My old nvidia gfx card doesnt support doom3, not in terms of performance but functionality.

---

### Post by oddabe19 on 2005-02-02
[QUOTE=dhonn]When you run:
glxinfo | grep direct

Does it say yes?

If not, edit /etc/X11/xorg.conf and where it says **Driver "nv"** insert **Driver "nvidia"**

restart your xserver with CTL+ALT+BKSPC

Just maybe the video drivers aren't loading.  Or maybe your gfx card is old.  My old nvidia gfx card doesnt support doom3, not in terms of performance but functionality.[/QUOTE]
```

oddabel@ubuntu:~ $ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
oddabel@ubuntu:~ $
```

But i've already replaced my xorg.conf file stuff.... and did everything you're supposed to with nvidia...

IIRC, there used to be a problem with the mesa portion of the drivers and xorg/xfree but i don't remember how to fix anyof it...

---

### Post by piedamaro on 2005-02-02
[QUOTE=oddabe19]```

oddabel@ubuntu:~ $ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
oddabel@ubuntu:~ $
```

But i've already replaced my xorg.conf file stuff.... and did everything you're supposed to with nvidia...

IIRC, there used to be a problem with the mesa portion of the drivers and xorg/xfree but i don't remember how to fix anyof it...[/QUOTE]
 What did you do to install nvidia drivers? Have you got a line in /etc/modules which reads: nvidia ?
Did you issue a:
sudo nvidia-glx-config enable ?

---

### Post by oddabe19 on 2005-02-02
I actually use their own drivers from their site...

Anyway, i forgot to reinstall when I updated xorg and the newest kernel, so the drivers didn't know what to do.

I reinstalled them and it worked....

my bad, human error... thanks anyway guys. :-D

---

### Post by GrayFox^ on 2005-04-21
This is the error I get when following the guide here [http://www.easylinuxguide.com/index.php?name=PNphpBB2&file=viewtopic&t=735&sid=2a14d155b61b123b6a5a675b0d20066e](http://www.easylinuxguide.com/index.php?name=PNphpBB2&file=viewtopic&t=735&sid=2a14d155b61b123b6a5a675b0d20066e) 
I get the following error when trying to do step 6.
```
root@apiata:/home/conrad # sh linux_installer.sh
Copying to a temporary location...
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 2003 for GNU/Linux 2107......................................................................
No UI drivers available
.setup22050: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed.
./setup.sh: line 104: 22073 Aborted                 "$setup" "$@"
The setup program seems to have failed on x86/glibc-2.1

Fatal error, no tech support email configured in this setup
The program returned an error code (1)
root@apiata:/home/conrad #
```

Please help a Linux newbie out, as I succesfully installed Enemy Territory thanks to a guide on these forums.

---

