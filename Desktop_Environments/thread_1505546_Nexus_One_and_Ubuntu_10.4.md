---
title: "Nexus One and Ubuntu 10.4"
date: 2010-06-09
forum: Desktop Environments
---

### Post by shawalli on 2010-06-09
I cant get the adb to see my nexus one in ubuntu.  Ive tried many different things, including [http://www.lukejduncan.com/2010/04/getting-the-nexus-one-and-the-adb-working-in-fedora-12.php](http://www.lukejduncan.com/2010/04/getting-the-nexus-one-and-the-adb-working-in-fedora-12.php)  does anyone have any suggestions or workarounds?

---

### Post by shawalli on 2010-06-09
i ran lsusb in terminal and can in fact see the nexus one, so i know its at least being read by the system.  The ID number on there is "18D1", so the rules link from above is using the correct vendor id.  

BTW, i forgot to mention that when i try to run adb with "./adb devices" i get "??????? no permissions".  When I run adb with the emulator running and type "./adb devices" it recognizes the emulator as "emulator-5554 device".

---

### Post by StevieS on 2010-08-16
Hi there, I came across your question while trying to find a solution to the same problem.  I have no idea whether you have already found the answer yourself, but just in case, and for the benefit of others in the same situation I'll post the solution.

Instead of running adb as the local user, you need to run it as root, so to start the server try

```
sudo <PATHTO>/adb start-server
```

running

```
adb devices
```

then correctly lists my device.

If you are already running adb as the local user, then issue this command first to ensure that it has shut down correctly,

```
adb kill-server
```

Hope this helps you out.

---

### Post by Ridor on 2010-11-20
Thank you - I was having trouble with this as well.

---

### Post by ralph240574 on 2011-01-19
Thanks, this was the missing piece

---

