---
title: "Wireless mouse does not work and freezes the desktop"
date: 2006-01-26
forum: Desktop Environments
---

### Post by jcaceres on 2006-01-26
Hi All.
I have a problem with an wireless mouse.... :(
when i connect this mouse to the laptop, appears this message on syslog

[INDENT][I]syslog.0:Jan 26 10:33:20 localhost kernel: [4294940.082000] drivers/usb/input/hid-core.c: usb_submit_urb(ctrl) failed
[/I][/INDENT]

And This message on kern.log

[INDENT][I]Jan 26 10:53:49 localhost kernel: [4296169.599000] usb 3-1: USB disconnect, address 2
Jan 26 10:54:01 localhost kernel: [4296181.411000] usb 3-2: new low speed USB device using uhci_hcd and address 3
Jan 26 10:54:11 localhost kernel: [4296191.582000] drivers/usb/input/hid-core.c: usb_submit_urb(ctrl) failed
Jan 26 10:54:11 localhost kernel: [4296191.582000] drivers/usb/input/hid-core.c: timeout initializing reports
Jan 26 10:54:11 localhost kernel: [4296191.582000]
Jan 26 10:54:11 localhost kernel: [4296191.591000] input: USB HID v1.10 Mouse [0d62:1000] on usb-0000:00:1d.2-2[/I][/INDENT]


When that happens, i can't make any click on desktop, only in current application. I can not click on menu, can't change desktop number (ctrl+alt+shift), really, can't do anythig. My desktop freezes, and can only work on current application. The strange thing is that on 3 - 5 minutes, this behavior dessapears, an everthing becomes normal... ¿?

My wireless mouse is a kensigton..

.. Another thing ... on my laptop i have Window XP .. :(  and this mouse work fine ... ¿?

---

### Post by rjwood on 2006-01-26
I don't have the answer for you, my wireless mouse for my desktop has alway's worked fine. I suspect it is not the mouse per se but instead has to do with the usb connection. I suggest you search the forums for 'wireless' or 'mouse' or even 'usb' and have fun solving your problem, while getting an education as well. I like doing that myself as I also get a sense of the people who have posted.. Good Luck!!!

---

### Post by jcaceres on 2006-01-26
RJ,
I really thank for quick answering. But, when i don't thing that is an usb problem because with normal mouses with usb connection, ubuntu desktop works fine, and with Windows XP works fine... but the problem is that i always use ubuntu not XP...
Thanks ...

---

