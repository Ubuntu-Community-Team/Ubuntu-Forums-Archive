---
title: "rc.local"
date: 2009-05-30
forum: General Help
---

### Post by Dork Lord on 2009-05-30
When I was using Mandriva 2009, I came across a solution to my problems with wireless internet. The command "iwconfig wlan0 rate 5.5M fixed" when run allows the card to function properly, so to make this run as root on every start up I did:

su
echo "iwconfig wlan0 rate 5.5M fixed" /etc/rc.d/rc.local

Is there a way to get the same result in ubuntu? I can work currently by just running the command every time I log in, but this would be more convenient.

---

### Post by ddrichardson on 2009-05-30
[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by Brandon Williams on 2009-05-30
On ubuntu, the file is /etc/rc.local, not /etc/rc.d/rc.local, but other than that, it works in the same way. Just put your code in /etc/rc.local and make sure that /etc/rc.local is marked executable.

---

