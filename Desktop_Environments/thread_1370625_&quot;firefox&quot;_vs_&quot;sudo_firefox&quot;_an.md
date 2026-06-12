---
title: "&quot;firefox&quot; vs &quot;sudo firefox&quot; and flashplayer.so"
date: 2010-01-02
forum: Desktop Environments
---

### Post by gstanden on 2010-01-02
Hi, have a problem with using flash in youtube.com -- if i run firefox from the ubuntu karmic launcher icon in the toolbar -- as myself -- I get a black screen in youtube.com and no video delivery...if I run it from terminal as "sudo firefox" I get excellent and error-free flash video delivery and content.

I've looked at about:plugins and they look the same
I've opened up permissions on every copy of libflashplayer.so I can find on the disk...

I still have to launch firefox as "sudo firefox" or I cannot get flash content delivery.

Any ideas on how to get this to support flash without having to open firefox in terminal using "sudo firefox"?  It seems like an env or permissions problem, but so far have not found what it is...

TIA

---

### Post by gstanden on 2010-01-02
Well here is how it was "fixed" - although I still don't have the exact picture of exactly why this worked - but here is how I fixed it:  

cd /home/username

mv .mozilla .mozilla.bak

reboot machine

now firefox is finding and using the flashplayer.so just fine, either from toolbar application launcher or from "sudo firefox"

Note, do not delete .mozilla but rather rename it as above or you will lose your bookmarks etc.

---

### Post by lovinglinux on 2010-01-02
NEVER, NEVER start Firefox with sudo. When you do that, it starts as root, but using your FF profile, so you loose ownership of the .mozilla folder and get all sorts of errors, like not being able to save bookmarks.

If you need to run Firefox with administrative rights, which I don't see a good reason to do it, then use gksudo instead, so it will use the root profile instead of yours.

To regain ownership of your profile run this, without modifying anything:

```
sudo chown -R $USER:$USER ~/.mozilla
```

See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by gstanden on 2010-01-02
the "good reason" was that libflashplayer.so plugin was not working and so I tried "sudo firefox" and then it worked - so this was a problem solving hair-pulling adventure and if I had known a better way to diagnose and fix this I would have...

in any case, thank you for your post and for taking the time to reply... :-)

---

