---
title: "random screen freezes in 8.10"
date: 2008-12-06
forum: General Help
---

### Post by aaronLund on 2008-12-06
Hi all.

I'm using envy with my Nvidia GeForce Fx 5200.....just got that working a week or so ago and its nice!

I thought this would solve my random freezes but it really hasn't.  I think they occur less-often now but they're still happening.

Basically, what I'd like to know is if there's any sort of log that I can look at to diagnose what's causing these freezes.  

I should note that they never happen when I'm using the computer.  It's only after I've been away, I'll come back to my desk to find my my screen is black but my mouse cursor is still visible on it.  (It's frozen too...but I can see it on the screen).

I thought it could be a screen-saver issue but I don't think it's that either. 

Any advice?  Is there a log I could look at?

Thanks.

---

### Post by linux_tech on 2008-12-06
messages are contained in /var/log/message
```
cat /var/log/messages
```
another source of messages
```
dmesg
```

for video info-
```
sudo lshw -C video
```
```
sudo nano /etc/X11/xorg.conf
```
```
 xrandr
```

---

### Post by linux_tech on 2008-12-06
Another good command to get video any error or warning messages from xorg.conf is:
```
cat /var/log/Xorg.0.log | grep EE
```

to just see what nvidia card you have try:
```
lspci | grep -i nvidia
```


Here is a link with some good information about nvidia drivers for ubuntu
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

