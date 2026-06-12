---
title: "Get back Ubuntu-desktop"
date: 2012-01-12
forum: Desktop Environments
---

### Post by frankie1234 on 2012-01-12
I was following this walkthrough:

[http://www.xappsoftware.com/wordpress/2010/10/26/ubuntu-10-10-and-iphone-tethering-solved-updated/](http://www.xappsoftware.com/wordpress/2010/10/26/ubuntu-10-10-and-iphone-tethering-solved-updated/)

And I ran the command at the end and it removed Ubuntu desktop. I still get the login screen but when I log in it just goes right back to the log in screen. Any advise?

---

### Post by varunendra on 2012-01-14
Not sure if it's gonna work, but try this:

[LIST]
[*]Boot in 'Recovery mode' option (you may have to press and hold 'Shift' key while booting to bring up the Grub menu)
[*]choose "root" option (drop to root shell prompt) in recovery menu
[*]issue this command: apt-get install --reinstall ubuntu-desktop
[*]reboot into normal mode and see if it allows you to log-in.
[/LIST]

---

