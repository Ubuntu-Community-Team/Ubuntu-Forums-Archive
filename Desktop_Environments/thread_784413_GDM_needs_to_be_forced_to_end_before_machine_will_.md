---
title: "GDM needs to be forced to end before machine will shutdown / logoff / restart"
date: 2008-05-06
forum: Desktop Environments
---

### Post by tim_wright on 2008-05-06
Hello, thanks for taking the time to come and read this.

My problem is that when I logoff / shutdown / restart ubuntu GDM does not end. I then have to kill it via Ctrl + Alt + Backspace and everything works fine. Could someone tell me where to get the error logs and I will post them here for us to sort out. 

Ubuntu 8.04 - Hardy Heron x64
Fully updated. 

Thanks

---

### Post by tim_wright on 2008-05-26
I found the solution to this. The problem lies with keytouchd (the daemon) it cannot kill its processes and therefore refuses to let x shut down. Here is the site:

[https://bugs.launchpad.net/ubuntu/+bug/186713/comments/42](https://bugs.launchpad.net/ubuntu/+bug/186713/comments/42)

If you found this helpful please add a reply and hopefully the problem will be fixed soon.

Thanks,
Tim

---

### Post by gummygod on 2008-07-16
ive had the same problem.  altho after i did 'sudo reboot' i could restart using the gui thing in the corner from then on.  not sure if it works with logout also

---

