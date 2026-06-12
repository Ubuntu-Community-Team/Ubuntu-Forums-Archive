---
title: "cant see or use desk top"
date: 2008-02-15
forum: Desktop Environments
---

### Post by rtprice on 2008-02-15
ubuntu has loaded fine in the past .it loads and checks for updates  and the screen goes blue then grey-black.right click does nothing live cd gets me to firefox .installed simple back up but i dont know how to use it yet,i am new to ubuntu .iam not familar with any thing but windows.i am trying to get away from windows.please help .thank you in advance

---

### Post by gavintlgold on 2008-02-16
If you can't update because of the problem, you might want to try starting up in recovery mode (hit escape when GRUB counts down at boot, and choose the recovery mode from the list)

That should keep you in a black screen, where you can login and then type 
```
sudo apt-get update
```
and then
```
sudo apt-get upgrade
```
When you are done, try restarting again by typing control-alt-delete. I've never heard of this problem, but maybe, just maybe, updating this way will fix it.

Hope that helps.

---

### Post by rtprice on 2008-02-16
thanks ,it updates and all like that but i cant see desktop,iwas trying to install compiz and  went to windows to check when i rebooted back to ubuntu desk top went away
                                   thank you

---

### Post by rtprice on 2008-02-16
i have reinstalled ubuntu so problem solved thanks:):)

---

