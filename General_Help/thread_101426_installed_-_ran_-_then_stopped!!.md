---
title: "installed - ran - then stopped!!??"
date: 2005-12-09
forum: General Help
---

### Post by Phreezzz on 2005-12-09
Hi community
this is a first post, and I have done a quick search in case the answer is lying in the archives somewhere, but so far, not found
Installed 5.10 on my wifes laptop for her, she was tired of XP!
Great first three days, then after an accidental shutdown due to power loss (she thought it was plugged in!) it now wont start
Fires up to X login, enter username and password but then displayes message that session lasted less than 10 seconds blah blah blah
Viewing /.xsession-errors  highlights are
/etc/gdm/Xsession: Beginning sessions stgartup
_IcetransTransNoListen: unable to find transport tcp
followed by about ten more lines of errors ending with
unable to read ICE authority file:  /home/cindy/.ICEauthority

I have no idea how to fix this problem, surely not another install?

Thanks in advance guys!
Phil

---

### Post by amohanty on 2005-12-09
Boot up and login in recovery mode
then :

```
cd ~cindy
chown cindy:cindy .ICEauthority

```

reboot login normally again.

HTH

If by any chance I am wrong on the name of the file, just do that for the file that starts with .ICE....
not on my boxen right now.

---

### Post by Kobra on 2005-12-09
Amohanty, I'm thanking you aswell.  I updated my ATi drivers and the same exact thing happened to me.  LOL.  What are the odds of that happening?

---

### Post by amohanty on 2005-12-09
You are welcome. Well anytime, you are in root mode and crash and burn it could happen.

---

### Post by Phreezzz on 2005-12-10
Thanks for responses but ----
Logged in again in recovery mode
cd ~cindy no problem
then
chown  the ICE file and response is ---- no such file or directory
While in cindy I did ls to see what is listed
I now only have Desktop, Evenescence and Images, in blue so these are directories
Nothing else
Dont look good?
Thanks

---

### Post by kaamos on 2005-12-10
Try "ls -la".

---

### Post by amohanty on 2005-12-10
> chown the ICE file and response is ---- no such file or directory

As kaamos suggested try 

> ls -la

The filename is .ICEauthority, I have edited the original post so try it again. I was off on the case of 'a'.
Also keep in mind that there is a "." infront of the filename. Its important because all files with a "." as prefix are hidden files ie not visible by > ls but are visible using the -a flag.

HTH

---

### Post by Phreezzz on 2005-12-10
Thanks everyone
This did it
Only modification I had to make to these instructions was first
sudo -s
otherwise I had an 'operation not permitted' message
All is working now, wife is not going back to MS and happines pervades the early morning household!
Thanks a million

---

