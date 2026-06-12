---
title: "Dynamic Window Manager Tagging"
date: 2008-09-25
forum: Desktop Environments
---

### Post by binarymutant on 2008-09-25
I've been using dwm for awhile now, but I still can't figure out how to go about tagging terminals like xterm or aterm in my config.h file. I've tried different variants like Xterm and XTerm but to no avail. I also would like to know if there is a way to tag console commands. Please help. Here's the tagging section in my config.h file for reference:

/* tagging */
static const char tags[][MAXTAGLEN] = { "Main", "Msg", "Chat", "Web", "Media" };
static unsigned int tagset[] = {1, 1}; /* after start, first tag is selected */

static Rule rules[] = {
	/* class      instance    title       tags mask     isfloating */
	{ "MPlayer",  NULL,	  NULL,	      1<<4,	    True },
	{ "feh",      NULL, 	  NULL,       1<<4,         True },
	{ "Links",    NULL,       NULL,       1<<3,         False },
	{ "Xchat",    NULL,       NULL,       1<<2,         False },
	{ "ATerm",    NULL,       NULL,       1<<1,         False },
};

---

### Post by binarymutant on 2008-09-25
nevermind, I used xprop to figure this out. Thanks to the great people at #awesome on OFTC for their help!

---

