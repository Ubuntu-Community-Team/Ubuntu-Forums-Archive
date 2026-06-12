---
title: "running a service on start up"
date: 2009-06-16
forum: General Help
---

### Post by zoomiest on 2009-06-16
I just installed CATS applicant tracking system ([www.opencats.org](www.opencats.org)), and run the Sphinx (sphinx_for_cats) indexer, and it all went well, but (last step) it seems that the last piece of instruction was to

"Run chkconfig to run Sphinx on startup."

            ```
chkconfig --add searchd
```

but, it seems that my Ubuntu server (8.04.1) doesn't have chkconfig, and an attempt to use apt to download it... failed. 

What tool would I use instead of chkconfig to add a service to the start up list, so it will initiate when I, for example, reboot the computer?

---

### Post by billgoldberg on 2009-06-16
Try this:

[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by Cheesemill on 2009-06-16
Try installing and running sysv-rc-conf (it's a terminal program).
If Sphinx is listed you can enable it to run at startup.

This may not work as Ubuntu uses a different style of init scripts than Red Hat (which is where the chkconfig is used).

---

### Post by nutznboltz on 2009-06-24
> **zoomiest said:**
> but, it seems that my Ubuntu server (8.04.1) doesn't have chkconfig, and an attempt to use apt to download it... failed. 

What tool would I use instead of chkconfig to add a service to the start up list, so it will initiate when I, for example, reboot the computer?

Just use chkconfig -- it's good enough for esr: [http://www.mail-archive.com/upstart-devel@lists.ubuntu.com/msg00217.html](http://www.mail-archive.com/upstart-devel@lists.ubuntu.com/msg00217.html) ;)

I have attached the script and manpage from esr's post as a shell archive.  Download the attachment and run```
mkdir chkconfig; mv chkconfig.sh chkconfig; cd chkconfig ; sh chkconfig.sh; rm chkconfig.sh
```to unpack.  Then install with:

```
sudo mv chkconfig /usr/bin; sudo mv chkconfig.8 /usr/share/man/man8
```

---

