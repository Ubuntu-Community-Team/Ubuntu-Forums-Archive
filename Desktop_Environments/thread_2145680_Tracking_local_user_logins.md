---
title: "Tracking local user logins"
date: 2013-05-16
forum: Desktop Environments
---

### Post by Berduchwal on 2013-05-16
I am looking to track when users login to their Ubuntu machines.

I have 4 machines with Ubuntu on them they all share dropbox accounts.

I wanted to track when each user logs in and out of a machine.

I have tried to view: /var/log/auth.log but it only holds few days worth of data and also is stored on a local machine.

I would prefare that there is a file in Dropbox to which all user have access and which is updated on login and log out giving time, machine name, user name, login/log out.

All users except one are non privileged users meaning they can not use sudo. 

What I was thinking of is having a script in Dropbox folder which is activated on login and log out.
This script I could then update and user PC would update it automatically.

Preferebly such a script would not require elevated privilages and I would only need to update start up routine somehow?

Any comments about my idea would be welcome.

```
#!/bin/bash    
DAT=$(date +"%Y%m%d,%T")
ENTR="$DAT,$HOSTNAME,$USER"
sleep 600
echo $ENTR >> $HOME/Dropbox/Technology/log.csv
```

I added sleep to make sure that entry is added to the latest version of the file. I added the script to start up application.

---

