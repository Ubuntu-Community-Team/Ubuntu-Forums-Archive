---
title: "can't login to gnome"
date: 2011-02-21
forum: Desktop Environments
---

### Post by paul555 on 2011-02-21
Hi all i have a very big problem. When the last time i logged in gnome my laptop freezed. After that i can't login to gnome and it shows me that my user is currently logged in. I created a new user and he can login ok, Any ideas how to fix it?

---

### Post by Krytarik on 2011-02-23
Although this seems to be an odd question, but nevertheless makes really sense: Did you shutdown/reboot since that happened?

---

### Post by paul555 on 2011-02-24
Yes i shutdown and restart my machine many times. Now i created a new user who can login ok. Now how can i migrate my settings from the older user to the new one?

---

### Post by amsterdamharu on 2011-02-24
Just a shot in the dark here but I see i've got a file called ~/.bash_logout and according to the texton the top it is "executed by bash(1) when login shell exits."

You could try logging in as the user in a terminal (press control + alt + F1 and log in) then run the following command:

```
bash ~/.bash_logout
```

Don't know if that will clean up any stuff that locks you from logging in but it's worth a try.

---

### Post by Krytarik on 2011-02-24
Try to log out your old user in the following way:

- login either with the new user (if you assigned it to the admin group) or via recovery mode/root shell prompt
- check if your old user is indeed still logged in
```
who
```- try to kill all processes started by it and log it out
```
sudo pkill -KILL -u username
```You don't have to use "sudo" if issuing the command from the root shell prompt.

---

### Post by paul555 on 2011-02-25
Krytarik thank you it worked :D

---

### Post by Krytarik on 2011-02-25
> **paul555 said:**
> Krytarik thank you it worked :D
Great! :)

Then please mark this thread as "solved", via "Thread Tools".

---

