---
title: "Problem with PowerTop, and webcam. How to re-enable the cam?"
date: 2009-04-24
forum: General Help
---

### Post by lapstue on 2009-04-24
Hello!

I fiddled around with powertop today, but sadly I got to greedy in my quest for alternatives to save power :( I managed to turn of my webcam, through powertop.

I'm quite new to Ubuntu, and I'm not sure what's the best way to re-enable it, I guess it's blacklisted or something..

A little info about my system:
The laptop is a Dell XPS M1530, and the webcam in question is the integrated one.
The output of "dmesg | grep cam" is:
```
[    8.377572] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[    8.378574] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input9

```
I hope I used dmesg right, I'm after all quite new to Ubuntu, but I'm loving it :)

Can anyone help me with this problem?

---

### Post by libssd on 2010-08-21
I think I have exactly the same problem, with an Acer AA1 D150. The webcam has been working for the past 15 months, using Windows XP, Ubuntu 9.04 and 10.04, and Mint 9. Today, I discovered that it isn't working (under any of those operating systems).

However, while trouble-shooting in XP, I discovered that Windows still ***detects ***the built-in webcam, which suggests to me that this is not a hardware problem.

About 2 weeks ago, I installed Powertop, and I remember at one point using the option to turn off the webcam to save power. I'm pretty sure (but not certain) that the webcam still worked after this, but discovered today that it does not.

```

$ dmesg | grep uvcvideo
[    5.169867] uvcvideo: Found UVC 1.00 device WebCam (0c45:62c0)
[    5.176712] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    5.178580] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[    5.178746] uvcvideo: Failed to initialize the device (-5).
[    5.178977] usbcore: registered new interface driver uvcvideo

```

After re-flashing the BIOS, webcam still doesn't work under any OS, so I am now leaning to a hardware problem unrelated to Powertop. Apparently webcam failures are common enough that Acer has a "Webcam not working" page on the topic: [http://netbooks-us.custhelp.com/app/answers/detail/a_id/86/~/webcam-not-working](http://netbooks-us.custhelp.com/app/answers/detail/a_id/86/~/webcam-not-working)

---

