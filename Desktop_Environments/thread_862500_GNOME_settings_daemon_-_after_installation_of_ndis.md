---
title: "GNOME settings daemon - after installation of ndisgtk"
date: 2008-07-17
forum: Desktop Environments
---

### Post by bl3nd3r on 2008-07-17
Hi Everyone. I have been playing with Ubuntu for a few years and have had success installing and using it on a number of computers. Now that I am switching my main computer over to Ubuntu I grabbed Hardy Heron and installed it. I had everything working until I restarted which is when I got this error.

"Error starting the GNOME settings daemon"

There was an option to press cancel, however, this button was not responding to my clicks. 

I restarted a few more times and had the same problems so threw in my 7.10 live CD and have been trying to debug it from here. So far I have had no luck and even reinstalled 8.04 again only to have the same error happen after my first restart. I have tried safe mode and the terminal but both seem to not work. 

Because of my wireless card I was required to use ndisgtk. Everything works including ndisgtk on 7.10 but not with 8.04. 

I tried editing /etc/x11/Xsession.d/99x11-common_start and ...55gnome-session_gnomerc, as recommended in another post. This did not help so I am turning to others to try and help. 

I have no way to use the computer unless I use the live CD and would be very grateful to anyone who can provide some help.

---

### Post by Prefix100 on 2008-07-17
A temporary fix so you can use the computer while finding a fix is to install a different desktop envir. and use it when logging in.

Hit ctrl+alt and f1, log in, then type

```
sudo apt-get install kubuntu-desktop
```

Once installed ctrl+alt and f7 and ctrl+alt and backspace, then click sessions and then kde, then log in.

---

### Post by bl3nd3r on 2008-07-17
> **Prefix100 said:**
> A temporary fix so you can use the computer while finding a fix is to install a different desktop envir. and use it when logging in.

Hit ctrl+alt and f1, log in, then type

```
sudo apt-get install kubuntu-desktop
```

Once installed ctrl+alt and f7 and ctrl+alt and backspace, then click sessions and then kde, then log in.

Thanks for the suggestion. I do really enjoy GNOME over KDE but having something that works is something I like even better.

If anyone can provide information specific to this problem it would be great!

---

### Post by bl3nd3r on 2008-07-17
> **Prefix100 said:**
> A temporary fix so you can use the computer while finding a fix is to install a different desktop envir. and use it when logging in.

Hit ctrl+alt and f1, log in, then type

```
sudo apt-get install kubuntu-desktop
```

Once installed ctrl+alt and f7 and ctrl+alt and backspace, then click sessions and then kde, then log in.

Well there goes something that works! I followed your steps but once I typed in the code and pressed enter, it just went to the next line and nothing happened. I was able to type and all but the lines were blank otherwise. Any idea about this?

---

### Post by Frogster on 2008-07-19
I get exactly the same problem. However, its when I start updating Hardy Heron that the problem occurs. Everything works well until the updates are applied.

This is the third/fourth attempt at getting the Heron to work and all is fine until the updates are applied. I am just about to give it one last attempt with the latest ISO. Hopefully the problem will not occur in the latest image.

---

### Post by bl3nd3r on 2008-07-21
> **Frogster said:**
> I get exactly the same problem. However, its when I start updating Hardy Heron that the problem occurs. Everything works well until the updates are applied.

This is the third/fourth attempt at getting the Heron to work and all is fine until the updates are applied. I am just about to give it one last attempt with the latest ISO. Hopefully the problem will not occur in the latest image.

Yeah I am not sure of the exact problem but I do know that it has happened 3 times after fresh install for me. I ended up reinstalling Gutsy and have been having great success with it. I may just end up waiting till the next release before I update or until someone can help let me know what is going on.

---

