---
title: "Delete unnecessary files..."
date: 2006-02-10
forum: Desktop Environments
---

### Post by iemand on 2006-02-10
Hi guys, 

I'd like to make the cleaning on my KUbuntu 5.10. And then, I wonder, is there some directories like windows' temp folders that we can clean up and retrieve some spaces on the hard-drive ?

I guess /tmp ? 

But is there a place where apt-get downloads packages and that we need to delete by ourselves ?
When I make an full-update, are old packages automaticaly deleted ?

... 

Can you tell me more about how can I clean my system ?

Thanks in advance

---

### Post by heimo on 2006-02-10
I think /tmp is automatically emptied at every boot (not sure). Also I believe cache for apt is emptied using "scheduled jobs", cron. You can empty the Trashcan (I think it's just a hidden directory .Trashcan or something like that in homedirectory) and you can "manually" clean apt's cache using:
```
sudo apt-get autoclean
``` or 
```
sudo apt-get clean
``` 

From apt-get's man page:
>        
clean  
clean clears out the local repository of retrieved package files. It removes everything  but  the  lock
              file  from  /var/cache/apt/archives/  and  /var/cache/apt/archives/partial/. When APT is used as a dse-
              lect(8) method, clean is run automatically. Those who do not  use  dselect  will  likely  want  to  run
              apt-get clean from time to time to free up disk space.

       autoclean
              Like  clean,  autoclean  clears  out the local repository of retrieved package files. The difference is
              that it only removes package files that can no longer be downloaded, and are largely useless. This  al-
              lows  a  cache to be maintained over a long period without it growing out of control. The configuration
              option APT::Clean-Installed will prevent installed packages from being erased if it is set to off.

---

### Post by Ramses on 2006-02-10
There is .thumbnails folder in your home directory which contains konqueror's thumbnail pictures. There could be quite many useless old thunbnails.

---

### Post by iemand on 2006-02-10
Thanks all of you for these fast answers. :--)

---

### Post by engla on 2006-02-10
This is interesting..
Gnu/Linux keeps most things clean; /tmp is cleared on boot, logs are compressed and rotated and the apt-cache is trimmed over time (when you use apt-get etc).

However, does Gnome (and/or KDE) never clean the ~/.thumbnails directory? It's quite irresponsible to let things just sit there and grow, no matter how slow the growth is.
Something to do about this, to automate it? Something already done?

---

### Post by andlinux21 on 2006-07-11
i just tried the apt-get autoclean and it did find some files so thanks for that info

---

