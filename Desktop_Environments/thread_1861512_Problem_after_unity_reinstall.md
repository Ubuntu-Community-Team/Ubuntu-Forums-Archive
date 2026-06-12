---
title: "Problem after unity reinstall"
date: 2011-10-15
forum: Desktop Environments
---

### Post by 81duz1d0 on 2011-10-15
Yesterday I updated my Ubuntu 11.04 and I ran into serious problems with the GUI. The windows didn't draw properly so I tried to do 

```

sudo nvidia-xconfig --add-argb-glx-visuals -d 24
gtk-window-decorator --replace &

```

No luck.

Then I did

```

metacity --replace

```

The windows got drawn but anything else worked, so I tried uninstalling Compiz (along with unity and ubuntu-desktop) and then reinstalled it. Well, if I try to login as Guest it works but I can't login with my former user. When I try, I got back to the login screen.

How could I fix it

---

### Post by Dr3Daemon on 2011-10-15
I am having a similar problem. I can not login on my "normal" user after an upgrade. I can't find anythin in any log files, so not sure where to start debugging this - when I try to login it accepts my password and then takes me back to the login screen.

If I login as guest or as another user I have created, unity works fine. I have tried removing all the .files from my user directory and I have also tried copying the .files from one of the users that works into my normal user dir. The best I can get is a terminal window coming up with no window manager - I can then sort of get compiz, metacity and unity running but not themed and looking pretty broken...

Also I couldn't connect to a wireless network without a bit of fiddling around (had to create a new connection using sudo to start the ui).

All in all , not the seemless upgrades I had gotten used to - ah well, that'll teach me to update as soon as it becomes available!

---

### Post by Dr3Daemon on 2011-10-16
Any one? Even some tips on how to get more info. It just dumps me back to the login screen and I can't find anything relevant in the error logs... :(

---

### Post by Dr3Daemon on 2011-10-16
OK, I have found at least one problem. Somehow my .Xauthority file had become owned by root. So obviously X couldn't start. I'm not sure if that happened while I was messing around trying to fix things or if it somehow happened during the update, but removing the old .Xauthrity has certainly allowed me to login again.

However this is not everything, I can only get unity to start properly by removing a bunch of my old config files, I'll post again once I know what other bits of config are troublesome.

---

### Post by Dr3Daemon on 2011-10-16
I put back all my old config piece by piece and the only part that seemed to reliably coincide with things not working was the .compiz folder (which doesn't seem to be necessary anyway).

So I'm not really sure what went wrong. Certainly after the upgrade I couldn't even log in, and when I could everything was broken. Now pretty much everything is working and I don't really know what I've changed.

But for other people having this problem, try deleting your .compiz directory and your .Xauthority file.

---

