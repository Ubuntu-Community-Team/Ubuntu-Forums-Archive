---
title: "a very long silent wait after log in"
date: 2006-09-29
forum: Desktop Environments
---

### Post by ryu kun on 2006-09-29
Hi everyone,

After I type my username and password in log in screen, ubuntu waits for 2-3 minutes, apparently doing nothing. there is even no sound coming from HDD. nothing on the screen, only my mouse pointer. after the long wait finishes, ubuntu startup sound comes and that little startup window appears.

How can I get rid of this?

Thank you!

---

### Post by henriquemaia on 2006-09-29
Maybe something in your home configurations is borked. Test this out creating a new user and login in with it. Do not use an existing one, but create it for the test. Check the startup times.

---

### Post by ryu kun on 2006-09-29
I created a new user and tested. It waits like the other.

Is there a log somewhere to check?

---

### Post by darrenm on 2006-09-29
Run top on a PTS while waiting for the login and see if anythings taking the CPU hostage.

---

### Post by ryu kun on 2006-09-29
> **darrenm said:**
> Run top on a PTS while waiting for the login and see if anythings taking the CPU hostage.

Sorry, what is PTS and how can I run it? :confused:

---

### Post by henriquemaia on 2006-09-29
A real terminal. Press ctrl+alt+F1 (or any F until F6)

Login there and run **top**, change back to X session pressing ctrl+alt+F7, login and return to your terminal session.

---

### Post by ryu kun on 2006-09-29
ctrl+alt+F1 to F6, all terminals are blank here.. No cursor, nothing.. Just black screen.

---

### Post by darrenm on 2006-09-29
Sorry for the geekspeak.

Can you post the output of 
```
sudo cat /var/log/messages | tail -n 50
```

after you have logged in?

---

### Post by ryu kun on 2006-09-29
It's all right. 

The log is attached (hopefully) :)

---

### Post by chrisccoulson on 2006-09-29
I bet the problem is that your local loopback interface is not coming up automatically. Look here: [http://www.ubuntuforums.org/showthread.php?t=265628]("http://www.ubuntuforums.org/showthread.php?t=265628")

---

### Post by ryu kun on 2006-09-29
Thanks but I've added these first two lines but didn't help... :(

```
auto lo
iface lo inet loopback

#auto eth1
#iface eth1 inet dhcp
```

In the atteched log there is a failure message:
```

Sep 29 15:25:46 localhost gconfd (ertugrul-10477): Failed to send buffer
Sep 29 15:25:46 localhost last message repeated 9 times
```

Maybe there is something wrong with gconfd...?

And ```
sudo gedit
``` or ```
gksudo gedit
``` commands strangely don't work, I've been using nano to make these changes..

---

### Post by ryu kun on 2006-10-01
I just wanted to add that this strange delay has strangely disappeared...

---

