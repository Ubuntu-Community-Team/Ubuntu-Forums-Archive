---
title: "Xmodmap not applying at resume"
date: 2014-03-22
forum: Desktop Environments
---

### Post by josephellengar2 on 2014-03-22
Hi everybody! I am running a fully updated version of Ubuntu 13.10 (Saucy) with Gnome 3. In my setup I have a small number of keys that I remap using xmodmap. Unfortunately, while I am able to get my xmodmap settings to apply at boot, they do not always apply at resume. It just leaves the keymap in the normal qwerty setup. I am unsure why, after testing many theories.

Anyway, the solution that almost everybody online seems to be suggesting is this:

In the directory /etc/pm/sleep.d I have a file named 99_xmodmap.sh (it is executable)

```

#!/bin/sh
case "$1" in
  suspend)
     ;;
  resume)
    DISPLAY=:0.0 ; export DISPLAY
    sleep 3;
    xmodmap /home/ross/.Xmodmap
     ;;
  *) exit $NA
     ;;  
esac

```

Is there something wrong with this? Any other suggestions? Thanks.

---

### Post by Toz on 2014-03-22
I believe you need to export XAUTHORITY and run the command as the user. Try this instead:
```
#!/bin/sh
case "$1" in
  suspend)
     ;;
  resume)
    export DISPLAY=":0"
    export XAUTHORITY="/home/ross/.Xauthority"
    su ross -c "xmodmap /home/ross/.Xmodmap"
     ;;
  *) exit $NA
     ;;  
esac
```
...of course, assuming that your username is ross.

---

### Post by josephellengar2 on 2014-03-22
Thanks! I'll try it out and see if it works. It not working is somewhat itermittent now (I think it has to do with how long the computer was suspended) so I'll get back to you in a day or two.

---

### Post by josephellengar2 on 2014-03-23
Well, it seems to still be working. I'll mark the thread solved. Thanks!

---

### Post by u2nTu on 2014-08-18
Thought this would work for 14.04.1 so cobbled together a quick script for ease of use:
```
echo '#!/bin/bash
case "$1" in
  suspend)
   ;;
  resume)
    export DISPLAY=":0"
    export XAUTHORITY="/home/'$USER'/.Xauthority"
    su '$USER' -c "/usr/bin/xmodmap /home/'$USER'/.Xmodmap"
   ;;
  *) exit 0
   ;;
esac' > Xmod-tmp

sudo mv -f Xmod-tmp /etc/pm/sleep.d/90_reload-xmodmap
sudo chmod +x /etc/pm/sleep.d/90_reload-xmodmap

echo ''
ll /etc/pm/sleep.d/90_reload-xmodmap
echo ''
cat /etc/pm/sleep.d/90_reload-xmodmap
```
File is created and should be running fine, but keys are not remapped -- have to manually execute the very same command as in the '90_reload-xmodmap' script.

Giving up on auto-reload now.

With the Nautilus fiasco, this is yet another item to put back the way it was.

---

### Post by dedalu on 2014-08-21
Since '~.Xmodmap' is a user file, the solution should stay on the user side. I did a python script to be loaded on Startup Applications, that reloads the '~/.Xmodmap' on resume, user change and layout change. I uploaded it to the [bug report #1243642]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1243642") (comment #6), and you can download it [here]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1243642/+attachment/4183061/+files/user-xmodmap-reload-hack").

---

### Post by u2nTu on 2014-08-21
> **dedalu said:**
> Since '~.Xmodmap' is a user file, the solution should stay on the user side. I did a python script to be loaded on Startup Applications, that reloads the '~/.Xmodmap' on resume, user change and layout change. I uploaded it to the [bug report #1243642]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1243642") (comment #6), and you can download it [here]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1243642/+attachment/4183061/+files/user-xmodmap-reload-hack").
Incremented the 'also have' counter and subscribed, thanks. Sometimes...we wait. (Though not always patiently or cheerfully. 8-[ )

---

