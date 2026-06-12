---
title: "Steam Ubuntu 15.04"
date: 2015-06-05
forum: Gaming &amp; Leisure
---

### Post by sg4rb0 on 2015-06-05
Trying to install Steam on Ubuntu and it works, but won't run as shown below. Some people have said to stop the runtime thing that steam runs, however I don't know how to do it cos I just installed and used ubuntu yesterday for the first time.    ```
desktop:~/.steam$ ./steam.sh 
rm: cannot remove &#8216;/home/john/.steam/steam&#8217;: Is a directory 
rm: cannot remove &#8216;/home/john/.steam/bin&#8217;: Is a directory 
Running Steam on ubuntu 15.04 64-bit STEAM_RUNTIME is enabled automatically [2015-06-05 22:15:05]
 Startup - updater built Jun  4 2015 10:35:42 
Installing breakpad exception handler for appid(steam)/version(1433441724) 
libGL error: unable to load driver: radeonsi_dri.so 
libGL error: driver pointer missing 
libGL error: failed to load driver: radeonsi 
libGL error: unable to load driver: swrast_dri.so 
libGL error: failed to load driver: swrast 
SteamUpdateUI: An X Error occurred 
X Error of failed request:  BadValue (integer parameter out of range for operation)
```

---

### Post by QIII on 2015-06-05
Hello!  Don't try to remove those things.  They are necessary.

Would you please tell us the OEM and model of your graphics adapter?

---

### Post by berk6 on 2015-06-05
Try this: It looks like you need 32 bit libraries

sudo -i
cd /etc/apt/sources.list.d
echo "deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) raring main restricted universe multiverse" >ia32-libs-raring.list
apt-get update
apt-get install ia32-libs

---

### Post by sg4rb0 on 2015-06-06
@berk6, doesn't work When i go to install ia32-libs, it says:  ```
Package ia32-libs is not available, but is referred to by another package. 
This may mean that the package is missing, has been obsoleted, or is only available from another source 
However the following packages replace it:   lib32z1 lib32ncurses5  E: Package 'ia32-libs' has no installation candidate. 
``` 

 So I install those 2 libraries. Now the msg says: 
 ```
STEAM_RUNTIME is enabled automatically [2015-06-06 04:57:05] Startup - updater built Jun  4 2015 10:35:42 Installing breakpad 
exception handler for appid(steam)/version(1433441724)
libGL error: unable to load driver: radeonsi_dri.so 
libGL error: driver pointer missing 
libGL error: failed to load driver: radeonsi 
libGL error: unable to load driver: swrast_dri.so 
libGL error: failed to load driver: swrast 
SteamUpdateUI: An X Error occurred 
X Error of failed request:  BadValue (integer parameter out of range for operation)
```  @Qlll Radeon windforce7870

---

### Post by sg4rb0 on 2015-06-06
How do you get the flipping terminal ouput pasted in & make it use the correct format?

---

### Post by QIII on 2015-06-06
Are you using the proprietary AMD driver?

(As for the code, I don't know why that came out like that.  Did you CTRL + SHIFT + C from the terminal and CTRL + V between code tags?)

---

### Post by sg4rb0 on 2015-06-06
I have no idea, how can i find out?

---

### Post by sg4rb0 on 2015-06-06
Anyone got any ideas at all?

---

### Post by MikeCyber on 2015-06-07
I have a Nvidia but it looks like you didn't install the AMD driver. Install it with synaptic and paste the output again if it still doesn't work.

---

### Post by QIII on 2015-06-08
> **sg4rb0 said:**
> I have no idea, how can i find out?


If you get something back from 

```
fglrxinfo
```

other than an unrecognized command message, you have it.

But if you don't remember installing it, you probably don't.

---

### Post by oldrocker99 on 2015-06-08
> **sg4rb0 said:**
> How do you get the flipping terminal ouput pasted in & make it use the correct format?

Highlight the code, and copy it. Then open a terminal and use SHIFT-CTRL-V to paste it.

You can also highlight the text, without using copy, and paste it in the terminal by just clicking the middle mouse button; it's one more of the many advantages of Linux.

---

