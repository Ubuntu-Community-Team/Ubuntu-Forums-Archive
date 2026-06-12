---
title: "Wine Problem!"
date: 2006-02-27
forum: Desktop Environments
---

### Post by XIII on 2006-02-27
I installed wine, to run macromedia dreamweaver on it, but wine doesn't work at all, there's a problem that i can't configure, i copied the error message i got from it when i tried to even run notepad through it:
[COLOR="Red"]/home/sting# wine notepad.exe
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.[/COLOR]
This is what i got, hope i can get a solution, i'm really confused with it.:???:

---

### Post by mustang on 2006-02-27
This doesn't fix your problem but I'll let you know right now that you won't be able to run dreamweaver alone with wine. You will need crossover office for it.

---

### Post by XIII on 2006-02-27
It didn't solve it, what is crossover office?

---

### Post by ltmon on 2006-02-27
Hi,

I would get rid of your compiled version, then use the repository at [http://winehq.org](http://winehq.org) to get prebuilt binaries for Ubuntu.  They are kept pretty up-to-date with the latest sources.

Once installed run:

> winecfg

Which will allow you to set up a whole lot of stuff.

After this wine should work.  Be sure to check out the application database at [http://winehq.org](http://winehq.org) for the programs you want to run to get some idea of how successful it will be.

L.

---

