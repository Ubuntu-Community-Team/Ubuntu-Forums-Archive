---
title: "ubuntu 11.10 on ASUS G73SW: resume mode"
date: 2011-11-20
forum: Desktop Environments
---

### Post by alain.roger on 2011-11-20
Hi,

i would like to know if it's possible to resume ubuntu after notebook ASUS G73SW went to sleeping mode ?

in my case i can only press "power" button to switch off and to restart computer.

do you have any idea how to solve it ?

thx.

---

### Post by qleak on 2011-11-20
You may want to see if the suspend behavior is working in the most basic sense.

Go to the dash menu and search for: terminal 
run the program

make sure you have all your important programs closed and files saved in case it doesn't work.

run the following command lines (you'll have to enter your user password)
```

sudo apt-get install pm-utils
sudo pm-suspend

```Your computer should suspend. Try resuming by pressing the power button. If this works, it should be fairly easy to get it working.

---

### Post by alain.roger on 2011-11-20
pm-utils has been already installed.
and whe i type pm-suspend. notebook is sent to suspend mode.... my problem is not to send it to suspend mode.... it's the wake-up mode.... everything stay dark and never come back to resume mode :-(

---

