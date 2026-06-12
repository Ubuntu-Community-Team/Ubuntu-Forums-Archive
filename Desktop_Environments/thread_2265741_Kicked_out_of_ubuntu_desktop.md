---
title: "Kicked out of ubuntu desktop"
date: 2015-02-17
forum: Desktop Environments
---

### Post by Byb on 2015-02-17
Hi I have precise with gnome-classic. Dealing with suspend/hibernate issues I noticed killing X between suspend or hibernate allowed me to send a second suspend/hibernate request successfully, when they crash if I leave X living between.
From tty1 I sent sudo service lightdm restart to see if the effect was the same.
Now I am unable to login into lightdm: the session opens then closes as soon.

Please help

I tryied sudo dpkg-reconfigure lightdm , then I selected both lighdm or gdm, but it always reboots to lightdm.
There is a message that says I must edit X servers startup scripts in /etc/init.d and remove the test but I don't know how to do this.
I just can log ok in tty, so no password issue.

Thank you very much

---

### Post by Byb on 2015-02-26
startx 
message about .Xauthority file

---

