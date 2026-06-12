---
title: "Find and/or delete expired users?"
date: 2009-02-19
forum: General Help
---

### Post by pmgeahan on 2009-02-19
FOlks - 

Fresh install of Intrepid on a Dell server.  This server is going to be used by external parties to get information from us.  As such, we expect to create lots of short-term users.  

I'm expiring a set of users after seven days.  The expiration works fine - after seven days, the users can no longer login.  However, I'm trying to figure out a way to locate those expired users and delete them.  Preferably, I'd like to be able to run a cron job every night that looks for expired users and wipes them off the system.

Is there any method I can use to find expired users?

---

### Post by sdennie on 2009-02-19
I'm not a sysadmin so there may be a better way but, if your disks aren't using noatime or nodiratime, you can simply write a script to check the last access time of the inode for every user directory.  This isn't a solution but, it's the basic idea:

```

#!/bin/bash

cd /home
for file in `echo *`; do
echo "$file"
stat $file | grep Access | grep -v \( | awk '{print $2;}'
echo
done

```

---

### Post by pmgeahan on 2009-02-19
> **sdennie said:**
> I'm not a sysadmin so there may be a better way but, if your disks aren't using noatime or nodiratime, you can simply write a script to check the last access time of the inode for every user directory.  This isn't a solution but, it's the basic idea:

That's a good idea.  It'll lag about a week behind the actual expiration, but that really shouldn't matter.  Actually, that's probably a good idea in and of itself.

---

### Post by heindsight on 2009-02-19
You could use 
```
chage -l username
``` for each user, grab the account expiry date from that, and use ```
date
``` to test if that is before today.

perhaps something similar to this:
```
#!/bin/sh

today=`date -d 0:00today +%s`

check_expired() {
  local e expire

  e=`chage -l $1 | awk -F: '/^Account expires/{ print$2 }'`
  if [ "$e" = " never" ]; then
    return 1
  fi

  expire=`date -d "$e" +%s`

  if [ $expire -lt $today ]; then
    return 0
  else
    return 1
  fi
}

awk -F: '{ print$1 }' /etc/passwd | while read name; do
  if check_expired $name; then
    echo "Account $name has expired"
  fi
done
```

EDIT:
Of course if you want accounts to hang around for a while before removing them, you could just change ```
today=`date -d 0:00today +%s`
``` to something else, like say:
```
today=`date -d "0:00last week" +%s`
``` Although you'd probably want to rename the variable then ;)

EDIT2:
You probably don't want to check all users. You might want to use something like:
```
awk -F: '( $3 >= 1000 ) && ( $3 < 65534 ) { print$1 }' /etc/passwd
```
instead of
```
awk -F: '{ print$1 }' /etc/passwd
```
to only test users with uid > 999 (except nobody who has uid=65534).

---

