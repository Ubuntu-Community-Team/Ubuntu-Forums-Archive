---
title: "No Kernel Options at boot time"
date: 2009-06-17
forum: General Help
---

### Post by edkilp on 2009-06-17
Hi everyone. I'm running 9.04. I have also installed the real-time  kernel 2.6.28-3-rt. When I boot my machine, I get no list to choose from. No memtest, no recovery mode, nothing. Just goes straight from the Ubuntu bootsplash to the desktop. uname -r tells me i'm running 2.6.28-11-generic. I'm thinking I have to edit my menu.lst? Any help would be appreciated. Thanks
ed

---

### Post by redilyn on 2009-06-17
Try the following

```

sudo gedit /boot/grub/menu.lst

```

Comment out the hidden menu entry.

```

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]#hiddenmenu[/COLOR]

```

Also check the timeout to make sure its not 0

```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).[COLOR="Red"]
timeout		10[/COLOR]

```

Save and reboot

---

### Post by edkilp on 2009-06-18
Thanks very much. That did the trick!. Unfortunately, just as I've been reading, the rt kernel doesn't play well with nvidia drivers. But at least I can get to it now! Thanks again
ed

---

