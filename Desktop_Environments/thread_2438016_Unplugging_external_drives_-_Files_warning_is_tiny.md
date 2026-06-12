---
title: "Unplugging external drives - Files warning is tiny and silent"
date: 2020-03-04
forum: Desktop Environments
---

### Post by arvindp3 on 2020-03-04
I am using Ubuntu 18.04 with GNOME desktop.  

While safely removing an external hard drive (or USB stick), Files does issue notifications as stated in the link below ("Writing data to ....... Device should not be unplugged...").  Once the data transfer is complete, the message for safely removing the device also appears normally.

See: [(https://help.ubuntu.com/stable/ubuntu-help/files-removedrive.html.en)  But these notifications are so tiny and silent that it is easy to not notice them. The risk of not noticing them and removing the drive prematurely by mistake is obviously high.   Is there any way to customize these notifications to make them appear more boldly, and with a audible tone?"] https://help.ubuntu.com/stable/ubuntu-help/files-removedrive.html.en]("http://I am using Ubuntu 18.04 with GNOME desktop.    While safely removing an external hard drive (or USB stick), Files does issue notifications as stated in the link below (&quot;Writing data to ....... Device should not be unplugged...&quot;).  Once the data transfer is complete, the message for safely removing the device also appears normally.  See:  [https://help.ubuntu.com/stable/ubuntu-help/files-removedrive.html.en)

But these notifications are so tiny and silent that it is easy to not notice them. The risk of not noticing them and removing the drive prematurely by mistake is obviously high. 

Is there any way to customize these notifications to make them appear more boldly, and with an audible tone?

---

### Post by Dennis N on 2020-03-04
These are controlled by the Gnome Shell Theme. Some have larger notification bubbles*, so try some different ones. Or, you may be able to edit settings in the gnome-shell.css file for your existing gnome shell theme. System sounds: be sure system sound volume is turned up in Settings > Sound. There is a very audible sound when inserting or removing USBs (at least in Ubuntu 19.10)

*for example, these are somewhat larger with larger text in **Flat-Remix-Dark** gnome-shell theme, but I'm using Ubuntu 19.10. (Later tried this theme in Ubuntu 18.04, and it works fine there too.)

---

### Post by arvindp3 on 2020-05-26
Thanks

---

