---
title: "X11 forwarding via telnet"
date: 2006-08-11
forum: Desktop Environments
---

### Post by monteros on 2006-08-11
I know telnet... why the hell... I have to administer very old box that the client doesn't want to use ssh on... long story, anyway, I am having issues trying to get X to display back to my ubuntu test box.

I have done the following:
xhost +
Login Window> Preferences> Unchecked "Deny TCP Connections to Xserver"

Still can't get X to display back to the Ubuntu box.

Any ideas?

Thanks!
-Monteros

---

### Post by monteros on 2006-08-11
Found this and going to try it> In Ubuntu the X server by default does not listen on a TCP socket, meaning that your Sun machine cannot reach it over the network. This is done for security reasons and since ssh -X is a better solution than the xhost stuff you should better leave it this way.
If you want to make X11 listen on a TCP socket nonetheless you have to edit the file /etc/X11/xinit/xserverrc and remove the '-nolisten tcp' option from it.

---

### Post by monteros on 2006-08-11
Yup the above worked just fine.

---

