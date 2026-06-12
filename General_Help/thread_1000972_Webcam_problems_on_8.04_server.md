---
title: "Webcam problems on 8.04 server"
date: 2008-12-03
forum: General Help
---

### Post by SoCalChris on 2008-12-03
I've got 8.04 server running in my garage, and am trying to hook up a webcam. The webcam is recognized, and is mounted at /dev/video0. Instead of getting a good picture though, all I get is a random green image. I've searched on the forums here, but almost everything that I've found is related to changes made to the gspca driver in 8.10, I haven't found anything that helps me with 8.04.

[IMG]http://www.wilsonsinmt.com/driveway.jpg[/IMG]

The webcam is a Creative Live, lsusb gives the following description "041e:4053 Creative Technology, Ltd"

According to [this page]("http://mxhaard.free.fr/spca5xx.html"), the webcam is supported and should be using the spca5xx driver. However, according to [this page]("https://help.ubuntu.com/community/Spca5xx#Ubuntu%207.10%20(Gutsy),%20and%208.04%20(Hardy)") the driver was replaced by gspca, and should be enabled by default in 8.04. The page says to check that the driver is loaded by running lsmod. 

lsmod returns the following, so I know that the driver is loaded.
```
gspca                 643920  1
videodev               29440  3 gspca
usbcore               146028  4 gspca,usbhid,uhci_hcd

```

Any suggestions on how to get this working in 8.04?

Thanks

---

### Post by SoCalChris on 2008-12-04
Anyone?

---

### Post by SoCalChris on 2008-12-11
I've updated the computer to 8.10 server. I'm not getting the random green any more, but the picture is completely over exposed. I somewhat solved it by putting a piece of window tint in front of the lens, but there is still several hours a day where the light is too much.

---

