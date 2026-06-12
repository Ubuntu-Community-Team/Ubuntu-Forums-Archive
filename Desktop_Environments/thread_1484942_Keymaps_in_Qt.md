---
title: "Keymaps in Qt"
date: 2010-05-16
forum: Desktop Environments
---

### Post by Azathoth_ on 2010-05-16
Hi everybody,

I have always used LIRC up to the last Ubuntu 10.04 *Lucid Lynx* release in which my *Hauppage HVR-4000* is integrated in ir-common.ko
I tried to delete all the definitions in */usr/src/linux/drivers/media/common/ir-keymap.c* but then irw did not recognize any key and *dmesg* gave me errors "unknown key".

Finally, due to LIRC is going to be deprecated and replaced by *ir_common* and to avoid future problems in next Ubuntu releases, I decided to use ir_common features for my ir remote controller.
I am using KDE 4.4 and here all the keytables are not integrated... I mean, if I check in *ir-keypmap.c* I see the following keytable:

```
static struct ir_scancode ir_codes_hauppauge_new[] = {
	/* Keys 0 to 9 */
	{ 0x00, KEY_0 },
	{ 0x01, KEY_1 },
	{ 0x02, KEY_2 },
	{ 0x03, KEY_3 },
	{ 0x04, KEY_4 },
	{ 0x05, KEY_5 },
	{ 0x06, KEY_6 },
	{ 0x07, KEY_7 },
	{ 0x08, KEY_8 },
	{ 0x09, KEY_9 },

	{ 0x0a, KEY_TEXT },		/* keypad asterisk as well */
	{ 0x0b, KEY_RED },		/* red button */
	{ 0x0c, KEY_RADIO },
	{ 0x0d, KEY_MENU },
	{ 0x0e, KEY_SUBTITLE },		/* also the # key */
	{ 0x0f, KEY_MUTE },
	{ 0x10, KEY_VOLUMEUP },
	{ 0x11, KEY_VOLUMEDOWN },
	{ 0x12, KEY_PREVIOUS },		/* previous channel */
	{ 0x14, KEY_UP },
	{ 0x15, KEY_DOWN },
	{ 0x16, KEY_LEFT },
	{ 0x17, KEY_RIGHT },
	{ 0x18, KEY_VIDEO },		/* Videos */
	{ 0x19, KEY_AUDIO },		/* Music */
	/* 0x1a: Pictures - presume this means
	   "Multimedia Home Platform" -
	   no "PICTURES" key in input.h
	 */
	{ 0x1a, KEY_MHP },

	{ 0x1b, KEY_EPG },		/* Guide */
	{ 0x1c, KEY_TV },
	{ 0x1e, KEY_NEXTSONG },		/* skip >| */
	{ 0x1f, KEY_EXIT },		/* back/exit */
	{ 0x20, KEY_CHANNELUP },	/* channel / program + */
	{ 0x21, KEY_CHANNELDOWN },	/* channel / program - */
	{ 0x22, KEY_CHANNEL },		/* source (old black remote) */
	{ 0x24, KEY_PREVIOUSSONG },	/* replay |< */
	{ 0x25, KEY_ENTER },		/* OK */
	{ 0x26, KEY_SLEEP },		/* minimize (old black remote) */
	{ 0x29, KEY_BLUE },		/* blue key */
	{ 0x2e, KEY_GREEN },		/* green button */
	{ 0x30, KEY_PAUSE },		/* pause */
	{ 0x32, KEY_REWIND },		/* backward << */
	{ 0x34, KEY_FASTFORWARD },	/* forward >> */
	{ 0x35, KEY_PLAY },
	{ 0x36, KEY_STOP },
	{ 0x37, KEY_RECORD },		/* recording */
	{ 0x38, KEY_YELLOW },		/* yellow key */
	{ 0x3b, KEY_SELECT },		/* top right button */
	{ 0x3c, KEY_ZOOM },		/* full */
	{ 0x3d, KEY_POWER },		/* system power (green button) */
};
```

By example, *xev* and KDE recognize *KEY_PAUSE* like a "pause" key (keyboard extension) but xev and KDE does not recognize *KEY_BLUE*...
After pressing each button and running *dmesg* I can see no "unknown key" error.

**My question is if is there any way to add the above KEY_xxxx (keytables) to Qt detection, to use in Amarok, VLC, Smplayer, ...**

Thanks in advance.

---

