---
title: "JMF autodetection not working?"
date: 2005-11-27
forum: Desktop Environments
---

### Post by Turtle.net on 2005-11-27
I had a lot of problems to install the driver for my Logitech Quickcam Messenger (see [my post on this subject]("http://www.ubuntuforums.org/showthread.php?t=53755"))
Now I can use my webcam under Gnomemeeting.
But I would like to use Mercury. I installed it without any problem, I installed also the JMF 2.1.1 from [the sun's official website]("http://java.sun.com/products/java-media/jmf/2.1.1/download.html").
And either when I try the detection using jmfregistry or jmfinit, or even the autodetection feature in Mercury (after downloading the needed files from Mercury web site) the detection begin but never end...it seems to try to do something but nothing happen (I waited 30min just to be sure).
Any idea :confused: ???

---

### Post by arnieboy on 2005-12-10
[QUOTE=Turtle.net]I had a lot of problems to install the driver for my Logitech Quickcam Messenger (see [my post on this subject]("http://www.ubuntuforums.org/showthread.php?t=53755"))
Now I can use my webcam under Gnomemeeting.
But I would like to use Mercury. I installed it without any problem, I installed also the JMF 2.1.1 from [the sun's official website]("http://java.sun.com/products/java-media/jmf/2.1.1/download.html").
And either when I try the detection using jmfregistry or jmfinit, or even the autodetection feature in Mercury (after downloading the needed files from Mercury web site) the detection begin but never end...it seems to try to do something but nothing happen (I waited 30min just to be sure).
Any idea :confused: ???[/QUOTE]
try the following howto:
[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)

---

### Post by Turtle.net on 2005-12-10
Thanks for your help but my webcam is a ```
$lsusb
Bus 004 Device 002: ID 046d:08f0 Logitech, Inc.

``` Hence it seems that I cannot use the driver you recommend.

Thanks anyway.

It seems that the JMF from Mercury can detect my webcam...but now my webcam just give up after few seconds ...
```
$dmesg
[4295843.084000] quickcam [47.488203]: USB transfer error -18
[4295843.084000] quickcam [47.488216]: qc_stream_error(qc=d5351000)
[4295843.084000] quickcam [47.488231]: Too many errors, giving up

``` 
I think that the driver I use is maybe not ready yet :(

---

