---
title: "Cannot install wireless patch : Permission denied"
date: 2009-01-07
forum: General Help
---

### Post by gaalaaant on 2009-01-07
I cant patch my wireless stuff, because each time I try i get : PERMISSION DENIED

daniel@daniel-laptop:/wifi$ sudo patch -p1 < 2.6.24.patch
bash: 2.6.24.patch: Permission denied


please help?

---

### Post by mssever on 2009-01-07
> **gaalaaant said:**
> I cant patch my wireless stuff, because each time I try i get : PERMISSION DENIED

daniel@daniel-laptop:/wifi$ sudo patch -p1 < 2.6.24.patch
bash: 2.6.24.patch: Permission denied


please help?
Make sure you have write permissions on all the files you're trying to modify.

---

### Post by gaalaaant on 2009-01-07
umm what exactly does that mean?

---

### Post by mssever on 2009-01-07
> **gaalaaant said:**
> umm what exactly does that mean?
Permissions control what you can and can't do with files. Google "linux permissions" for details. Use ls -l to see the current permissions.

Also, on re-reading your post, what are the permissions of the file 2.6.24.patch?

---

### Post by gaalaaant on 2009-01-07
Dude, I am a total noob here. I dont really kow how to get the permissions of that file, but i did use ls -l and this is wat I got, if I did it wrong, just tell me

daniel@daniel-laptop:/wifi$ 
daniel@daniel-laptop:/wifi$ ls -l
total 64
-r-------- 1 root root 6363 2009-01-08 04:39 2.6.24.patch
drwxr-xr-x 3 root root 4096 2009-01-08 04:39 ieee80211
-rwxr-xr-x 1 root root   54 2009-01-08 04:39 ifcfg-wlan0
-rwxr-xr-x 1 root root  196 2009-01-08 04:39 install
-rwxr-xr-x 1 root root  124 2009-01-08 04:39 makedrv
-rw-r--r-- 1 root root  681 2009-01-08 04:39 README.FIRST
-rwxr-xr-x 1 root root 5117 2009-01-08 04:39 ReadMe.txt
-rwxr-xr-x 1 root root  538 2009-01-08 04:39 release_note
drwxr-xr-x 3 root root 4096 2009-01-08 04:39 rtl8187
-rwxr-xr-x 1 root root  294 2009-01-08 04:39 wlan0dhcp
-rwxr-xr-x 1 root root  471 2009-01-08 04:39 wlan0down
-rwxr-xr-x 1 root root   75 2009-01-08 04:39 wlan0rmv
-rwxr-xr-x 1 root root  611 2009-01-08 04:39 wlan0up
drwxr-xr-x 6 root root 4096 2009-01-08 04:39 wpa_supplicant-0.5.3

---

### Post by mssever on 2009-01-07
> **gaalaaant said:**
> Dude, I am a total noob here. I dont really kow how to get the permissions of that file,That's why I suggested a Google search. > but i did use ls -l and this is wat I got, if I did it wrong, just tell me

daniel@daniel-laptop:/wifi$ 
daniel@daniel-laptop:/wifi$ ls -l
total 64
-r-------- 1 root root 6363 2009-01-08 04:39 2.6.24.patch
Yes, your permissions are wrong. Typing ```
sudo chmod 644 2.6.24.patch
```will fix them. But you really should read up on permissions so you understand why this fix works. It's a key part of working with Linux.

---

### Post by gaalaaant on 2009-01-08
yeah problem is unless i have an ethernet cord plugged in my connection drops every 5 minutes but i will look up permissions because I do want to get better at htis.

---

