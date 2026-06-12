---
title: "Frostwire installed and in sys tray.........."
date: 2006-09-09
forum: Desktop Environments
---

### Post by jayneella on 2006-09-09
Hello i have just installed Frostwire and i have it in my system tray, however when trying to get it up it wont even bring up a window after i have selected it from the system tray.....can anyone help please?

Thanks
Jayne
](*,)

---

### Post by taurus on 2006-09-09
Do you have java install on your machine???  I bet you don't...  Try running it from a terminal, Applications -> Accessories -> Terminal, so see what the problem is!

```
frostwire
```

---

### Post by DougieFresh4U on 2006-09-09
Do you have java installed? Add/remove or synaptic-sun java 5 & also jre 1.4 both wre neede when I installed frostwire. Hope this helps as I am learning by trial & error!!

---

### Post by jayneella on 2006-09-09
Hey thanks for that, when i go to synptic for installing java 5 and jre i get several different subjects to indidually install, which is it? arghhhh this is difficult i have never installed a thing in my life!

](*,) ](*,) ](*,)

---

### Post by jayneella on 2006-09-09
jayne@jayne-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
jayne@jayne-laptop:~$

---

### Post by DougieFresh4U on 2006-09-09
In my add/remove I checked Sun java 5 runtime & java web start 1.4, so check this out and look for same in synap.---(Applications-Add/remove)

---

### Post by jayneella on 2006-09-09
yes it has definately been installed and it still wont work, any ideas?
thanks for your help

Jayne

---

### Post by DougieFresh4U on 2006-09-09
The last 2 things I mentioned wre in my add/remove under Aplications drop down. In my synaptic I have sun-java-bin, java-commom, & java-gcj are all checked. I am still new to all this, so I've gone through this same crap also.Don't know what esle.but check these out

---

### Post by jayneella on 2006-09-09
Thanks so much i have done it now! now all i have to figure out is how to burn the dam things xxx

---

### Post by taurus on 2006-09-09
> **jayneella said:**
> Thanks so much i have done it now! now all i have to figure out is how to burn the dam things xxx
If you want to burn something in Ubuntu, k3b is a good option, one of many burning apps.

```
sudo aptitude update
sudo aptitude install k3b

```

---

### Post by jayneella on 2006-09-09
Thanks im using K3B but it will only allow me to burn two songs and then i get the following error - 

Could not determine size of resulting image file.

Can anyone help?

Thanks so much x

---

### Post by taurus on 2006-09-09
How did you burn it?  Did you use the data option and then just drag those songs to the burning window (below)?

---

### Post by jayneella on 2006-09-09
the song was in the current projects window and then i clicked burn!

---

### Post by jayneella on 2006-09-09
i tried the drag and drob and it still didnt work

---

### Post by taurus on 2006-09-09
Why don't you do it the old fashion way?  Start k3b from the Applications -> Sound & Video -> k3b.  Click on data and browser to where all your songs are.  Then just drag then to the bottom window and click Burn!!!

---

### Post by jayneella on 2006-09-09
this is probably a silly question but i have selected K3B via the apps and it comes up fine, with the songs i have downloaded at the top what do i do next?

---

### Post by jayneella on 2006-09-09
ok so i fgured it out but still get the same error....doh!

---

### Post by jayneella on 2006-09-09
> **jayneella said:**
> ok so i fgured it out but still get the same error....doh!

Also whe i play the cd in my cd player it doesn't work but when i play it in the dvd or lap top its fine?????

---

