---
title: "ATI + xgl + Beryl = xserver failure"
date: 2007-03-12
forum: Desktop Environments
---

### Post by FugitivePuppeT on 2007-03-12
I'm on a sony vaio pcg-nv100p. I have an ATI Mobility Radeon 9000 in my laptop, I've tried pretty much every tutorial I can find on the net to get beryl to work on my laptop but all end with the xserver crashing. When I view the detailed output most of the time it says something about no screen present. (Not sure, can find out)

Any help? (I can post more information if needed)

---

### Post by K.Mandla on 2007-03-12
(Moved to Desktop Environments. ;) )

---

### Post by STREETURCHINE on 2007-03-12
if you have a backup try


              ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

              then

               ```
sudo apt-get update
```

          then restart x

              ```
startx
```

if that dont work

                ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by FugitivePuppeT on 2007-03-12
> **STREETURCHINE said:**
> if you have a backup try


              ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

              then

               ```
sudo apt-get update
```

          then restart x

              ```
startx
```

if that dont work

                ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Thanks for the response, but unfortunately it failed to work for me. The xserver still crashed and I received these errors:

```
Failed to start the X server (your graphical interface). It is likely that it is not set up correctly.
```

Then I view the x server output and it says:

```
Fatal server error: no screens found
```

---

### Post by STREETURCHINE on 2007-03-12
ok now we reconfigure

      ```
sudo dpkg-reconfigure xserver-xorg
```

if you are not sure of the answers just accept the defaults

then restartx

---

### Post by FugitivePuppeT on 2007-03-12
> **STREETURCHINE said:**
> ok now we reconfigure

      ```
sudo dpkg-reconfigure xserver-xorg
```

if you are not sure of the answers just accept the defaults

then restartx

Just did that. Still get the same error. What I can do is change my driver in xorg.conf from "fglrx" to "ati" and at least it will boot up. Although beryl still wont work.

---

### Post by STREETURCHINE on 2007-03-12
yes it definatly sounds like a driver problem,give your idea a go ,if it works good,you can always install beryl again,

---

### Post by FugitivePuppeT on 2007-03-12
Ugh... ok I'm going to try Feisty Fawn tomorrow, if it doesn't work... I might just go back to Windows XP :(

---

### Post by 351W on 2007-03-12
I thought I had a good idea, but I was wrong. This is only here because I can't figure out how to delete my post entirely.

---

### Post by nicktrik on 2007-03-21
Have to make sure your ATI drivers are setup correctly in order for Beryl and Xgl to work. Do an fglrxinfo and if Mesa drivers show up you all you have to do is google search until you install the ATI drivers correctly. If all is sell a fglrxinfo will show ATI driver.
Try that and I am sure it will work.

---

