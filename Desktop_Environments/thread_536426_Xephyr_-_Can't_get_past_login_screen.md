---
title: "Xephyr - Can't get past login screen"
date: 2007-08-27
forum: Desktop Environments
---

### Post by akshaydua on 2007-08-27
Hi all,

I did the following:

```
Xephyr ":1" -query localhost
```

This opens up a new window where I see the Ubuntu login screen. I enter my username and password correctly and then it promptly goes back to the login screen again and not my desktop.

Error messages in the terminal on starting Xephyr are as follows:

```
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```

I read somewhere that this problem can be solved by setting up a font server and adding it to the font path via xset. So this is what I did...

```
akshay@gumpy$ sudo ./xfs start
Setting up X font server socket directory /tmp/.font-unix...done.
Starting X font server: xfs.
akshay@gumpy$ xset +fp tcp/localhost:7100
xset:  bad font path element (#390), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax
akshay@gumpy$ 
```

At this point I am totally stuck and can't get Xephyr to work. My overall goal is to be able to SSH to my remote machine and start Xephyr and use the GNOME desktop. I can't use simple remote login because my remote machine does not have a public IP address.

Any help will be appreciated.

---

