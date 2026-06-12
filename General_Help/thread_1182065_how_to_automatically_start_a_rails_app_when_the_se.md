---
title: "how to automatically start a rails app when the server is rebooted"
date: 2009-06-08
forum: General Help
---

### Post by manokaran on 2009-06-08
Hi,

I have been trying to configure a Ubuntu 9.04 desktop system so that a rails app I have deployed on it starts up automatically when the system is rebooted.

I tried a simple setup where I created a script called start_rails in /etc/init.d and call it from the last line in /etc/init.d/rc.local. The start_rails script itself looks like this:

______________________
#!/bin/bash

/abs/path/to/rails/app/current/script/process/spawner mongrel --environment=production --instances=1 --port=8000

exit 0
______________________________

But the above does nothing! 

Can anyone explain how to get this right?

I went through the following link: 

[http://ubuntuforums.org/showthread.php?t=674598](http://ubuntuforums.org/showthread.php?t=674598)

but I dont want such a complex setup. Just the regular mongrel would do.

thanks,
mano

---

