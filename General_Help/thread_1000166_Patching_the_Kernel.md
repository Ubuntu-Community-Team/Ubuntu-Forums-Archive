---
title: "Patching the Kernel"
date: 2008-12-02
forum: General Help
---

### Post by jhardingptx on 2008-12-02
I am trying to get my ATI TV Wonder 600 usb tv tuner to work under Ubuntu. I am relatively new to Ubuntu and linux in general. I have been trying to follow the instructions listed on [THIS]("http://www.linuxforums.org/forum/peripherals-hardware/131790-ati-tv-wonder-600-usb-2-0-0438-b002-linux-2-6-26-kernel.html") page but I cant seem to figure out quite what to do. In particular, I am stuck at the line that tells me to "- Use the attached patch em28xx.patch.txt to patch your 2.6.26 source and compile the kernel/modules."

Any help would be greatly appreciated.

---

### Post by cube3x3 on 2008-12-02
Use 'patch' command in command line to patch the kernel source.

use this link [http://www.cpqlinux.com/patch.html]("http://www.cpqlinux.com/patch.html") to know more about how to apply a patch.

I could open the patch file in the link because I dont have a login in that forum and I dont want to create one, so couldnt figure out that which location you have to apply the patch file.

---

### Post by jhardingptx on 2008-12-02
ahh well here is the code. i will try to figure it out on my own, but i can never say no to help.

```

diff -Nur /tmp/em28xx/em28xx-cards.c /tmp/em28xx.new/em28xx-cards.c
--- /tmp/em28xx/em28xx-cards.c	2008-07-13 17:51:29.000000000 -0400
+++ /tmp/em28xx.new/em28xx-cards.c	2008-09-29 15:24:47.000000000 -0400
@@ -151,6 +151,29 @@
 					MSP_DSP_IN_SCART, MSP_DSP_IN_SCART),
 		} },
 	},
+	[EM2880_BOARD_AMD_ATI_TV_WONDER_HD_600] = {
+		.name           = "AMD ATI TV Wonder HD 600",
+		.vchannels      = 3,
+		.tda9887_conf   = TDA9887_PRESENT,
+		.tuner_type     = TUNER_XC2028,
+		.mts_firmware   = 1,
+		.has_12mhz_i2s  = 1,
+		.has_dvb        = 1,
+		.decoder        = EM28XX_TVP5150,
+		.input          = { {
+			.type     = EM28XX_VMUX_TELEVISION,
+			.vmux     = TVP5150_COMPOSITE0,
+			.amux     = 0,
+		}, {
+			.type     = EM28XX_VMUX_COMPOSITE1,
+			.vmux     = TVP5150_COMPOSITE1,
+			.amux     = 1,
+		}, {
+			.type     = EM28XX_VMUX_SVIDEO,
+			.vmux     = TVP5150_SVIDEO,
+			.amux     = 1,
+		} },
+	},
 	[EM2880_BOARD_HAUPPAUGE_WINTV_HVR_900] = {
 		.name         = "Hauppauge WinTV HVR 900",
 		.vchannels    = 3,
@@ -429,6 +452,8 @@
 			.driver_info = EM2880_BOARD_HAUPPAUGE_WINTV_HVR_950 },
 	{ USB_DEVICE(0x2040, 0x651f), /* HCW HVR-850 */
 			.driver_info = EM2880_BOARD_HAUPPAUGE_WINTV_HVR_950 },
+	{ USB_DEVICE(0x0438, 0xb002),
+			.driver_info = EM2880_BOARD_AMD_ATI_TV_WONDER_HD_600 },
 	{ USB_DEVICE(0x0ccd, 0x0042),
 			.driver_info = EM2880_BOARD_TERRATEC_HYBRID_XS },
 	{ USB_DEVICE(0x0ccd, 0x0047),
@@ -544,6 +569,7 @@
 	case EM2880_BOARD_HAUPPAUGE_WINTV_HVR_900:
 	case EM2880_BOARD_TERRATEC_HYBRID_XS:
 	case EM2880_BOARD_HAUPPAUGE_WINTV_HVR_950:
+	case EM2880_BOARD_AMD_ATI_TV_WONDER_HD_600:
 		em28xx_write_regs(dev, EM28XX_R0F_XCLK,    "\x27", 1);
 		em28xx_write_regs(dev, EM28XX_R06_I2C_CLK, "\x40", 1);
 		msleep(50);
@@ -577,6 +603,7 @@
 		ctl->demod = XC3028_FE_ZARLINK456;
 		break;
 	case EM2880_BOARD_HAUPPAUGE_WINTV_HVR_950:
+	case EM2880_BOARD_AMD_ATI_TV_WONDER_HD_600:
 		/* FIXME: Better to specify the needed IF */
 		ctl->demod = XC3028_FE_DEFAULT;
 		break;
diff -Nur /tmp/em28xx/em28xx-dvb.c /tmp/em28xx.new/em28xx-dvb.c
--- /tmp/em28xx/em28xx-dvb.c	2008-07-13 17:51:29.000000000 -0400
+++ /tmp/em28xx.new/em28xx-dvb.c	2008-09-29 15:33:56.000000000 -0400
@@ -399,6 +399,7 @@
 	/* init frontend */
 	switch (dev->model) {
 	case EM2880_BOARD_HAUPPAUGE_WINTV_HVR_950:
+	case EM2880_BOARD_AMD_ATI_TV_WONDER_HD_600:
 		dvb->frontend = dvb_attach(lgdt330x_attach,
 					   &em2880_lgdt3303_dev,
 					   &dev->i2c_adap);
diff -Nur /tmp/em28xx/em28xx.h /tmp/em28xx.new/em28xx.h
--- /tmp/em28xx/em28xx.h	2008-07-13 17:51:29.000000000 -0400
+++ /tmp/em28xx.new/em28xx.h	2008-09-29 15:31:18.000000000 -0400
@@ -55,6 +55,7 @@
 #define EM2820_BOARD_PROLINK_PLAYTV_USB2	14
 #define EM2800_BOARD_VGEAR_POCKETTV             15
 #define EM2880_BOARD_HAUPPAUGE_WINTV_HVR_950	16
+#define EM2880_BOARD_AMD_ATI_TV_WONDER_HD_600   17
 
 /* Limits minimum and default number of buffers */
 #define EM28XX_MIN_BUF 4

```

---

### Post by cube3x3 on 2008-12-03
It seems that your patch is created from /tmp directory.

Do following:
1. First copy your em28xx directory to /tmp then put the patch file in /

2. Then goto / directory and give following command
```
patch -p0 < patchFile
```
Replace the 'patchFile' with the file-name of the patch.

This should patch the files.
To make sure check if the file em28xx-cards.c is modified or not.

---

### Post by deadowl on 2008-12-03
I wish I could install a custom kernel, I always get kernel panics after it compiles though, because I'm completely retarded when it comes to configuring it.

---

### Post by hissyfut on 2008-12-03
under the linux related part, there is a good cheat sheet
for patches, and also some information about compiling 2.6 kernels.
[http://www.freewebs.com/specfiles/help](http://www.freewebs.com/specfiles/help)

---

