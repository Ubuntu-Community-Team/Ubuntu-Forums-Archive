---
title: "Infrared control"
date: 2009-05-07
forum: Desktop Environments
---

### Post by Psicolonia on 2009-05-07
Hi everyone,

I'm trying to get a Kingsun IrDa device to work with ubuntu. I want to control XBMC with it. I installed lirc and gnome-lirc that has a nice interface and all but... it does not recognize my IrDa.

Here are two outputs (lsusb)
```
Bus 003 Device 002: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 07d0:4100 Dazzle Kingsun SF-620 Infrared Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

```

(dmesg | grep 'irda')
```
[    9.447062] irda_init()
[    9.541423] net irda0: IrDA: Registered KingSun/Dazzle device irda0

```

There is no /dev/irda0 on the filesystem.

Can anyone help me get this going?

---

### Post by RaZoR1394 on 2009-06-02
[http://palosanto.com/~a_villacis/codeprojects/kingsun-linux.en.html](http://palosanto.com/~a_villacis/codeprojects/kingsun-linux.en.html)

> 
#
Can I use them with LIRC, or with/as an IR remote control?

Several people have e-mailed me with this question, as well as with inquires/comments that assume LIRC support. Because of this, I will give both a short and a long answer.

The short answer is: no. These drivers cannot be used with LIRC or with remote controls.

The long answer consists of several reasons, as follows:

    * The IrDA framing is too high a level of abstraction. LIRC requires raw access to the data read from the IR source, and IrLAP (part of the IrDA specification) framing and unframing gets in the way of the raw stream of data. This is why standard USB-IrDA dongles (for which framing is performed by the dongle itself) are explicitly not supported by LIRC.
    * The IrDA physical layer uses an encoding scheme that is very different from the Consumer IR (CIR) encoding, even though both use infrared signals for communication. Many remote controls use a 38KHz sub-carrier for encoding, which is not one of the standard frequencies for IrDA. Some trickery to send and receive remote-control data with a SIR dongle can be done, but it is very timing-dependent, and depends on the ability to set a speed of 115200bps for the dongle (which only ksdazzle supports).
    * Even after reprogramming the speed, the issue of timing remains. There is no hard guarantee in the USB bus about the timing of the requests for interrupt endpoints (the ones used by ksdazzle). This means that the timing required to decode the remote-control signals has too much uncertainity to have a reliable reception.

If you think you need LIRC to communicate with your camera/cellphone/PDA, you should know that it is not required. It is enough that the device is IrDA-enabled. See this question above.


---

