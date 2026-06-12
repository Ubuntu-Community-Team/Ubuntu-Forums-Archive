---
title: "Desktop Unresponsive!?!?!?!"
date: 2008-04-27
forum: Desktop Environments
---

### Post by manizzle on 2008-04-27
Hi. So i just recently upgraded to hardy. When first installing, it said there was an error installing samba-commmon, smbclient, and ubuntu-desktop.
Now, restarting into hardy, the desktop is unresponsive, i cannot open my home folder, and filesystem. I cannot right click on the desktop, there are no icons and basically i cannot do anything on my desktop. My wallpaper has disappeared and im left with a brown screen and no right clicking. I tried running nautilus from terminal and came up with this:

```
seahorse nautilus module initialized
Initializing nautilus-share extension
nautilus: symbol lookup error: nautilus: undefined symbol: g_file_query_filesystem_info_async

```


please help me. I cant even access any of my files. Okay. Any help is greatly appreciated. Thanks.

---

### Post by butigy on 2008-05-02
I had this, this is how I solved it:

the symbol g_file_query_filesystem_info_async is a function in glocalfileinfo.c.  

So I did a 

```

locate glocalfile.c

```

which pointed to a glib installation I had done myself from source (glib-2.15.4).  So I uninstalled this

```

cd /usr/local/src/glib-2.15.4
sudo make uninstall

```

and then for good measure did a reinstall of various glib bits and bobs via the synaptic package manager.

Hope that helps.

---

### Post by Awalton on 2008-05-03
Your (locally) installed version of GIO is too old. Either uninstall it as the previous user mentioned, or update to trunk (may require a Nautilus rebuild, not sure where we are in terms of ABI compatibility yet.)

---

### Post by jmvankeuren on 2010-08-10
Sorry for bump.  

I think I have this problem to in Ubuntu 10.4.  Ubuntu works fine except the desktop is unresponsive to clicking and doesn't display any of the content in homefolder/desktop.

I'm very new to linux and tried what was in these posts but I must be doing something wrong.  I'd appreciate if it could be explained better.

---

