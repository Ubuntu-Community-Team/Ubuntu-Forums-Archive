---
title: "Trying to troubleshoot what went wrong with my bin/bash rsync script."
date: 2009-01-18
forum: General Help
---

### Post by Roasted on 2009-01-18
I had an rsync script set up.

```
sudo rsync -a --progress --delete --exclude=.gvfs ~/ /media/localbackup
```

I decided to change it to this.

```
sudo rsync -a --progress --delete --exclude=.gvfs /home/jason /media/localbackup
```

Suddenly my backup drive got maxed out because doubles were transferred over. I don't know how, I don't know why, and quite frankly I don't even know where the extra data was because I did not see it on the backup drive. I just saw my hard drive activity in system monitor start bugging out with high activity, so I knew that more data was transferred. I also noticed that my drive had 0 bytes remaining.

I changed my script back, so instead of /home/jason it just read ~/ (which means my home directory anyway) and re-ran the script. Since I have the --delete function, it deletes anything that isn't on the original drive. Now, it's back to normal.

But, what in the world was different that could have caused that?

ALSO - When I booted up, somehow my hard drives just took off... like my activity just went crazy right away when I didn't even run the script. What in the world would provoke a hard drive to have such high activity (I'm talking 80-100% steady) when booting up? My space was decreasing, so I assumed it was due to the drive adding data, which was consistent with what was happening earlier when my script was acting goofy.

What would cause my drives to do that automatically?
Is it due to the fact I rebooted when my drives were under high activity? I rebooted cause I wanted to "cancel" what was happening and when it booted up my drives took off.

I've rebooted several times since I put my script back to ~/ and ran it, and everything seems perfectly fine. But like I said, I'm assuming that due to the fact I rebooted during mid-data transfer earlier that when I booted up again, my backup drive just started going again. Does that sound possible? 

Thanks for any input you folks can offer.

---

