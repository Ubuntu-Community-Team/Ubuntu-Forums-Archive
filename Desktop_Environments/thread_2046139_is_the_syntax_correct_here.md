---
title: "is the syntax correct here:"
date: 2012-08-22
forum: Desktop Environments
---

### Post by bilboubu on 2012-08-22
#!/bin/bash
ping -c 2 192.168.0.2 >/dev/null
if [ $? -eq 1 ] ; then
/usr/bin/wakeonlan 00:1d:92:dd:1a:0d
sleep 5
if [ "$(pidof xbmc.bin)" ] ; then
killall -9 xbmc.bin
sleep 60 
fi
fi

so if ping responds do nothing, if not the wake the remote computer, check for xbmc.bin locally, if xbmc.bin found kill it.

I want the sleep 60 to only run if xbmc.bin is not found.

---

### Post by bilboubu on 2012-08-22
tried 

#!/bin/bash
ping -c 2 192.168.0.2 >/dev/null
if [ $? -eq 1 ] ; then
/usr/bin/wakeonlan 00:1d:92d:1a:0d
sleep 5
if [ "$(pidof xbmc.bin)" ] ; then
killall -9 xbmc.bin
else
sleep 60 
fi
fi


but seems to have failed

---

### Post by efflandt on 2012-08-22
"failed" is ambiguous.  Did you get an error?  Did it not wake the other computer?  Who was xbmc.bin running as, and are you that user or have permission to kill a process of that user?

It can help to liberally sprinkle a script with echo statements while developing it, so you can tell what path it followed, or if the result of part of it was different than you expected.  Or add additional tests to see if the wakeonlan was successful and xmbc.bin was actually killed.

When posting a script, it also helps to wrap it in code tags (highlight it and click **#** in message window) in case missing spaces or formatting matters.

---

