---
title: "Import digital photographs in XFCE"
date: 2013-05-09
forum: Desktop Environments
---

### Post by spillz on 2013-05-09
In Settings -> Removable Drives and Media -> Camera, I check "import digital photographs when connected". I then type the name of the program I want to used in the "Command:" prompt, but is it possible to also specify the path/uri to the camera, such as: "program %uri" where %uri represent the uri to the camera? Does anyone know if there is a syntax for this?

(I am using Ubuntu 12.04 with XFCE 4.8)

---

### Post by 2F4U on 2013-05-10
Why would you want to do that? For USB devices, that path could change, for example, depending on if there are other USB devices attached.

---

### Post by spillz on 2013-05-10
> **2F4U said:**
> Why would you want to do that? For USB devices, that path could change, for example, depending on if there are other USB devices attached.

That's precisely why I want to do that, because my program doesn't necessarily know which of several attached media devices it should be importing from. On the other hand, the system knows that a camera/SD card has been plugged in and therefore it also knows the filesystem location of the photos on it, so I was expecting there would be some way to pass this info to the program.

---

### Post by spillz on 2013-05-10
So after a bit more googling I figured out that the camera command will replace "%d" with the device name, which is good enough for me. So for example:

picture-importer -d %d

will get replaced with 

picture-importer -d /dev/sdb

(The -d switch tells the program I use that this is a unix device location.)

---

