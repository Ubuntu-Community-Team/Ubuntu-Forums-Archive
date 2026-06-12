---
title: "Desktop Notification not working"
date: 2010-12-23
forum: Desktop Environments
---

### Post by Guruprasad on 2010-12-23
I have a script running every 5 mins as user mail.
I want to send desktop notification through this script.
I tried notify-send by no success.
Can anyone help me regarding this?

---

### Post by anglican on 2010-12-23
> **Guruprasad said:**
> I have a script running every 5 mins as user mail.
I want to send desktop notification through this script.
I tried notify-send by no success.
Can anyone help me regarding this?notify-send is the way I'd do this. Why didn't it work - how were you trying to use it?

H

---

### Post by Guruprasad on 2010-12-23
> #!/bin/sh
notify-send "Bhoomija" "Starting Bhoomija script."

I am runnin the script as cron job for mail user.

---

### Post by anglican on 2010-12-24
> **Guruprasad said:**
> I am runnin the script as cron job for mail user.Then you need to be very careful about the user environment, and specifically the user's PATH. cron does not give you the same path that a shell does, it's much shorter. Give everything its full path in scripts. Use:
```
which notify-send
```in a shell to find out what the full path is. Do the same for any other commands used also, including commands used in scripts that you run with cron.

H

---

