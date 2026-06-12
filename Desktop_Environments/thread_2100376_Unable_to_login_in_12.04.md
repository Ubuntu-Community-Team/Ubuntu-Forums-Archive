---
title: "Unable to login in 12.04"
date: 2013-01-01
forum: Desktop Environments
---

### Post by jackal_79 on 2013-01-01
Hi, Iam currently unable to login to my ubuntu 12.04. It was working fine until afternoon. Earlier i tried playing a video file and player got stuck. I tried different players and all had same result. Other applications were working fine.Then i switched off my machine. When i booted up later iam getting logging screen but it is not accepting password(Shaded mode). When reboot didn't work i logged in to previous kernel at which time it was taking password, but immediately after that it again showed the login screen. I tried with gnome, gnome classic and ubuntu .But all showed same result. Please advice,

---

### Post by speedwlk on 2013-01-01
> **jackal_79 said:**
> Hi, Iam currently unable to login to my ubuntu 12.04. It was working fine until afternoon. Earlier i tried playing a video file and player got stuck. I tried different players and all had same result. Other applications were working fine.Then i switched off my machine. When i booted up later iam getting logging screen but it is not accepting password(Shaded mode). When reboot didn't work i logged in to previous kernel at which time it was taking password, but immediately after that it again showed the login screen. I tried with gnome, gnome classic and ubuntu .But all showed same result. Please advice,


This is a shot in the dark, but try it out. My guess is that the ".ICEauthority" in your home folder may be giving trouble.

Step1: boot with recovery mode and get into root prompt. This will give you direct admin rights. [use with caution]

Step2: The root is now mounted with read-only mode. To get read-write permission do
```

mount -o remount,rw /

```If you have a separate /home partition, you will need to mount it also.

Step3: Get into your home folder by
```

cd /home/USERNAME/

```here replace "USERNAME" accordingly.

Step 4: change ownership of the file ".ICEauthority" by
```

chown USERNAME:USERNAME .ICEauthority

```step 5: restart your machine
```

reboot

```and see if you are now able to login.

If not, then redo the above steps with step4 altered as follows
```

mv .ICEauthority .ICEauthority.bak

```Hopefully this is the issue. Good luck.


EDIT:  Should have thought of it earlier, before I posted. Do not go into recovery mode. At your login screen, switch to console mode by "CTRL+ALT+F1". You will be given option to type in your USERNAME and PASSWORD.
After logging in, try step 4. [prepend "sudo", if required].
To go back to desktop mode, try the key combination "CTRL+ALT+F7". Try logging in now.

---

### Post by zombifier25 on 2013-01-02
My solution that I gave (and solved) many people's same problem is the same as above, but the file is .Xauthority . Since we're stabbing people in the dark here, try both files.

---

### Post by jackal_79 on 2013-01-02
i have tried with both files. still no change. sometime it shows login screen. after i type password it again shows login screen in a shaded mode. Any more ideas?

---

### Post by jackal_79 on 2013-01-03
Can someone help me on this please?

---

### Post by steeldriver on 2013-01-03
Can you log in at a virtual terminal (Ctrl-Alt-F1 etc.)? or are you only able to get in by booting to the recovery (root) console? 

Does Guest login work?

Are you able to check that your home partition is not full and your home dir is writeable?

```
$ df -h /home
``````
$ ls -ld $HOME
```

---

### Post by jackal_79 on 2013-01-05
> **steeldriver said:**
> Can you log in at a virtual terminal (Ctrl-Alt-F1 etc.)? or are you only able to get in by booting to the recovery (root) console? 

Does Guest login work?

Are you able to check that your home partition is not full and your home dir is writeable?

```
$ df -h /home
``````
$ ls -ld $HOME
```

Well, i can login through virtual terminal. Incidentally, today i was able to login after i selected the previous version of kernel in GRUB. I don't know whether it will still work after re-boot and i still don't know what is the issue.
Any ways, iam posting the output for your commands.

========================================================
jackal@Treadstone:~$ df -h /home
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        81G   14G   63G  19% /
jackal@Treadstone:~$ ls -ld $HOME
drwxr-xr-x 37 jackal jackal 4096 Jan  5 22:16 /home/jackal
=========================================================

---

