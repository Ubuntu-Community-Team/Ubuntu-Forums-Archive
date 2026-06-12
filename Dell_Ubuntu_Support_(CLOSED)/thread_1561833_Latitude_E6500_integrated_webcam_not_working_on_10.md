---
title: "Latitude E6500 integrated webcam not working on 10.4"
date: 2010-08-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by grigglestone on 2010-08-26
Can't seem to get the Creative Labs integrated webcam working. Tried guvcview and get this:

$ guvcview
guvcview 1.1.3
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
video device: /dev/video0 
opening '/sys/class/video4linux' failed: Error opening directory '/sys/class/video4linux': No such file or directory
Unable to detect devices on your system
ERROR opening V4L interface: No such file or directory
Init video returned -1
Terminated.

also...

ls /dev/video*
ls: cannot access /dev/video*: No such file or directory

I guess this means no webcam was found.

Any thoughts? Anything else I can test?

thanks

---

