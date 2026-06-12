---
title: "Frustrating Mplayer Error"
date: 2006-07-01
forum: Desktop Environments
---

### Post by SharekhaN on 2006-07-01
Hello , 


   I have tried and install Mplayer with the help found from this location 

   [http://www.ubuntuforums.org/archive/index.php/t-31061.html](http://www.ubuntuforums.org/archive/index.php/t-31061.html)

   i have taken care to make sure i am replacing the names with the filenames of the latest ones available . so far it has been smooth sailing . i wasnt able to install the x window system from the package described in that but i see that it is installed my sy setup . 

   no matter what i do , i cant  " make " so that i can " make install " mplayer . 
   i do "./configure " and it finished without any major errors or warnings to the best of my knowledge .  i have also tried "./configure --enable-gui" and even then " make " is never an option . 


I do not want to install any other player . i have tried automatix , but totem still dosent work . vlc works but fails to play my x264 files properly . 

 Please help me to a resolution 

```

xero@ubuntu:~/MPlayer-1.0pre8$ make
bash: make: command not found

```

This is what i see

---

### Post by angkor on 2006-07-01
```
sudo apt-get install build-essential
```

should fix that error

---

### Post by SharekhaN on 2006-07-01
Thank you so much . it worked .

---

