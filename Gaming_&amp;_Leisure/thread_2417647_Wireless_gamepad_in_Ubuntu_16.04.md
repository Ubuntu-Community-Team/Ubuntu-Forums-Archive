---
title: "Wireless gamepad in Ubuntu 16.04"
date: 2019-04-25
forum: Gaming &amp; Leisure
---

### Post by peibolmeneibol on 2019-04-25
Hi! 
I have Ubuntu 16.04 on a nas Qnap ts-251.  I'm trying to use an wireless gamepad but I do not get it.  I think the problem is that it is wireless, and I am not capable of being recognized by ubuntu.  Can someone help me?  Would it be easier with a gamepad with USB cable?
A lot of thanks.

---

### Post by oldrocker99 on 2019-04-25
Do this first.```
lsusb
```

This will show every USB device. Look for an unusual name, which is likely to be the wireless adapter.

---

### Post by peibolmeneibol on 2019-04-25
> **oldrocker99 said:**
> Do this first.```
lsusb
```

This will show every USB device. Look for an unusual name, which is likely to be the wireless adapter.


OK, thank you very much, I will try as soon as I get home and comment.

---

### Post by peibolmeneibol on 2019-04-25
> **oldrocker99 said:**
> Do this first.```
lsusb
```

This will show every USB device. Look for an unusual name, which is likely to be the wireless adapter.

This is what appears:
Bus 002 Device 002: ID 1c05:3074  
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1005:b155 Apacer Technology, Inc. 
Bus 001 Device 007: ID 0603:0002 Novatek Microelectronics Corp. 
Bus 001 Device 009: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 001 Device 002: ID 1c05:2074  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and without the adapter:

Bus 002 Device 002: ID 1c05:3074  
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1005:b155 Apacer Technology, Inc. 
Bus 001 Device 007: ID 0603:0002 Novatek Microelectronics Corp. 
Bus 001 Device 002: ID 1c05:2074  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


What does it means?

---

### Post by oldrocker99 on 2019-04-25
What is missing with the adapter unplugged is this:
 Bus 001 Device 009: ID 045e:028e Microsoft Corp. Xbox360 Controller

It is seen by your system, so, although I have never used a controller in my 70 years, here's a URL that'll get you on the right track:

[https://www.unixblogger.com/how-to-get-your-xbox-360-wireless-controller-working-under-your-linux-box/](https://www.unixblogger.com/how-to-get-your-xbox-360-wireless-controller-working-under-your-linux-box/)

You can have my mouse and keyboard when you pry them from my cold, dead fingers!

BTW, Google is your friend.;)

---

### Post by peibolmeneibol on 2019-04-25
> **oldrocker99 said:**
> What is missing with the adapter unplugged is this:
 Bus 001 Device 009: ID 045e:028e Microsoft Corp. Xbox360 Controller

It is seen by your system, so, although I have never used a controller in my 70 years, here's a URL that'll get you on the right track:

[https://www.unixblogger.com/how-to-get-your-xbox-360-wireless-controller-working-under-your-linux-box/](https://www.unixblogger.com/how-to-get-your-xbox-360-wireless-controller-working-under-your-linux-box/)

You can have my mouse and keyboard when you pry them from my cold, dead fingers!

BTW, Google is your friend.;)

This error appears:
-- [ ERROR ] ------------------------------------------------------
USBController::USBController(): libusb_open() failed: LIBUSB_ERROR_NO_DEVICE

 I do not have an Xbox gamepad, it's from another brand. Before asking for help here, I was looking for information and I read that I could work on installing Xboxdrv, but it did not work for me. Could it be that it appears like this because it was installed before? Or is it really detected simply by connecting it to the usb?
many thanks

---

### Post by thenailedone on 2019-04-25
> **peibolmeneibol said:**
> Would it be easier with a gamepad with USB cable?

Much, much easier (that is not to say that your current gamepad won't work... but it could turn out to be more hassle than it is worth ](*,)).

---

### Post by peibolmeneibol on 2019-04-26
> 
-- [ ERROR ] ------------------------------------------------------
USBController::USBController(): libusb_open() failed: LIBUSB_ERROR_NO_DEVICE




I have read elsewhere that this error is because "The libusb permissions are not set for you". How are those permissions configured?

>  Much, much easier (that is not to say that your current gamepad won't work... but it could turn out to be more hassle than it is worth ).'ll try a little more with the wireless

I'll try a little more with the wireless

---

### Post by peibolmeneibol on 2019-04-30
[FONT=arial][SIZE=2]
[/SIZE][/FONT]
[FONT=arial][SIZE=2][COLOR=#212121]I changed the gamepad for a logitech f310, usb, and I still have the same problem. I have searched and searched for information, and I can not fix the problem.When I plugged in the f310 for the first time if I appeared in jstest, but not anymore.
[/COLOR][SIZE=3][SIZE=2]Does anyone know how to try to solve the problem? Thanks[/SIZE]
[/SIZE][/SIZE][/FONT]

---

