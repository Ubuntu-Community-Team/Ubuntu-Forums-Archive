---
title: "INITNG boot issues"
date: 2006-02-09
forum: Desktop Environments
---

### Post by naruto11111 on 2006-02-09
Hi, I'm new to linux.  My boot time is very very long.  It seems to get frozen on the configuring network part so I installed Initng according to the guides I found on this forum. ([http://ubuntuforums.org/showthread.php?t=80423&highlight=fast+boot](http://ubuntuforums.org/showthread.php?t=80423&highlight=fast+boot))

My first problem was it would only boot straight up to a command prompt but I found the answer to that problem on the forum.  I only have one more issue and I can't seem to find the answer.  Thanks in advance!

After I start up using the Initng boot, my wireless card is not detected or usable.  I tried to add the recommended script to activate wireless from:  [http://ubuntuforums.org/showpost.php?p=441841&postcount=55](http://ubuntuforums.org/showpost.php?p=441841&postcount=55)

That didn't work so I thought it might be because my wireless is labeled as wlan0 instead of eth1.  So I tried to do that whole step again replacing all instances of eth1 with wlan0 but it said that net/wlan0 is not a script.

Finally, I typed in:  sudo ifup wlan0 
after I booted up using Initng.  This seemed to bring my wireless card back up but I can't get network manager to run.  (nm-applet)  It shows that it is running under sessions, but it's not in my toolbar.  if I try to run it manually, it still won't show up.

Initng has made my system startup really fast now, If I could fix this last problem it would be great.  Thanks again!

-Michael

---

### Post by naruto11111 on 2006-02-23
Anybody?

---

### Post by yanns on 2006-02-23
You do not have to activate your wireless card if you want to use NetworkManager. (this is my case)

You should just need to add NetworkManager :
sudo ng-update NetworkManager
sudo ng-update NetworkManagerDispatcher

Check that  ps -A | grep NetworkManager returns two processes :
 6324 ?        00:00:00 NetworkManagerD
 6325 ?        00:00:00 NetworkManager

A final hint : you can try with "nm-applet --sm-disable"

---

