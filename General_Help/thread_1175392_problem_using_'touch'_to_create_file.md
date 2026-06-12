---
title: "problem using 'touch' to create file"
date: 2009-06-01
forum: General Help
---

### Post by bawig1 on 2009-06-01
Hi,

I am trying to create a file using 'touch' but when I try to use it I get the following;

```
bawig1@bawig1-laptop:~$ sudo touch /sys/class/video4linux/video0/vflip 
``````
touch: cannot touch `vflip': No such file or directory
```I have checked the modes of the video0 dir

```
lrwxrwxrwx  1 root root 0 2009-06-01 18:51 video0 -> ../../devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/video4linux/video0

```what am I doing wrong?

thanks,

Brett.

---

### Post by sanemanmad on 2009-06-01
You cannot write to that directory (I am not too sure, however I believe that is a virtual directory)

Look at this link for a better explanation. [SYS directory]("http://linux.about.com/od/pap_howto/a/hwtpap07t06.htm")

---

### Post by sanemanmad on 2009-06-01
Try this if your not sure```
michael@Alice:~$ du -sh /sys
```

---

