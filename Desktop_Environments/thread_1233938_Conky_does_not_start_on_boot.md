---
title: "Conky does not start on boot"
date: 2009-08-07
forum: Desktop Environments
---

### Post by acrocephalus on 2009-08-07
Hello!
I just have installed conky and added this bash script to start it when booting
```
#!/bin/bash
sleep 10 && conky;
```
It works well when I logout, but it does not work when booting. Any idea on how to solve this? 
Best,

Dani

---

### Post by Phobiac on 2009-08-07
There are two things I'd try.
1) If conky is starting up but then closing, increase the sleep time. For example, try this.
```
#!/bin/bash
sleep 15 && conky ;
```
2) I'm not sure how much of a difference this makes, but my conky startup script has a space between "conky" and ";". So, try simply adding a space, like the code I put above.

---

### Post by alexandari on 2009-08-07
Go to system >> preferences >> sessions. And add conky :) It`s much easyer that way

---

### Post by acrocephalus on 2009-08-19
Hello,
My conky now starts on boot, using the bash script I posted, with a sleeping time of 15 second :). Now I have another problem :(. When booting, conky loads before the 15s, thus not loading properly. The, I have to re-load the X and the conky loads when required. Any idea on how to solve this?
Best,

Dani

---

### Post by wotsit on 2009-08-20
It sounds like either conky is running from sessions instead of the shell script running from sessions, or the sleep isn't long enough. I run mine with a 20 second sleep. So try this instead: (the script I assume is hidden in your home directory)
 
Make the .sh executable by
 
```
 
sudo chmod a+x .file_name.sh

```
 
Then in sessions, remove conky and instead, add the shell script by typing ~/.file_name.sh in the command box.

---

### Post by enli on 2009-08-20
Depending on your Ubuntu version and filesystem used (ext3/4) the time needed to actually boot will vary. So whenever you log in the login scripts are executed but the time needed to actually render the desktop will be much greater than 15sec. Try increasing this delay to more number.. maybe 30ish or even 50sec. That way you don't have to worry about reloading X.

Edit : I put all my scripts inside ~/Scripts folder. It looks better organization to me and easy to find the scripts next time you need to edit them.

---

### Post by acrocephalus on 2009-08-27
Sorry for the delay. I've been on holiday and forgot the PC completely. Now it works great.
Thanks!!

Dani

---

