---
title: "configure the resolution on the login screen"
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by Balvinder25 on 2007-08-19
hi all,
          I was just wondering as to how change the screen resolution on the login screen..usually i se 1024*768 @ 85 on the desktop but on the login screen this is  1284*1024@60 .but couldnt find any options anywhere to change these..so could any one help me on this..Thanks in advance..By the way i use 7.04

Regards,
balvinder

---

### Post by Chymera on 2007-08-21
stop your x and then run ```
sudo dpkg-reconfigure xserver-xorg
```

for more info check [http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#PROBLEMS_SECTION](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#PROBLEMS_SECTION)

---

### Post by runemaste644 on 2007-09-08
Is there a way to do that without editing my xorg.conf? I absolutely HATE editing my xorg.conf!!!!!

---

### Post by runemaste644 on 2007-09-08
Oh, and i also HATE dpkg-reconfigure because it broke my internet once!!!!!

---

