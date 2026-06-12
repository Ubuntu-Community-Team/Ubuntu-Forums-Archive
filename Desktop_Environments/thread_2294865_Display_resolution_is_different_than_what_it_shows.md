---
title: "Display resolution is different than what it shows"
date: 2015-09-14
forum: Desktop Environments
---

### Post by prat22 on 2015-09-14
Hello,

I am using Lubuntu 14.04.3 LTS.
Recently after installing Win 7 and grub2win, when I log in to my Linux, my display properties shows that I am using 1024 * 768, but I am sure that it is displaying a lower resolution. When I checked online through [http://www.whatismyscreenresolution.com/](http://www.whatismyscreenresolution.com/), it shows that I am using 930 * 698. 

Following are the opinion of the terminal:
```
$ xdpyinfo  | grep dimensions  dimensions:    1024x768 pixels (302x191 millimeters)



```

```
$ xrandr --currentxrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  



```

Anyone help me get back my resolution... The display looks horrible!!

---

