---
title: "Problem running Twonky Media on Ubuntu Server 8.10"
date: 2009-06-08
forum: General Help
---

### Post by Nixie Pixel on 2009-06-08
Hello, I recently tried to install Twonky Media version 5.0 on Ubuntu Server 8.10. I followed both the manual installation instructions and the script installation instructions, and I am having the same error each time.

Whenever I try to run the twonkymedia .sh file or run the twonkymedia file it tells me that there is "no such file or directory." I changed the permissions to be 777 to ensure there was no permissions problem, and tried using both a fully qualified path (i.e. /home/nixie/.twonkymedia/twonkymedia) and ./twonkymedia, but none of it works, it keeps telling me it does not exist, even though it does.

Can anyone tell me why Ubuntu Server insists that these files do not exist when I try to run them?

Thanks!

---

### Post by stewiefet on 2009-06-12
I'm having the exact same problem.    Anyone have any suggestions?

---

### Post by agzela on 2009-06-16
I had the same problem just use the manual .zip files instead of the .sh file(download from twonkymedia) copy .zip to /usr/local make sure you are doing all this as root, run unzip on the file (if you dont have unzip then do 'apt-get install unzip' first) overwrite old install if you had one with the exception of the key file(it says it in its name). then type (serveripaddress):9000 on web browser. configure twonky via web interface....

Easy!

FYI - I found that if you use 5.0.65 the .sh will work go here and download [http://www.twonkyforum.com/unsupported/5.0.65/](http://www.twonkyforum.com/unsupported/5.0.65/)

I found problems with 5.0.61 and the proper DLNA recognizing of a PS3 so use 5.0.65 works great so far watched several movies using twonky/Ubuntu 9.04 Server streaming to PS3 and other DLNA devices.

---

