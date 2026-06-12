---
title: "Mini-9 OBEX &amp; Bluetooth not fully starting?"
date: 2009-06-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dave66 on 2009-06-04
Hi,

I've come across something on Dell Mini-9's that appears to be a little odd. I want to be able to send files via bluetooth between two Dell Mini-9's and elected to use OBEX Push. I'm running Ubuntu 8.04 LTS (obex-data-server 0.3.1-0ubuntu1).

So under Bluetooth preferences I set the following:

**Mode of operation: **
Visible and connectable for other devices

**Services running: **
Input & Audio

**General: **
Receive files from remote devices & Automatically authorize incoming requests.

With that done I can use bluetooth to send/receive files between the two machines.

Now, restart the machines and try sending files using bluetooth and I can't, get an error "Device does not support Obex File Transfer"

So go to a terminal and try 

> sdptool browse local

The obex-data-server is not running (or I suspect not "fully" started)

So now kill the obex server and restart it, through terminal:

> killall obex-data-server
obex-data-server --no-daemon

I see a popup notification over the bluetooth icon in the top panel to say that receiving files is enabled.

Try sdptool browse local and there I see the obex-data-server is now running. I can now send and receive files once more.

So to my noob mind, it appears that obex-data-server does not fully start on power up, I say fully because if it wasn't running when I used killall obex-data-server I would have got "no process killed" but I don't.

I have used a script:
> #!/bin/sh
killall obex-data-server
obex-data-server --no-daemon

So I can run this script on start up, but I'm hoping there is a more experienced person out there that can offer a more elegant solution to this issue.

By the way I have tested this on 10 different Dell's and the problem is present on them all - straight out of the box.

Any suggestions for a more refined solution?

---

### Post by dave66 on 2009-06-08
So do any of the guru's out there have a suggestion on how to fix this issue so that I don't have to manually kill and then start obex-data-server every time I boot the Mini-9?

---

