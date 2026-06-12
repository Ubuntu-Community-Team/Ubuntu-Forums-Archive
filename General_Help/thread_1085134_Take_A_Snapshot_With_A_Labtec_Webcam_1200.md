---
title: "Take A Snapshot With A Labtec Webcam 1200"
date: 2009-03-02
forum: General Help
---

### Post by xluryan on 2009-03-02
I have a 'Labtec Webcam 1200'. When I plug it in, I get this:

```

$ dmesg | tail

[1881416.180065] usb 1-8: new full speed USB device using ohci_hcd and address 7
[1881416.394347] usb 1-8: configuration #1 chosen from 1 choice
[1881416.397685] gspca: probing 093a:2464
[1881416.403169] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[1881416.403179] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2464)
[1881416.427800] gspca: probe ok

```

Looks like it found the camera... and the webcam *does* work with Ekiga! But when I try to use vgrabbj, it won't capture images; I only get a 0 length file.

Here is this:
```

$ vgrabbj -s /dev/video0

vgrabbj, Version 0.9.6
Videodevice name: /dev/video0 (CIF Single Chip     )
Capabilities
Type     : 1    Values can be looked up at videodev.h
Channels : 1
Audio    : 0
MaxWidth : 352
MaxHeight: 288
MinWidth : 48
MinHeigth: 32

Current Settings:
Brightness: 1028
Hue       : 0
Color     : 0
Contrast  : 0
Whiteness : 0
Depth     : 8
Palette   : (null) (0)
Width     : 176
Height    : 144
Chromakey : 0

```

And this:
```

$ ls -lh /dev/video0
crw-rw----+ 1 root video 81, 0 2009-03-02 17:59 /dev/video0

```

What can I do???

---

### Post by loell on 2009-03-02
i dunno if this could make a difference.

```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so vgrabbj -s /dev/video0 
```

---

### Post by xluryan on 2009-03-03
That actually did the trick. With that, my webcam is now functioning like it should with all applications (vgrabbj, motion, etc...), however, I get several warnings from the v4l1convert utility:

```

$ env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so motion

...

[1] Using V4L2
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
[1] Started stream webcam server in port 8081
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000fff6
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000fffd
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000fffb

```

And it just keeps going. Any ideas?

---

### Post by loell on 2009-03-03
I see, that's good to know. :)

 I suppose the warning messages are specific decoding errors also for some specific webcam chipsets. lets hopes things will improve in jaunty.

---

