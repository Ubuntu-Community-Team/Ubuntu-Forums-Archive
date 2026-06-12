---
title: "KDE not working after login, black and white"
date: 2009-04-03
forum: Desktop Environments
---

### Post by TropheusJon on 2009-04-03
Hello,

I'm a newbie.  I've been using Kubuntu for a few months.  Today I tried to boot it up, after I login, it showed the usual KDE startup screen with the icons, then it turned black and white.  You can see the windows from the previous session as black or white or gray rectangles but nothing inside them.  I tried to use recover mode to fix broken packages and restart xserver, didn't work.  I also booted with a empty session and yet it didn't work.  Failsafe doesn't work as well.  It gave me an error message when I tried to use it.

Running Kubuntu 8.10 64bit, Q6600, HD4870.

I'm using Vista right now thanks to dual boot so the videocard itself is working.

Please help!
Thanks!
Jon

---

### Post by TropheusJon on 2009-04-03
I'm running compiz, not sure if thats a problem.  I did do an update but I forgot what it was totally.  If disabling it might help I don't know the console commands, lol.

Thanks.

---

### Post by Tobi-fp on 2009-04-03
compiz is the proplem, i had the exact same problem.. There is a way to work around this, but i cant remember exactly how..
I bet you are using a intel gma graphics adapter, right?

anyways, you should try finding a work around googling the net for intel compiz problem

---

### Post by TropheusJon on 2009-04-03
Does anyone know the command to disable or uninstall compiz from the kernel?

Thanks

---

### Post by TropheusJon on 2009-04-03
Hi,

I just attempted to remove compiz in recovery mode in the kernel.  I did sudo apt-get remove compiz*.  It did a bunch of things, I then chose the attempt to fix x-server option again then did the normal boot.  Still it goes to the black screen after the last boot-up icon appears after I logged in to KDE.

Please help.

Thanks in advance.

---

### Post by Giblet5 on 2009-04-03
You can still log out by doing Ctrl-Alt-Backspace.

The do Ctrl-Alt-F1 to flip over to the text console.

Log in.

Do the following:
```

mkdir DotFiles
mv .kde DotFiles
mv .gnome* DotFiles
mv .gconf* DotFiles

```

Log off.

Do Ctrl-Alt-F7 to flip back to the greeter.

Log in.

This will make everything the default, but all of your good stuff is still safe in that DotFiles directory.

That will get you running.

---

### Post by TropheusJon on 2009-04-04
It worked!  I can log back in now, thanks a bunch!:popcorn:

---

### Post by Giblet5 on 2009-04-04
> **TropheusJon said:**
> It worked!  I can log back in now, thanks a bunch!:popcorn:

Great!

Remember that any settings (email accounts, IM accounts, etc) all have to either be copied from the DotFiles directory, or re-entered manually.

Enjoy

---

