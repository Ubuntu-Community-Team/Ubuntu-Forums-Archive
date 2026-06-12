---
title: "Cold War Demo Will Not Start"
date: 2011-03-02
forum: Gaming &amp; Leisure
---

### Post by Joseph Schwenker on 2011-03-02
I just got the Cold War Demo from here, but it will not start after the first start. I get the error 

```
joseph@joseph:~/coldwar_demo$ sh coldwar_demo 
bin/launcher: 7: function: not found
Cold War Demo 1.1 by Mindware Studios
Published by Linux Game Publishing
http://www.linuxgamepublishing.com/
Support: http://support.linuxgamepublishing.com
e-mail: support@linuxgamepublishing.com
bin/launcher: 16: function: not found
Usage: coldwar [options]
[-h | --help]         Display this help message
[-v | --version]      Display the game version
[-w | --windowed]     Run the game windowed
[-f | --fullscreen]   Run the game fullscreen
[-s | --nosound]      Do not access the sound card
[+s | --sound]        Enable sound
[-g | --withgl] [x]   Use [x] instead of /usr/lib/libGL.so.1 for OpenGL
error: IO error 'Permission denied' encountered while opening a file
joseph@joseph:~/coldwar_demo$ 

```

Can anyone help me out?

---

### Post by Joseph Schwenker on 2011-03-02
Also, during the install, I got an error in the installer's terminal. A screenshot is attached.

---

### Post by sakuramboo on 2011-03-02
From the looks of it, you installed it in your home directory. Am I right?

Also, do you have AppArmor or any SELinux modules installed?

You shouldn't have to use 'sh' to run the game. After installing, it is already executable. just run it with ./ instead. That shouldn't give any errors, just a little tick of mine. :)

Have you tried contacting LGP? Hop into their IRC channel on freenode and shoot them an email.

---

### Post by Joseph Schwenker on 2011-03-02
> **sakuramboo said:**
> From the looks of it, you installed it in your home directory. Am I right?

Also, do you have AppArmor or any SELinux modules installed?

You shouldn't have to use 'sh' to run the game. After installing, it is already executable. just run it with ./ instead. That shouldn't give any errors, just a little tick of mine. :)

Have you tried contacting LGP? Hop into their IRC channel on freenode and shoot them an email.

I have AppArmor and libselinux1 installed.

```
joseph@joseph:~/coldwar_demo$ ./coldwar_demo 
bin/launcher: 7: function: not found
Cold War Demo 1.1 by Mindware Studios
Published by Linux Game Publishing
http://www.linuxgamepublishing.com/
Support: http://support.linuxgamepublishing.com
e-mail: support@linuxgamepublishing.com
bin/launcher: 16: function: not found
Usage: coldwar [options]
[-h | --help]         Display this help message
[-v | --version]      Display the game version
[-w | --windowed]     Run the game windowed
[-f | --fullscreen]   Run the game fullscreen
[-s | --nosound]      Do not access the sound card
[+s | --sound]        Enable sound
[-g | --withgl] [x]   Use [x] instead of /usr/lib/libGL.so.1 for OpenGL
error: IO error 'Permission denied' encountered while opening a file
joseph@joseph:~/coldwar_demo$ 

```

---

### Post by sakuramboo on 2011-03-02
If you installed the game in your home directory, then that is your problem, AppArmor.

I had a similar problem when I used to run Fedora with SELinux.

Unfortunately, I am not too familiar with AppArmor, but I am willing to bet that is your issue.

If I remember correctly, you need to create a new definition for AppArmor to allow library calls within your home directory.

EDIT: Forgot to mention...

My bad, I meant that using ./ won't produce anything different. It will still give errors. Just, you don't have to use 'sh' since not all executables will be bash scripts.

---

### Post by Joseph Schwenker on 2011-03-02
> **sakuramboo said:**
> If you installed the game in your home directory, then that is your problem, AppArmor.

I had a similar problem when I used to run Fedora with SELinux.

Unfortunately, I am not too familiar with AppArmor, but I am willing to bet that is your issue.

If I remember correctly, you need to create a new definition for AppArmor to allow library calls within your home directory.

I had the same problem when installing the game into /usr/local/games, except the game would start from the installer with no sound, then not start again.
Should I just uninstall AppArmor?

---

### Post by sakuramboo on 2011-03-02
That is up to you.

From a security stand point, I say get the issue resolved.

From a usability stand point, I say get rid of it.

It seems to be a problem when calling libraries when they are not in the proper location. Unfortunately, I am unable to help you. ACL's in Linux are still rather new to me. You can try sending LGP an email and see what they say.

But, it is entirely up to you.

---

### Post by Joseph Schwenker on 2011-03-02
I think I figured it out. Apparently, ~/.lgp/coldwar-demo was owned by root for some reason, which forced me to run the game with sudo. I changed it back to me, and the game ran fine without sudo. However, I'm still trying to get sound working. I did not need to uninstall AppArmor.

---

### Post by Joseph Schwenker on 2011-03-02
I fixed the sound! I followed the advice of a user on the Frictional Games forums and applied it to this game.

> There was a symbolic link in my PenumbraOvertureDemo/lib folder called libopenal.so.1 which pointed to the file libopenal.so.1.3.253 in the same folder. Following your advice, I pointed the link to /usr/lib/libopenal.so.0 instead, and now I have sound in the Overture demo.

Basically, just go into coldwar_demo/lib, remove libopenal.so.0, go to /usr/lib/, hold down alt while dragginglibopenal.so.1.12.854, then release the mouse when in /coldwar_demo/lib, then choose "Link Here". Be sure to rename it to libopenal.so.0. You should now have sound--at least I did!

---

### Post by szoept on 2011-04-15
Thanks Joseph!
This worked perfectly for me as well (default ubuntu 10.10 install)!

---

### Post by BrownieBoy on 2011-05-23
That worked for me too, and for the full version of the game under 64-bit Natty.  For 64-bit though, the target libopenal.so... file is in /usr/lib32.  You'll need some 32-bit compatibility files installed too, I think.

Now, if only I could get the game's config dialog to appear.  The manual says that it's supposed show every time that you start the game...

---

