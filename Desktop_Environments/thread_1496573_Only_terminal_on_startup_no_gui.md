---
title: "Only terminal on startup no gui?"
date: 2010-05-29
forum: Desktop Environments
---

### Post by menelajas on 2010-05-29
Hello strange problem when my netbook remix 10.04 starts I can see only terminal and no graphic interface (as you can see in the picture). I see the log in screen type my password and when the screen like on the picture.

I 'm using lenovo N100 nb

Tryed to install ubuntu desktop but no use
Please help:)

---

### Post by rudihawk on 2010-05-29
> **menelajas said:**
> Hello strange problem when my netbook remix 10.04 starts I can see only terminal and no graphic interface (as you can see in the picture). I see the log in screen type my password and when the screen like on the picture.

I 'm using lenovo N100 nb

Tryed to install ubuntu desktop but no use
Please help:)

What happens if you type:

```
startx
```

---

### Post by menelajas on 2010-05-29
> **rudihawk said:**
> What happens if you type:

```
startx
```

Fatal server error:
server is already active for display 0
if the server is no longer running  remove /tmp/.X0-lock
and start again.

please consult the X.org Foundation support
at [http://wiki.x.org](http://wiki.x.org)
for help

---

### Post by hok00age on 2010-05-29
> **menelajas said:**
> Hello strange problem when my netbook remix 10.04 starts I can see only terminal and no graphic interface (as you can see in the picture). I see the log in screen type my password and when the screen like on the picture.

I 'm using lenovo N100 nb

Tryed to install ubuntu desktop but no use
Please help:)

Stop X server:
```
sudo service gdm stop
```

then start it again:
```
sudo service gdm start
```

Hope it works, regards :)

---

### Post by menelajas on 2010-05-30
> **hok00age said:**
> Stop X server:
```
sudo service gdm stop
```then start it again:
```
sudo service gdm start
```Hope it works, regards :)

Sadly but the same situation after stopping and starting :(

any ideas?

---

### Post by Jakiejake on 2010-05-30
Ctrl + Alt + F7
Does That Help

---

### Post by menelajas on 2010-05-30
> **Jakiejake said:**
> Ctrl + Alt + F7
Does That Help

No it does bot work too

---

### Post by hok00age on 2010-05-30
Run:
```
gconftool-2 --type string --set /desktop/gnome/session/required_components/filemanager nautilus
```

```
gconftool-2 --type string --set /desktop/gnome/session/required_components/panel gnome-panel
```

```
gconftool-2 --type string --set /desktop/gnome/session/required_components/windowmanager compiz
```

Then:
```
sudo service gdm stop && sudo service gdm start
```

Hope it works

Regards :)

---

### Post by nischalinn on 2010-05-30
I also faced the same the problem few days ago. I lost my graphics driver. I reinstalled it and everything was fine. Please reinstall the graphics driver.
I hope that will solve the problem.

---

### Post by acrazyplayer on 2010-05-30
At the login screen there is sometimes a option at the bottom to what session you want to log into. You may have it set on some failsafe setting or something other then what you want. Try to look there and find what you need.

---

### Post by menelajas on 2010-05-30
> **nischalinn said:**
> I also faced the same the problem few days ago. I lost my graphics driver. I reinstalled it and everything was fine. Please reinstall the graphics driver.
I hope that will solve the problem.

How to reinstall graphics driver in terminal if my laptop does not have the internet connection?

---

### Post by menelajas on 2010-05-30
> **hok00age said:**
> Run:
```
gconftool-2 --type string --set /desktop/gnome/session/required_components/filemanager nautilus
``````
gconftool-2 --type string --set /desktop/gnome/session/required_components/panel gnome-panel
``````
gconftool-2 --type string --set /desktop/gnome/session/required_components/windowmanager compiz
```Then:
```
sudo service gdm stop && sudo service gdm start
```Hope it works

Regards :)

I got Error while parsing options: unknown option -set. (after second command). :(

---

### Post by menelajas on 2010-05-30
> **acrazyplayer said:**
> At the login screen there is sometimes a option at the bottom to what session you want to log into. You may have it set on some failsafe setting or something other then what you want. Try to look there and find what you need.

At log in screen I see no option only (see the picture)

---

### Post by hok00age on 2010-05-30
> **menelajas said:**
> I got Error while parsing options: unknown option -set. (after second command). :(

Not '-set' mate but '--set'

Triple check what you've typed before executing.

---

### Post by menelajas on 2010-05-31
> **hok00age said:**
> Not '-set' mate but '--set'

Triple check what you've typed before executing.

Don't know what to do else :( This did help too.

Maybe can do system restore or repair installation or sth like that from terminal as I can't solve this problem :/

---

### Post by acrazyplayer on 2010-06-02
> **menelajas said:**
> At log in screen I see no option only (see the picture)

sorry it took me so long to reply but you are one step away from the option to change sessions in that picture. You must click on your user name and when it asks for a password dont enter it but instead look at the bottom of the screen and you will see the "sessions" option. then try changing it.

---

