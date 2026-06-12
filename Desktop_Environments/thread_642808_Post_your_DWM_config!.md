---
title: "Post your DWM config!"
date: 2007-12-17
forum: Desktop Environments
---

### Post by ~LoKe on 2007-12-17
There's a severe lack of DWM threads, so let's get one going here! I'm looking for inspiration, so let's get started. ;)

```
#include <X11/XF86keysym.h> /* makes XF86* keys work */
/* See LICENSE file for copyright and license details. */

/* appearance */
#define BARPOS			BarTop /* BarBot, BarOff */
#define BORDERPX		2
#define FONT			"-*-bitstream vera sans mono-medium-r-normal-*-10-*-*-*-*-*-*-*"
#define NORMBORDERCOLOR		"#222222"
#define NORMBGCOLOR		"#222222"
#define NORMFGCOLOR		"#cccccc"
#define SELBORDERCOLOR		"#222222"
#define SELBGCOLOR		"#222222"
#define SELFGCOLOR		"#afc81c"
#define TOPBAR			True		/* False */

/* tagging */
#define TAGS \
const char *tags[] = { "main", "media", "im", "other", NULL };
#define RULES \
static Rule rule[] = { \
	/* class:instance:title regex			tags regex	isfloating */ \
	{ "opera",					"main",		False }, \
	{ "*Bon Echo*",					"main",		False }, \
	{ "Minefield",					"main",		False }, \
	{ "Firefox-bin:.*(Bookmarks|Downloads|Add-ons)","main",		True }, \
	{ "Gimp",					"media",	True }, \
	{ "MPlayer",					"main",		True }, \
	{ "gedit",					"edit",		False }, \
	{ "pan",					"other",	False }, \
	{ "gpicview",					"media",	False }, \
	{ "xine",					"media",	True }, \
	{ "pidgin",					"im",		True }, \
};

#define LAYOUTS \
static Layout layout[] = { \
	/* symbol	function */ \
	{ "oO_",	floating }, /* first entry is default */ \
	{ "_Oo",	tile }, \
};

/* layout(s) */
#define MASTERWIDTH	500	/* master width per thousand */
#define NMASTER		1	/* clients in master area */
#define SNAP		1	/* snap pixel */ 
/* key definitions */
#define MODKEY			Mod1Mask
#define KEYS \
static Key key[] = { \
	/* modifier			key		function	argument */ \
	{ MODKEY|ShiftMask,		XK_Return,	spawn,		"exec gnome-terminal" }, \
	{ MODKEY,			XK_p,		spawn, 		"exe=`dmenu_path | dmenu` && exec $exe" }, \
	{ MODKEY,			XK_space,	spawn,		"exec screen" }, \
	{ MODKEY|ShiftMask,		XK_f,		spawn,		"exec firefox" }, \
	{ MODKEY,			XK_h,		incmasterw,	"-32" }, \
	{ MODKEY,			XK_l,		incmasterw,	"32" }, \
	{ MODKEY|ShiftMask,		XK_j,		incnmaster,	"1" }, \
	{ MODKEY|ShiftMask,		XK_k,		incnmaster,	"-1" }, \
	{ MODKEY,			XK_j,		focusclient,	"1" }, \
	{ MODKEY,			XK_k,		focusclient,	"-1" }, \
	{ MODKEY,			XK_m,		togglemax,	NULL }, \
	{ MODKEY,			XK_Return,	zoom,		NULL }, \
	{ MODKEY|ShiftMask,		XK_space,	togglefloating,	NULL }, \
	{ MODKEY|ShiftMask,		XK_c,		killclient,	NULL }, \
	{ MODKEY,			XK_0,		view,		NULL }, \
	{ MODKEY,			XK_1,		view,		"0" }, \
	{ MODKEY,			XK_2,		view,		"1" }, \
	{ MODKEY,			XK_3,		view,		"2" }, \
	{ MODKEY,			XK_4,		view,		"3" }, \
	{ MODKEY,			XK_5,		view,		"4" }, \
	{ MODKEY,			XK_6,		view,		"5" }, \
	{ MODKEY,			XK_7,		view,		"6" }, \
	{ MODKEY,			XK_8,		view,		"7" }, \
	{ MODKEY,			XK_9,		view,		"8" }, \
	{ MODKEY|ControlMask,		XK_1,		toggleview,	"0" }, \
	{ MODKEY|ControlMask,		XK_2,		toggleview,	"1" }, \
	{ MODKEY|ControlMask,		XK_3,		toggleview,	"2" }, \
	{ MODKEY|ControlMask,		XK_4,		toggleview,	"3" }, \
	{ MODKEY|ControlMask,		XK_5,		toggleview,	"4" }, \
	{ MODKEY|ControlMask,		XK_6,		toggleview,	"5" }, \
	{ MODKEY|ControlMask,		XK_7,		toggleview,	"6" }, \
	{ MODKEY|ControlMask,		XK_8,		toggleview,	"7" }, \
	{ MODKEY|ControlMask,		XK_9,		toggleview,	"8" }, \
	{ MODKEY|ShiftMask,		XK_0,		tag,		NULL }, \
	{ MODKEY|ShiftMask,		XK_1,		tag,		"0" }, \
	{ MODKEY|ShiftMask,		XK_2,		tag,		"1" }, \
	{ MODKEY|ShiftMask,		XK_3,		tag,		"2" }, \
	{ MODKEY|ShiftMask,		XK_4,		tag,		"3" }, \
	{ MODKEY|ShiftMask,		XK_5,		tag,		"4" }, \
	{ MODKEY|ShiftMask,		XK_6,		tag,		"5" }, \
	{ MODKEY|ShiftMask,		XK_7,		tag,		"6" }, \
	{ MODKEY|ShiftMask,		XK_8,		tag,		"7" }, \
	{ MODKEY|ShiftMask,		XK_9,		tag,		"8" }, \
	{ MODKEY|ControlMask|ShiftMask,	XK_1,		toggletag,	"0" }, \
	{ MODKEY|ControlMask|ShiftMask,	XK_2,		toggletag,	"1" }, \
	{ MODKEY|ControlMask|ShiftMask,	XK_3,		toggletag,	"2" }, \
	{ MODKEY|ControlMask|ShiftMask,	XK_4,		toggletag,	"3" }, \
	{ MODKEY|ControlMask|ShiftMask,	XK_5,		toggletag,	"4" }, \
	{ MODKEY|ControlMask|ShiftMask,	XK_6,		toggletag,	"5" }, \
	{ MODKEY|ControlMask|ShiftMask,	XK_7,		toggletag,	"6" }, \
	{ MODKEY|ControlMask|ShiftMask,	XK_8,		toggletag,	"7" }, \
	{ MODKEY|ControlMask|ShiftMask,	XK_9,		toggletag,	"8" }, \
	{ MODKEY|ShiftMask,		XK_q,		quit,		NULL }, \
};
```

**Results**
[http://icedloki.deviantart.com/art/Desktop-as-seen-on-12-16-07-72279727](http://icedloki.deviantart.com/art/Desktop-as-seen-on-12-16-07-72279727)
[http://icedloki.deviantart.com/art/Desktop-as-seen-on-12-08-07-71681502](http://icedloki.deviantart.com/art/Desktop-as-seen-on-12-08-07-71681502)

---

### Post by Dimitriid on 2007-12-17
What's your panel called?

---

### Post by ~LoKe on 2007-12-17
> **Dimitriid said:**
> What's your panel called?

It's not really a panel, basically one big status bar built into DWM.

---

### Post by Dimitriid on 2007-12-17
Neat. Im looking into something similar for openbox, right now I go panel-less.

---

### Post by fuscia on 2007-12-17
i don't know how long a 'novice asking stupid questions' like me could use dwm, but it's kind of fun to play with. it's definitely a nice change  from the usual. i like dmenu a lot. that might be worth using dwm, by itself.

---

### Post by Onyros on 2007-12-17
Hmmm... dmenu is looking good, indeed. I'll have to try it out.

I'm not using DWM per se, but [something]("http://awesome.naquadah.org/") based on it. And I now have a nifty lil'status bar always visible, replacing Conky.

[[IMG]http://img258.imageshack.us/img258/4092/awesomebg9.th.jpg[/IMG]](http://img258.imageshack.us/my.php?image=awesomebg9.jpg)

---

### Post by forrestcupp on 2007-12-17
Wow! [DWM = Vista's window manager](http://en.wikipedia.org/wiki/Desktop_Window_Manager).

What a bunch of traitors.

---

### Post by hanzomon4 on 2007-12-17
You have to recompile DWM to change it's config right?

---

### Post by hanzomon4 on 2007-12-17
~Loke, Your config.h won't compile

---

### Post by ~LoKe on 2007-12-17
> **hanzomon4 said:**
> ~Loke, Your config.h won't compile

What error are you getting?

**EDIT**: I thought I may have screwed something up when cleaning it up, but it still works for me.

---

### Post by hanzomon4 on 2007-12-17
This is what I'm getting ```
cleaning
dwm build options:
CFLAGS   = -Os -I. -I/usr/include -I/usr/X11R6/include -DVERSION="4.7"
LDFLAGS  = -s -L/usr/lib -lc -L/usr/X11R6/lib -lX11
CC       = cc
CC dwm.c
dwm.c:238: error: &#8216;tags&#8217; undeclared here (not in a function)
dwm.c: In function &#8216;applyrules&#8217;:
dwm.c:254: error: &#8216;rules&#8217; undeclared (first use in this function)
dwm.c:254: error: (Each undeclared identifier is reported only once
dwm.c:254: error: for each function it appears in.)
dwm.c:269: error: &#8216;seltags&#8217; undeclared (first use in this function)
dwm.c: In function &#8216;compileregs&#8217;:
dwm.c:409: error: &#8216;rules&#8217; undeclared (first use in this function)
dwm.c: In function &#8216;drawbar&#8217;:
dwm.c:541: error: &#8216;seltags&#8217; undeclared (first use in this function)
dwm.c: In function &#8216;grabkeys&#8217;:
dwm.c:859: error: &#8216;keys&#8217; undeclared (first use in this function)
dwm.c: In function &#8216;isvisible&#8217;:
dwm.c:952: error: &#8216;seltags&#8217; undeclared (first use in this function)
dwm.c: In function &#8216;keypress&#8217;:
dwm.c:965: error: &#8216;keys&#8217; undeclared (first use in this function)
dwm.c: In function &#8216;manage&#8217;:
dwm.c:1011: error: &#8216;seltags&#8217; undeclared (first use in this function)
dwm.c: In function &#8216;setlayout&#8217;:
dwm.c:1396: error: &#8216;layouts&#8217; undeclared (first use in this function)
dwm.c: In function &#8216;setmwfact&#8217;:
dwm.c:1421: error: &#8216;MWFACT&#8217; undeclared (first use in this function)
dwm.c: In function &#8216;setup&#8217;:
dwm.c:1484: error: &#8216;seltags&#8217; undeclared (first use in this function)
dwm.c:1498: error: &#8216;MWFACT&#8217; undeclared (first use in this function)
dwm.c:1499: error: &#8216;layouts&#8217; undeclared (first use in this function)
dwm.c: In function &#8216;tile&#8217;:
dwm.c:1616: error: &#8216;RESIZEHINTS&#8217; undeclared (first use in this function)
dwm.c: In function &#8216;toggleview&#8217;:
dwm.c:1692: error: &#8216;seltags&#8217; undeclared (first use in this function)
dwm.c: In function &#8216;view&#8217;:
dwm.c:1859: error: &#8216;seltags&#8217; undeclared (first use in this function)
dwm.c: In function &#8216;viewprevtag&#8217;:
dwm.c:1870: error: &#8216;seltags&#8217; undeclared (first use in this function)
make: *** [dwm.o] Error 1

```

---

### Post by fuscia on 2007-12-17
loke, do you mind letting this thread branch out into a general dwm thread? or, should a seperate one be started? up to you.

---

### Post by hanzomon4 on 2007-12-17
Sorry...

---

### Post by ~LoKe on 2007-12-17
> **fuscia said:**
> loke, do you mind letting this thread branch out into a general dwm thread? or, should a seperate one be started? up to you.

Doesn't matter to me, as long as it's about DWM!

---

### Post by fuscia on 2007-12-17
> **~LoKe said:**
> Doesn't matter to me, as long as it's about DWM!

absolutely! i'm hooked.

---

### Post by ~LoKe on 2007-12-18
Anyone else?

---

### Post by fuscia on 2007-12-18
i found this nice little page (it's where i found out about dmenu. how could i ever go back to other menues?) - [http://www.xsnake.net/howto/dwm/dwm-eng.php](http://www.xsnake.net/howto/dwm/dwm-eng.php)
he says "As we can see, there is nothing difficult in installing dwm on your linux distribution, and there is no reason for it to be only for "elitists"."

---

### Post by shearn89 on 2007-12-18
i installed *awesome* yesterday thanks to a shot from Loke. Its cool - all the different keybindings in the config file need to be read through and cleaned up a bit. I'll probs back up the file and then strip it, adding keybindings as i decide that i need them. Plus, its weird getting used to using the magic button instead of alt for bindings - all my OB ones are Alt+this or that...

Definitely some potential for power-user bliss!

edit: it also just occurred to me how little i actually use the right-click menu in OB. I think its mostly just for setting my wallpaper...

---

### Post by ~LoKe on 2007-12-18
> **fuscia said:**
> i found this nice little page (it's where i found out about dmenu. how could i ever go back to other menues?) - [http://www.xsnake.net/howto/dwm/dwm-eng.php](http://www.xsnake.net/howto/dwm/dwm-eng.php)
he says "As we can see, there is nothing difficult in installing dwm on your linux distribution, and there is no reason for it to be only for "elitists"."

Haha, that guy's using my conky config. :D

---

### Post by Mateo on 2007-12-18
Well, I guess I don't belong here since I use wmii, not dwm.  Anyways, they are similar and both are great. I just found dwm a bit more difficult to use.

So, to keep discussion on dwm, does it do tagging?  I know that dwm starts out with like 10 workspaces, are these just stand-ins until you start to make your own tags?

---

### Post by Onyros on 2007-12-18
> **shearn89 said:**
> i installed *awesome* yesterday thanks to a shot from Loke. Its cool - all the different keybindings in the config file need to be read through and cleaned up a bit. I'll probs back up the file and then strip it, adding keybindings as i decide that i need them. Plus, its weird getting used to using the magic button instead of alt for bindings - all my OB ones are Alt+this or that...

Definitely some potential for power-user bliss!

edit: it also just occurred to me how little i actually use the right-click menu in OB. I think its mostly just for setting my wallpaper...You can easily change all the keybindings from Mod4 (usually know as Windows key, or whatever) to Mod1 (Alt). I did it because... my laptop doesn't have a Windows key and all.

---

### Post by hanzomon4 on 2007-12-18
~Loke, where did you get that dwm wallpaper?

---

### Post by phrostbyte on 2007-12-18
dwm, wmii and other tiling window managers sound very useful if you have a really big monitor. I hope one day to have one. :)

---

### Post by Mateo on 2007-12-18
i'm only using a 17" here.  but yeah, the bigger the monitor the better for tiling WMs.

---

### Post by phrostbyte on 2007-12-18
> **Mateo said:**
> i'm only using a 17" here.  but yeah, the bigger the monitor the better for tiling WMs.

Yes I have a 12" monitor (laptop), so tiling wms end up being used pretty much the same way as every other WM, maxed windows and a pager/taskbar. But if I had a 23 or 26 incher I'd likely split it down 3 way, half for my main stuff, and 1/4 and 1/4 for my documentation and other stuff for coding. :) Sounds really useful though.

---

### Post by Onyros on 2007-12-18
I'm also using a 12" laptop ( @ 1024 x 768 ) and still find it very useful. Maybe something to do with the fact that I mainly use size=7 for my fonts, too.

But I use a mix of floating + max + tiled windows, assigning apps to different tags, so that the starting 9 tags I had are now almost always completely full.

I use tag 1 for IM's and sporadic apps I open with floating windows; tag 2 with floating windows as well, for apps that are always open, but do not require max windows (file manager - PCManFM -, Osmo Organizer and XMMS); tag 3 for Opera or Kazehakase, whichever I'm in the mood for (max window); tag 4 for Claws-Mail (max); tag 5 for Liferea (max); tag 6, 7 and 8 mostly for CLI apps (mutt - for my text only email account -, alsamixer, cplay - when I'm not in an XMMS mood - urxvt's, nano, etc).

The thing is, as we can change layouts on the fly, whenever we feel like we can just tile the windows, or float them all... It makes for a great environment, especially when we are multitasking and need windows side by side without overlapping. The only thing I have occupying space in my config is a 7 px bar at the top, so it is also a great environment for small screens.

---

### Post by Mateo on 2007-12-18
can do you do multi-tags in dwm?

---

### Post by ~LoKe on 2007-12-18
> **hanzomon4 said:**
> ~Loke, where did you get that dwm wallpaper?
Here we are:

[Text](http://phraok.free.fr/config/dwm/dwm.wall.by.PhrAok.png).

---

### Post by aktiwers on 2007-12-18
Looks very nice! Love the screenshots here.
I will try this out when I have more time for sure! Thanks :)

---

### Post by init1 on 2007-12-18
I've always used the binary in the Debian packages, so I've never customized it. It's a nice WM though.

---

### Post by ~LoKe on 2007-12-18
> **init1 said:**
> I've always used the binary in the Debian packages, so I've never customized it. It's a nice WM though.

I couldn't imagine using the package in the repositories, kind of defeats the purpose of DWM.

---

### Post by Mateo on 2007-12-18
*cough* wmii can be customized without recompiling *cough* ;)

---

### Post by ~LoKe on 2007-12-18
> **Mateo said:**
> *cough* wmii can be customized without recompiling *cough* ;)

But where's the fun in that?

---

### Post by init1 on 2007-12-18
> **~LoKe said:**
> I couldn't imagine using the package in the repositories, kind of defeats the purpose of DWM.
Well to me the purpose of DWM was to be a light and organized WM, but that's just me ;)

---

### Post by fuscia on 2007-12-18
it's really not that hard to recompile it. i tried awesome and wmii, today, but i think i'll be sticking with dwm.

---

### Post by Mateo on 2007-12-19
but if you makes changes, after recompiling don't you have to log-out of dwm and log back in?  that's the one incovenience i can think of.

---

### Post by fuscia on 2007-12-19
> **Mateo said:**
> but if you makes changes, after recompiling don't you have to log-out of dwm and log back in?  that's the one incovenience i can think of.

if you're not using a display manager, it's just alt+shift+q, up arrow and enter. takes 2 seconds.

---

### Post by grte on 2007-12-19
```
/* See LICENSE file for copyright and license details. */

/* Makes XF86* keys work */
#include <X11/XF86keysym.h>

/* appearance */
#define BARPOS			BarTop /* BarBot, BarOff */
#define BORDERPX		1
#define FONT			"-*-dejavu sans-medium-r-normal-*-10-*-*-*-*-*-*-*"
#define NORMBORDERCOLOR		"#cccccc"
#define NORMBGCOLOR		"#000000"
#define NORMFGCOLOR		"#ffffff"
#define SELBORDERCOLOR		"#abba91"
#define SELBGCOLOR		"#333333"
#define SELFGCOLOR		"#ffffff"
#define BOTTOM_MARGIN_HEIGHT	16

/* tagging */
const char tags[][MAXTAGLEN] = { "home", "tmp", "media", "p2p" };
Bool seltags[LENGTH(tags)] = {[0] = True};
Rule rules[] = {
	/* class:instance:title regex	tags regex	isfloating */
	{ "nicotine",			"p2p",		False},
	{ "feh",			"media",	True },
	{ "Gimp",			"media",	True },
	{ "MPlayer",			"media",	True },
	{ "Conky",			NULL,		True },
};

/* layout(s) */
#define MWFACT			0.7	/* master width factor [0.1 .. 0.9] */
#define RESIZEHINTS		False	/* False - respect size hints in tiled resizals */
#define SNAP			32	/* snap pixel */
Layout layouts[] = {
	/* symbol		function */
	{ "=[t]",		tile }, /* first entry is default */
	{ "=[f]",		floating },
};

/* key definitions */
#define MODKEY			Mod1Mask
#define SUPERKEY		Mod4Mask
Key keys[] = {
	/* modifier			key				function	argument */
	{ 0,                       	XK_Menu,           		spawn,		
                 									"exe=`dmenu_path | dmenu -fn '"FONT"' -nb '"NORMBGCOLOR"' -nf '"NORMFGCOLOR"'"
                 									" -sb '"SELBGCOLOR"' -sf '"SELFGCOLOR"'` && exec $exe" },
	{ ControlMask|ShiftMask,	XK_a,				spawn, 		"exec urxvtc" },
	{ 0,				XF86XK_WWW,			spawn, 		"dbus-launch firefox" },
	{ 0,				XF86XK_Search,			spawn, 		"dbus-launch firefox http://www.google.ca" },
	{ 0,				XF86XK_Mail,			spawn, 		"urxvtc -e mutt -F $HOME/.config/mutt/muttrc" },
	{ 0,				XF86XK_AudioMute,		spawn,  	"exec mpc random" },
	{ 0,				XF86XK_AudioLowerVolume,	spawn, 		"exec amixer set PCM 4-%" },
	{ 0,				XF86XK_AudioRaiseVolume,	spawn, 		"exec amixer set PCM 4+%" },
	{ 0,				XF86XK_AudioPlay,		spawn, 		"exec mpc toggle" },
	{ 0,				XF86XK_Calculator,		spawn, 		"dbus-launch qalculate-gtk" },
	{ 0,				XF86XK_Back,			spawn, 		"exec mpc prev" },
	{ 0,				XF86XK_Forward,			spawn,	 	"exec mpc next" },
	{ MODKEY,			XK_space,			setlayout,	NULL },
	{ MODKEY,			XK_b,				togglebar,	NULL },
	{ MODKEY,			XK_j,				focusnext,	NULL },
	{ MODKEY,			XK_k,				focusprev,	NULL },
	{ MODKEY,			XK_h,				setmwfact,	"-0.05" },
	{ MODKEY,			XK_l,				setmwfact,	"+0.05" },
	{ MODKEY,			XK_m,				togglemax,	NULL },
	{ MODKEY,			XK_Return,			zoom,		NULL },
	{ MODKEY,			XK_Tab,				viewprevtag,	NULL },
	{ MODKEY|ShiftMask,		XK_space,			togglefloating,	NULL },
	{ MODKEY|ShiftMask,		XK_c,				killclient,	NULL },
	{ MODKEY,			XK_0,				view,		NULL },
	{ SUPERKEY,			XK_z,				view,		tags[0] },
	{ SUPERKEY,			XK_x,				view,		tags[1] },
	{ SUPERKEY,			XK_c,				view,		tags[2] },
	{ SUPERKEY,			XK_v,				view,		tags[3] },
	{ MODKEY|ControlMask,		XK_1,				toggleview,	tags[0] },
	{ MODKEY|ControlMask,		XK_2,				toggleview,	tags[1] },
	{ MODKEY|ControlMask,		XK_3,				toggleview,	tags[2] },
	{ MODKEY|ControlMask,		XK_4,				toggleview,	tags[3] },
	{ MODKEY|ShiftMask,		XK_0,				tag,		NULL },
	{ MODKEY|ShiftMask,		XK_1,				tag,		tags[0] },
	{ MODKEY|ShiftMask,		XK_2,				tag,		tags[1] },
	{ MODKEY|ShiftMask,		XK_3,				tag,		tags[2] },
	{ MODKEY|ShiftMask,		XK_4,				tag,		tags[3] },
	{ MODKEY|ControlMask|ShiftMask,	XK_1,				toggletag,	tags[0] },
	{ MODKEY|ControlMask|ShiftMask,	XK_2,				toggletag,	tags[1] },
	{ MODKEY|ControlMask|ShiftMask,	XK_3,				toggletag,	tags[2] },
	{ MODKEY|ControlMask|ShiftMask,	XK_4,				toggletag,	tags[3] },
	{ MODKEY|ShiftMask,		XK_q,				quit,		NULL },
};

```

Results in: [http://i19.tinypic.com/73neefa.png]("http://i19.tinypic.com/73neefa.png")

---

### Post by Mateo on 2007-12-19
> **fuscia said:**
> if you're not using a display manager, it's just alt+shift+q, up arrow and enter. takes 2 seconds.

but you have to close all the applications you're working on.

---

### Post by hanzomon4 on 2007-12-19
Thanks ~Loke, this freak'in Rocks!!!

Now I need some cool CLI app replacements.


1.Chat, IM, irc app:
2.Email app:
3.Music app: Mpd?

Any tips?

I know for video I can use mplayer, and for images I can use feh. I don't really need a file browser...

---

### Post by fwojciec on 2007-12-19
> **fuscia said:**
> if you're not using a display manager, it's just alt+shift+q, up arrow and enter. takes 2 seconds.

If all you do with dwm is change the configs then, indeed, it is not a problem :p
If, however, you're actually doing work and you have apps opened on all nine tags logging out gets slightly problematic...  Especially if all you're trying to do is change a single keybinding...

I'd definitely recommend awesome over dwm from the standpoint of features and convenience...  Or xmonad if you want a really full featured tiling wm that's extremely configurable.

---

### Post by ~LoKe on 2007-12-19
> **fwojciec said:**
> If all you do with dwm is change the configs then, indeed, it is not a problem :p
If, however, you're actually doing work and you have apps opened on all nine tags logging out gets slightly problematic...  Especially if all you're trying to do is change a single keybinding...

If you're doing such a large amount of work, you won't be worried about a "single key binding"...;)

---

### Post by fwojciec on 2007-12-19
> **~LoKe said:**
> If you're doing such a large amount of work, you won't be worried about a "single key binding"...;)

I guess my example was a bit extreme but trust me, it's very useful in the long run -- I've tried it both ways ans I know what I prefer.

Also, I noticed that you use a multi screen setup -- awesome, especially the latest version, is definitely an improvement over dwm in that regard in my experience.  You can have separate bars for each screen each displaying different info, you can have per tag and per screen custom settings defined in the config file etc.  You should try it out sometime ;)

Here's what my setup looks like in case you're interested:
Clean:
[[img]http://www.loka.pl/outgoing/dec_clean_screen-thumb.jpg[/img]](http://www.loka.pl/outgoing/dec_clean_screen.jpg)
Busy:
[[img]http://www.loka.pl/outgoing/dec_busy_screen-thumb.png[/img]](http://www.loka.pl/outgoing/dec_busy_screen.png)

---

### Post by ~LoKe on 2007-12-19
> **fwojciec said:**
> Also, I noticed that you use a multi screen setup -- awesome, especially the latest version, is definitely an improvement over dwm in that regard in my experience.  You can have separate bars for each screen each displaying different info, you can have per tag and per screen custom settings defined in the config file etc.  You should try it out sometime ;)

Interesting concept; I might have to try that out. ;)

---

### Post by ~LoKe on 2007-12-19
Not bad...now I get to configure it all over again. =D

---

### Post by ~LoKe on 2007-12-19
I like it!  Which font do you use?

        font = "fixed-10"

I changed it from 12 to 10 and nothing is different after reloading.  It's much too large.

---

### Post by Onyros on 2007-12-19
> **Mateo said:**
> but you have to close all the applications you're working on.That's where Awesome shines: you can customize everything - Mod4 + Control + R - and it reloads your config. Takes 1 second :)

edit:
I jumped the gun, fwojciec had beaten me to it.

Here's my latest Awesome errmmm... "desktop"? (Clean as a whistle)

[[IMG]http://img515.imageshack.us/img515/8530/awesomeisawesomerv7.th.jpg[/IMG]](http://img515.imageshack.us/my.php?image=awesomeisawesomerv7.jpg)

@ fwojciec - Is that stalonetray at the top right of your screen?

---

### Post by fwojciec on 2007-12-19
Fixed, I think, comes only in one size since it is a bitmap font.  You should be able to use regular ttf fonts (i.e. sans-8 or mono-8 ) which are scaled so you can adjust the size more easily.  I prefer the look of bitmap fonts though...

The font I use for awesome is called terminus ([link]("http://www.is-vn.bg/hamster/jimmy-en.html")) - on arch there is a package in the repos that provides it; you should be able to find it in ubuntu or debian repos as well I imagine.  It's a bitmap font, but comes in multiple sizes.  Another good one is dina ([link]("http://www.donationcoder.com/Forums/bb/index.php?topic=7857.0")) - this is what I use in in terminal...

---

### Post by shearn89 on 2007-12-19
> **hanzomon4 said:**
> Thanks ~Loke, this freak'in Rocks!!!

Now I need some cool CLI app replacements.


1.Chat, IM, irc app:
2.Email app:
3.Music app: Mpd?

Any tips?

I know for video I can use mplayer, and for images I can use feh. I don't really need a file browser...

1. Chat - either CenterICQ (not in repos, try google), or irssi for irc.
2. Not sure - mutt?
3. mpd + ncmpc or mpc. mpc for quick changes, ncmpc for an always-open-player.

---

### Post by hanzomon4 on 2007-12-19
I tried the forked CenterICQ, CenterIM but I can't find any documentation for either of them. I set up mpd+ncmpc and irssi. Um mutt, I may leave text mode email alone for now. This is so neat..

---

### Post by fwojciec on 2007-12-19
> **Onyros said:**
> @ fwojciec - Is that stalonetray at the top right of your screen?

It's trayer, this is how I run it:
> trayer --margin 1 --edge top  --align right --padding 10 --width 10 --height 30 --transparent true --alpha 100  --tint 1 --SetDockType false --SetPartialStrut false &
I also have awesome configured to send it to tag 9 (float) on screen 1 automatically... The integration is not perfect but it works.

---

### Post by Onyros on 2007-12-19
> **fwojciec said:**
> It's trayer, this is how I run it:

I also have awesome configured to send it to tag 9 (float) on screen 1 automatically... The integration is not perfect but it works.Ah, nice :) I use a transparent stalonetray in tag 1, also floating. I can't seem to make it sticky.

But from what I could gather from the awesome mailing list, we'll soon be able to ditch these trayers... ;)

That and... I'm itching for the tab support.

---

### Post by ~LoKe on 2007-12-19
This is...awesome!! Haha. ;)

I'm trying to get a clock in the status bar, but don't know how to do it.  It was easy in dwm, but not sure where to begin here.  Also...assuming I do figure it out...how do I get it to show up in only one status bar, and not both?

---

### Post by ~LoKe on 2007-12-19
Got it.  Neat.

---

### Post by Onyros on 2007-12-19
> **~LoKe said:**
> This is...awesome!! Haha. ;)

I'm trying to get a clock in the status bar, but don't know how to do it.  It was easy in dwm, but not sure where to begin here.  Also...assuming I do figure it out...how do I get it to show up in only one status bar, and not both?This is an awesome_setup script I configured to use with the awesome client, based on an original script composed by Nikos Ntarmos from the Awesome mailing list.

I shaved a few things I didn't want displayed (load avg and the CPU load which wasn't displaying accurately), and added the RAM used / total RAM display + the battery percentage indicator and status.

```
#!/bin/bash
PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin

delim=" | ";

print_status_info() {
	freq=`awk '/cpu MHz/{print int($4)}' < /proc/cpuinfo`;

	memtotal=`awk '/MemTotal/{print $2}' < /proc/meminfo`;
	memcached=`sed 4q /proc/meminfo | awk '/Cached/{print $2}'`;
	membuffers=`awk '/Buffers/{print $2}' < /proc/meminfo`;
	memory=$(( $memtotal/1024 ));
	memfree=`awk '/MemFree/{print $2}' < /proc/meminfo`;
	memfreez=$(( ($memtotal-$memfree) ));
	freemem=$(( ($memfreez-$membuffers-$memcached)/1024 ));

	battotal=`awk '/last full capacity/{print $4}' < /proc/acpi/battery/BAT0/info`;
	batfree=`awk '/remaining capacity/{print $3}' < /proc/acpi/battery/BAT0/state`;
	battper=$(( 100*$batfree/$battotal ));
	battery=`awk '/charging state/{print $3}' < /proc/acpi/battery/BAT0/state`;
	ctime=`date '+%a, %d %b %H:%M'`;

	/bin/echo "0 setstatustext CPU: ${freq}MHz${delim}$freemem MiB / $memory MiB${delim}Bat: ${battper}% $battery${delim}$ctime";
	if [ "x$XINERAMA" = "xYES" ]; then
	/bin/echo "1 setstatustext CPU: ${freq}MHz${delim}$freemem MiB / $memory MiB${delim}Bat: ${battper}% $battery${delim}$ctime";
	fi
}

while true; do
	print_status_info | /usr/local/bin/awesome-client
	sleep 5;
done
```

Just save it as awesome_status or something, make it executable, put it in your /usr/local/bin and add it to your startup script (if you have one).

---

### Post by fwojciec on 2007-12-20
Cool stuff Onyros - somehow I must have missed on the awesome ML.  What I use is so very crude in comparison ;)

We're very off topic now, by the way, so I'll shut up and somebody better post some dwm configs...  Or maybe LoKe can somehow rename the thread to "Post your dwm/awesome config!", to legitimate our activity here ;)

---

### Post by ~LoKe on 2007-12-20
> **fwojciec said:**
> Cool stuff Onyros - somehow I must have missed on the awesome ML.  What I use is so very crude in comparison ;)

We're very off topic now, by the way, so I'll shut up and somebody better post some dwm configs...  Or maybe LoKe can somehow rename the thread to "Post your dwm/awesome config!", to legitimate our activity here ;)

Too late to edit the title. :(

---

### Post by BobCFC on 2007-12-20
As someone said earlier AWM (awesome window manager) is really worth a look if you have dual screens

I have it setup on Twinview  so it spans both my monitors, even with different resolutions..   1680x1050  and 1280x1024

I use the left one as one big pannel for the web and the right screen split up in to many xterms.  

dmenu still works with AWM too.


EDIT:  also you can edit the .awesomerc file on the fly and press  win+r  to reload new settings.   Not only do you not have to recompile you can do it while it's still running.

---

### Post by ~LoKe on 2007-12-20
Yep.  It's definitely awesome, but the only reason I'm using awesome instead of DWM is because of the two status bars.  I'm in love, it's exactly what I've been looking for for a while now.

---

### Post by Mateo on 2007-12-20
> **hanzomon4 said:**
> Thanks ~Loke, this freak'in Rocks!!!

Now I need some cool CLI app replacements.


1.Chat, IM, irc app:
2.Email app:
3.Music app: Mpd?

Any tips?

I know for video I can use mplayer, and for images I can use feh. I don't really need a file browser...

mpd is a very good choice for a music app.  Use ncmpc as the frontend.  Cmus is also quite good, but it doesn't run on a daemon like mpd, that's the one downside.

---

### Post by Mateo on 2007-12-20
> **Onyros said:**
> That's where Awesome shines: you can customize everything - Mod4 + Control + R - and it reloads your config. Takes 1 second :)

edit:
I jumped the gun, fwojciec had beaten me to it.

Here's my latest Awesome errmmm... "desktop"? (Clean as a whistle)

[[IMG]http://img515.imageshack.us/img515/8530/awesomeisawesomerv7.th.jpg[/IMG]](http://img515.imageshack.us/my.php?image=awesomeisawesomerv7.jpg)

@ fwojciec - Is that stalonetray at the top right of your screen?

what are the advantages of awesome over wmii then?

---

### Post by grte on 2007-12-21
By the way, for updating dwm after a recompile, have you guys tried pkill dwm instead of restarting X?

---

### Post by BobCFC on 2007-12-22
> **Mateo said:**
> what are the advantages of awesome over wmii then?



Multihead support...  I run it across two monitors on TwinView


Transparency using composite rendering

---

### Post by fuscia on 2007-12-23
i'm hooked on wmii, now. i actually bothered to read the user guide (a rarety for me) and i'm enjoying all the things it can do. being an essentially superficial person (or maybe i should say "easily dazzled by a pretty face"), i liked its default look from the start. i even tried coming up with a fluxbox theme to look like it. it didn't really look right, though (like putting a blond wig on a donkey).

---

### Post by shearn89 on 2007-12-24
> **fuscia said:**
> like putting a blond wig on a donkey

ROFL(copter)

I'm getting a weird problem with my awesomerc - when i add a keybinding to launch opera, the keybindings to switch tags stop working... v. strange.

---

### Post by K.Mandla on 2007-12-25
In hopes of better organizing all the window manager and desktop environment threads, this has been shifted to Desktop Environments.

---

### Post by ~LoKe on 2007-12-25
Thanks, K.Mandla!

---

### Post by InfinityCircuit on 2007-12-26
On the second page, there was a compilation error that apparently got fixed by the poster.  I'm getting the same error:

```
dwm build options:
CFLAGS   = -Os -I. -I/usr/include -I/usr/X11R6/include -DVERSION="4.8"
LDFLAGS  = -s -L/usr/lib -lc -L/usr/X11R6/lib -lX11 -lXinerama
CC       = cc
CC dwm.c
dwm.c:44:37: error: X11/extensions/Xinerama.h: No such file or directory
dwm.c: In function 'applyrules':
dwm.c:271: error: 'rules' undeclared (first use in this function)
dwm.c:271: error: (Each undeclared identifier is reported only once
dwm.c:271: error: for each function it appears in.)
dwm.c:279: error: 'tags' undeclared (first use in this function)
dwm.c:291: error: 'initags' undeclared (first use in this function)
dwm.c: In function 'buttonpress':
dwm.c:343: error: 'tags' undeclared (first use in this function)
dwm.c: In function 'compileregs':
dwm.c:440: error: 'rules' undeclared (first use in this function)
dwm.c: In function 'drawbar':
dwm.c:573: error: 'tags' undeclared (first use in this function)
dwm.c: In function 'grabkeys':
dwm.c:914: error: 'keys' undeclared (first use in this function)
dwm.c: In function 'idxoftag':
dwm.c:932: error: 'tags' undeclared (first use in this function)
dwm.c: In function 'isvisible':
dwm.c:1007: error: 'tags' undeclared (first use in this function)
dwm.c: In function 'keypress':
dwm.c:1021: error: 'keys' undeclared (first use in this function)
dwm.c: In function 'manage':
dwm.c:1058: error: 'initags' undeclared (first use in this function)
dwm.c: In function 'movemouse':
dwm.c:1173: error: 'initags' undeclared (first use in this function)
dwm.c: In function 'reapply':
dwm.c:1220: error: 'tags' undeclared (first use in this function)
dwm.c: In function 'setlayout':
dwm.c:1474: error: 'layouts' undeclared (first use in this function)
dwm.c: In function 'setmwfact':
dwm.c:1501: error: 'MWFACT' undeclared (first use in this function)
dwm.c: In function 'setup':
dwm.c:1520: error: 'XineramaScreenInfo' undeclared (first use in this function)
dwm.c:1520: error: 'info' undeclared (first use in this function)
dwm.c:1562: error: 'initags' undeclared (first use in this function)
dwm.c:1579: error: 'MWFACT' undeclared (first use in this function)
dwm.c:1580: error: 'layouts' undeclared (first use in this function)
dwm.c: In function 'tag':
dwm.c:1655: error: 'tags' undeclared (first use in this function)
dwm.c: In function 'tile':
dwm.c:1715: error: 'RESIZEHINTS' undeclared (first use in this function)
dwm.c: In function 'toggletag':
dwm.c:1754: error: 'tags' undeclared (first use in this function)
dwm.c: In function 'toggleview':
dwm.c:1768: error: 'tags' undeclared (first use in this function)
dwm.c: In function 'view':
dwm.c:1936: error: 'initags' undeclared (first use in this function)
dwm.c:1937: error: 'tags' undeclared (first use in this function)
dwm.c: In function 'viewprevtag':
dwm.c:1945: error: 'tags' undeclared (first use in this function)
dwm.c:1949: error: 'initags' undeclared (first use in this function)
dwm.c: In function 'movetomonitor':
dwm.c:2000: error: 'initags' undeclared (first use in this function)
make: *** [dwm.o] Error 1

```

How can I fix this?

EDIT: I now see libxinerama-dev was not pulled in with apt-get build-depends, so that fixes the first error, but it still fails to compile.

---

### Post by mali2297 on 2007-12-27
dmenu is a fun tool. Here is a simple script for a run dialog with saved history.

```

#!/bin/bash

font="-misc-fixed-medium-r-semicondensed--13-120-75-75-c-60-iso8859-1"
prompt="Run: "
nbcol="#000000"
nfcol="#ffffff"
sbcol="#ffffff"
sfcol="#000000"
histfile="$HOME/.dmenu.history"
maxlines=100

if [ ! -f $histfile ]; then
touch $histfile
fi
                              
action=$(tac $histfile | dmenu -fn "$font" -nb $nbcol -nf $nfcol -p "$prompt" -sb $sbcol -sf $sfcol)

if [ "$?" -eq "1" ]; then
exit 1
fi

echo -e $action >> $histfile
nlines=$(wc -l $histfile | cut -d " " -f 1)
if [ $nlines -gt $maxlines ]; then
sed -i -e 1d $histfile
fi

exec $action

```

---

### Post by Mateo on 2007-12-27
> **fuscia said:**
> i'm hooked on wmii, now. i actually bothered to read the user guide (a rarety for me) and i'm enjoying all the things it can do. being an essentially superficial person (or maybe i should say "easily dazzled by a pretty face"), i liked its default look from the start. i even tried coming up with a fluxbox theme to look like it. it didn't really look right, though (like putting a blond wig on a donkey).

One thing about wmii is that it's a little buggy though.  When you create a new column, if you try to move a window using Mod+Mouse1 to another column it will cause wmii to crash.

Also, it doesn't seem to like full-screen very much.  I can't make epiphany go to full screen.  Mplayer will inconsistently work in full screen.  Sometimes it works, sometimes there's lines that appear, sometimes it just won't work.

-----------------------------

I have awesome installed and want to try it.  But how?  It doesn't appear in the GDM list... what do I do?

---

### Post by shearn89 on 2007-12-27
either try and manually add it (not sure how myself - maybe copy+customise an Xsession file? or edit .xinitrc to launch it.

---

### Post by fuscia on 2007-12-28
anyone know the key combo for closing an instance of xterm in wmii?

---

### Post by mali2297 on 2007-12-28
> **fuscia said:**
> anyone know the key combo for closing an instance of xterm in wmii?

From their [guide]("http://www.suckless.org/contrib/guide/wmii-3/guide-en/guide_en/node9.html#SECTION00092000000000000000"):
> 
$MODKEY-Shift-c  kill client


In any environment, you can type exit at the command prompt or press Ctrl+d.

---

### Post by fuscia on 2007-12-28
> **mali2297 said:**
> From their [guide]("http://www.suckless.org/contrib/guide/wmii-3/guide-en/guide_en/node9.html#SECTION00092000000000000000"):


In any environment, you can type exit at the command prompt or press Ctrl+d.

thanks. i've been looking all over the place for it.

---

### Post by Gigamo on 2007-12-28
Sorry to go offtopic, but what panel/window manager is that in your screenshots LoKe? :D

---

### Post by shearn89 on 2007-12-28
I think loke's using dwm? or are you back to OB?

---

### Post by Mateo on 2007-12-28
i tried awesome.  It's ok.  Not sure how to set up custom tags though.

---

### Post by shearn89 on 2007-12-30
you have to edit the .awesomerc file, and add a section like this:
```

rule
{
name = "thunar"
tags = "1","floats","whatever"
}

```

---

### Post by Mateo on 2007-12-30
but can you have custom tags on the fly?

---

### Post by shearn89 on 2007-12-30
i think there's a keybinding to tag something as that tag... not sure.

Yep - just had a look - by default its "mod4 + left click" to tag the client window. You have to click on the tags.

---

### Post by ~LoKe on 2008-01-02
Almost lost this thread.  I've configured it as well as I can for now...not sure how long it'll last (I change my layouts often).

[[img]http://tn3-2.deviantart.com/fs24/300W/f/2007/365/d/3/Desktop_as_seen_on_12_31_2007_by_IcedLoKi.jpg[/img]](http://icedloki.deviantart.com/art/Desktop-as-seen-on-12-31-2007-73458336)

---

### Post by brenix on 2008-01-06
> **~LoKe said:**
> Almost lost this thread.  I've configured it as well as I can for now...not sure how long it'll last (I change my layouts often).


Loke,

Could you post your awsomerc file. I've been having a lot of issues trying to configure it (such as the key bindings and transparency). I can't seem to get neither dwm or awsome to work fully...

EDIT: Got it from your recent screenshot
thx

---

### Post by ~LoKe on 2008-01-21
Bringing this thread back up.  Anyone have an .awesomerc for awesome 2.0?  Apparently they changed everything and I don't even know where to start.

---

### Post by Gigamo on 2008-01-22
> **~LoKe said:**
> Bringing this thread back up.  Anyone have an .awesomerc for awesome 2.0?  Apparently they changed everything and I don't even know where to start.

This is my .awesomerc, which I actually based off of yours and is working in Awesome 2.0, so I don't know if it's going to be a help or not (maybe I'm using a wrong awesomerc too? :D)

```
# Configuration file for awesome

# First physical screen
screen 0
{
    general
    {
        # Windows border size in pixel
        border = 1
        # Pixels number before collapsing window border and screen border
        snap = 8
        # Respect windows minimal geometry
        resize_hints = true
        # Opacity for unfocused windows (with xcompmgr)
        opacity_unfocused = 100
        # Should focus switching move pointer
        focus_move_pointer = false
        # Allow floating windows to be below others
        allow_lower_floats = false
        # Status bar font (Xft)
        font = "sans-7"
#    setstatustext = "test"
    }
    colors
    {
        # Normal border color
        normal_border = "#222222" ## #111111"
        # Normal background color (statusbar)
        normal_bg = "#000000" ## #1b1aa4"
        # Normal foreground color (statusbar)
        normal_fg = "#a8bcff" ## "#eeeeee"
        # Focused border color
        focus_border = "#444444" ## #6666ff"
        # Focused background color (statusbar)
        focus_bg = "#222222" ## #3434bd"
        # Focused foreground color (statusbar)
        focus_fg = "orange"
    }
    # Optional screen padding
    #padding
    #{
    #    left = 5
    #    right = 5
    #    top = 5
    #    bottom = -5
    #}
    statusbar
    {
        # Statusbar position
        # top, bottom, left, right, off
        position = "top"
    }
    tags
    {
        # Tag name
        tag main
        {
            # Tag default layout
            # tile, tileleft, max, floating
            layout = "floating"
        }
        tag www
        {
            # Number of master windows on this tag
            # ncol = 2
            layout = "tile"
        }
        tag media
        {
            ncol = 2
            layout = "floating"
        }
        tag misc
        {
            layout = "tile"
        }
        tag term
        {
            layout = "tile"
            nmaster = 2
        }
 #       tag 6
 #       {
 #           layout = "tile"
 #       }
 #       tag 7
 #       {
 #           layout = "tile"
 #       }
 #       tag 8
 #       {
 #           # Master width factor
 #           # 0 < mwfact < 1
 #           # mwfact = 0.3
 #           layout = "tile"
 #       }
 #       tag 9
 #       {
 #           layout = "floating"
 #       }
    }
    layouts
    {
        # Available layout
        layout tile
        {
            # Symbol drawn in statusbar for this layout
            symbol = "[]="
        }
        layout tileleft
        {
            symbol = "=[]"
        }
        layout max
        {
            symbol = "[ ]"
        }
        layout floating
        {
            symbol = "><>"
        }
    }
}

rules
{
    rule
    {
        name = "swtrunk"
        tags = "www"
    }
#    rule
#    {
#        name = "urxvt"
#        float = true
#    }
    rule
    {
        name = "pidgin"
        tags = "main"
        float = true
    }
    rule
    {
        name = "thunar"
        float = true
    }
    rule
    {
    name = "vlc"
    tags = "media"
    float = true
    }
    rule
    {
    name = "exaile.py"
    tags = "media"
    float = true
    }
    rule
    {
        name = "sonata"
        tags = "media"
        float = true
    }
}

# Mouse buttons bindings
mouse
{
    # For click on tag
    tag
    {
        button = "1"
        command = "tag_view"
    }
    tag
    {
        button = "1"
        modkey = {"Mod4"}
        command = "client_tag"
    }
    tag
    {
        button = "3"
        command = "tag_toggleview"
    }
    tag
    {
        button = "3"
        modkey = {"Mod4"}
        command = "client_toggletag"
    }
    tag
    {
        button = "4"
        command = "tag_viewnext"
    }
    tag
    {
        button = "5"
        command = "tag_viewprev"
    }
    # For click on layout symbol
    layout
    {
        button = "1"
        command = "tag_setlayout"
        arg = "+1"
    }
    layout
    {
        button = "4"
        command = "tag_setlayout"
        arg = "+1"
    }
    layout
    {
        button = "3"
        command = "tag_setlayout"
        arg = "-1"
    }
    layout
    {
        button = "5"
        command = "tag_setlayout"
        arg = "-1"
    }
    # For click on root window
    root
    {
        button = "3"
        command = "spawn"
        arg = "exec urxvt"
    }
    root
    {
        button = "4"
        command = "tag_viewnext"
    }
    root
    {
        button = "5"
        command = "tag_viewprev"
    }
    # For click on client windows
    client
    {
        modkey = {"Mod1"}
        button = "1"
        command = "client_movemouse"
    }
    client
    {
        modkey = {"Mod1"}
        button = "2"
        command = "client_zoom"
    }
    client
    {
        modkey = {"Mod1"}
        button = "3"
        command = "client_resizemouse"
    }
}

# Keys bindings
keys
{
    key
    {
        modkey = {"Mod4"}
        key = "x"
        command = "spawn"
        arg = "exec urxvt"
    }
    key
    {
    modkey = {"Mod4"}
    key = "f"
    command = "spawn"
    arg = "exec swtrunk"
    }
    key
    {
        modkey = {"Mod4"}
        key = "d"
        command = "spawn"
        arg = "exec swiftdove"
    }
    key
    {
        modkey = {"Mod4"}
        key = "e"
        command = "spawn"
        arg = "exec exaile"
    }
    key
    {
    modkey = {"Mod4"}
    key = "r"
    command = "spawn"
    arg = "exec xfrun4"
    }
    key
    {
    modkey = {"Mod4"}
    key = "t"
    command = "spawn"
    arg = "exec thunar"
    }
    key
    {
        modkey = {"Mod4"}
        key = "space"
        command = "tag_setlayout"
        arg = "+1"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "space"
        command = "tag_setlayout"
        arg = "-1"
    }
    key
    {
        modkey = {"Mod4"}
        key = "j"
        command = "client_focusnext"
    }
    key
    {
        modkey = {"Mod4"}
        key = "k"
        command = "client_focusprev"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "j"
        command = "client_swapnext"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "k"
        command = "client_swapprev"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "j"
        command = "screen_focusnext"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "k"
        command = "screen_focusprev"
    }
    key
    {
        modkey = {"Mod4"}
        key = "h"
        command = "tag_setmwfact"
        arg = "-0.05"
    }
    key
    {
        modkey = {"Mod4"}
        key = "l"
        command = "tag_setmwfact"
        arg = "+0.05"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "h"
        command = "tag_setnmaster"
        arg = "+1"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "l"
        command = "tag_setnmaster"
        arg = "-1"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "h"
        command = "tag_setncol"
        arg = "+1"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "l"
        command = "tag_setncol"
        arg = "-1"
    }
    key
    {
        modkey = {"Mod4"}
        key = "Escape"
        command = "tag_viewprev_selected"
    }
    key
    {
        modkey = {"Mod4"}
        key = "Left"
        command = "tag_viewprev"
    }
    key
    {
        modkey = {"Mod4"}
        key = "Right"
        command = "tag_viewnext"
    }
    key
    {
        modkey = {"Mod4"}
        key = "m"
        command = "client_togglemax"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "Return"
        command = "client_zoom"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "space"
        command = "client_togglefloating"
    }
    key
    {
        modkey = {"Mod1"}
        key = "k"
        command = "client_kill"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "q"
        command = "quit"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "r"
        command = "reloadconfig"
    }
    key
    {
       modkey = {"Mod4"}
       key = "0"
       command = "tag_view"
    }
    key
    {
        modkey = {"Mod4"}
        key = "1"
        command = "tag_view"
        arg = "1"
    }
    key
    {
        modkey = {"Mod4"}
        key = "2"
        command = "tag_view"
        arg = "2"
    }
    key
    {
        modkey = {"Mod4"}
        key = "3"
        command = "tag_view"
        arg = "3"
    }
    key
    {
        modkey = {"Mod4"}
        key = "4"
        command = "tag_view"
        arg = "4"
    }
    key
    {
        modkey = {"Mod4"}
        key = "5"
        command = "tag_view"
        arg = "5"
    }
    key
    {
        modkey = {"Mod4"}
        key = "6"
        command = "tag_view"
        arg = "6"
    }
    key
    {
        modkey = {"Mod4"}
        key = "7"
        command = "tag_view"
        arg = "7"
    }
    key
    {
        modkey = {"Mod4"}
        key = "8"
        command = "tag_view"
        arg = "8"
    }
    key
    {
        modkey = {"Mod4"}
        key = "9"
        command = "tag_view"
        arg = "9"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "0"
        command = "tag_toggleview"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "1"
        command = "tag_toggleview"
        arg = "1"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "2"
        command = "tag_toggleview"
        arg = "2"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "3"
        command = "tag_toggleview"
        arg = "3"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "4"
        command = "tag_toggleview"
        arg = "4"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "5"
        command = "tag_toggleview"
        arg = "5"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "6"
        command = "tag_toggleview"
        arg = "6"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "7"
        command = "tag_toggleview"
        arg = "7"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "8"
        command = "tag_toggleview"
        arg = "8"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "9"
        command = "tag_toggleview"
        arg = "9"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "0"
        command = "client_tag"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "1"
        command = "client_tag"
        arg = "1"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "2"
        command = "client_tag"
        arg = "2"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "3"
        command = "client_tag"
        arg = "3"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "4"
        command = "client_tag"
        arg = "4"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "5"
        command = "client_tag"
        arg = "5"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "6"
        command = "client_tag"
        arg = "6"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "7"
        command = "client_tag"
        arg = "7"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "8"
        command = "client_tag"
        arg = "8"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "9"
        command = "client_tag"
        arg = "9"
    }
    key
    {
        modkey = {"Mod4", "Shift", "Control"}
        key = "0"
        command = "client_toggletag"
    }
    key
    {
        modkey = {"Mod4", "Shift", "Control"}
        key = "1"
        command = "client_toggletag"
        arg = "1"
    }
    key
    {
        modkey = {"Mod4", "Shift", "Control"}
        key = "2"
        command = "client_toggletag"
        arg = "2"
    }
    key
    {
        modkey = {"Mod4", "Shift", "Control"}
        key = "3"
        command = "client_toggletag"
        arg = "3"
    }
    key
    {
        modkey = {"Mod4", "Shift", "Control"}
        key = "4"
        command = "client_toggletag"
        arg = "4"
    }
    key
    {
        modkey = {"Mod4", "Shift", "Control"}
        key = "5"
        command = "client_toggletag"
        arg = "5"
    }
    key
    {
        modkey = {"Mod4", "Shift", "Control"}
        key = "6"
        command = "client_toggletag"
        arg = "6"
    }
    key
    {
        modkey = {"Mod4", "Shift", "Control"}
        key = "7"
        command = "client_toggletag"
        arg = "7"
    }
    key
    {
        modkey = {"Mod4", "Shift", "Control"}
        key = "8"
        command = "client_toggletag"
        arg = "8"
    }
    key
    {
        modkey = {"Mod4", "Shift", "Control"}
        key = "9"
        command = "client_toggletag"
        arg = "9"
    }
}
```

---

### Post by mali2297 on 2008-01-22
Recent [news]("http://awesome.naquadah.org/news/"):
> 
version 2.1

The final version 2.1 of awesome is available. To download it, see the download page.

This release fixes some bugs, add some features. You can see some changes from 2.0.

    * Fix crashing bug triggered through awesome-client
    * Do not die anymore on bad config file, use a default internal one
    * Add uicbscreenfocus to switch to a specified screen.
    * Add a focus history.
    * Accept --version option.
    * Add spiral and dwindle layouts.
    * Widget-ise the statusbar.
    * Add new widgets: textbox, graph, progress bar, taglist, focustitle, tasklist, iconbox, layoutinfo, netwmicon.
    * We can now have several statusbar.
    * New uicb: focusclientbyname.
    * Partial EWMH support.
    * Switch to autotools based build system.


You need to update your .awesomerc file if you want to use the new version. There is an example of a configuration file in the source, I attach it here (though I have not tried to use it yet).

---

### Post by Gigamo on 2008-01-22
How would I go installing the new version? Just compile it and it will install over my 2.0?

---

### Post by ~LoKe on 2008-01-22
The documentation is horrible. =/

I'm getting errors like crazy because I'm trying to remake my .awesomerc based on the new template, but the new one is all over the place.  Mouse binds in the taglist?  Images for layouts?  Errrg...

```
screen 0
{
    general
    {
        allow_lower_floats = false
        border = 1
        focus_move_pointer = false
        font = "sans-7"
        new_become_master = false
        new_get_focus = true
        opacity_unfocused = 100
        resize_hints = true
        sloppy_focus = true
        snap = 8
    }
    tags
    {
        tag main
        {
            layout = "tile"
        }
        tag devel
        {
            nmaster = 2
            layout = "tile"
        }
        tag misc
        {
            layout = "tile"
        }
    }
}
screen 1
{
    general
    {
        allow_lower_floats = false
        border = 1
        focus_move_pointer = false
        font = "sans-7"
        new_become_master = false
        new_get_focus = true
        opacity_unfocused = 100
        resize_hints = true
        sloppy_focus = true
        snap = 8
    }
    tags
    {
        tag term
        {
            layout = "tile"
	    	nmaster = 2
        }
        tag devel
        {
            nmaster = 2
            layout = "tile"
        }
        tag media
        {
            ncol = 2
            layout = "tile"
        }
        tag misc
        {
            layout = "tile"
        }
		tag email
		{
	    layout = "max"
		}
    }
}
    colors
    {
        tab_border = "#6666ff"
        normal_border = "#222222"
        normal_bg = "#000000"
        normal_fg = "#a8bcff"
        focus_border = "#6666ff"
        focus_bg = "#000000"
        focus_fg = "orange"
        urgent_fg = "orange"
        urgent_bg = "orange"
    }
    layouts
    {
        layout tile { image = "@iconslayoutsdir@/tilew.png" }
        layout tileleft { image = "@iconslayoutsdir@/tileleftw.png" }
        layout max { image = "@iconslayoutsdir@/maxw.png" }
        layout spiral { image = "@iconslayoutsdir@/spiralw.png" }
        layout dwindle { image = "@iconslayoutsdir@/dwindlew.png" }
        layout floating { image = "@iconslayoutsdir@/floatingw.png" }
    }
    statusbar mystatusbar
    {
        position = "bottom"

        taglist mytaglist
        {
            mouse
            {
                button = "1"
                command = "tag_view"
            }
            mouse
            {
                button = "1"
                modkey = {"Mod4"}
                command = "client_tag"
            }
            mouse
            {
                button = "3"
                command = "tag_toggleview"
            }
            mouse
            {
                button = "3"
                modkey = {"Mod4"}
                command = "client_toggletag"
            }
            mouse
            {
                button = "4"
                command = "tag_viewnext"
            }
            mouse
            {
                button = "5"
                command = "tag_viewprev"
            }
        }
        layoutinfo mylayoutinfo
        {
            mouse
            {
                button = "1"
                command = "tag_setlayout"
                arg = "+1"
            }
            mouse
            {
                button = "4"
                command = "tag_setlayout"
                arg = "+1"
            }
            mouse
            {
                button = "3"
                command = "tag_setlayout"
                arg = "-1"
            }
            mouse
            {
                button = "5"
                command = "tag_setlayout"
                arg = "-1"
            }
        }
        tasklist mytasklist
        {
            mouse
            {
                button = "4"
                command = "client_focusnext"
            }
            mouse
            {
                button = "5"
                command = "client_focusprev"
            }
            mouse
            {
                modkey = {"Mod4"}
                button = "4"
                command = "client_swapnext"
            }
            mouse
            {
                modkey = {"Mod4"}
                button = "5"
                command = "client_swapprev"
            }
        }
    }
}

rules
{
    rule
    {
        name = "Firefox"
        tags = "main"
        float = false
        screen = 0
    }
    rule
    {
        name = "MPlayer"
		tags = "media"
        float = true
		screen = 1
    }
    rule
    {
        name = "gnome-terminal"
		tags = "term"        
		float = false
		screen = 1
    }
    rule
    {
        name = "Gimp"
		tags = "devel"
        float = false
		screen = 0
    }
    rule
    {
		name = "gedit"
		tags = "devel"
		float = false
		screen = 1
    }
    rule
    {
		name = "Thunderbird"
		tags = "email"
		float = false
		screen = 1
    }
}

mouse
{
    root
    {
        button = "3"
        command = "spawn"
        arg = "exec xterm"
    }
    root
    {
        button = "4"
        command = "tag_viewnext"
    }
    root
    {
        button = "5"
        command = "tag_viewprev"
    }
    client
    {
        modkey = {"Mod4"}
        button = "1"
        command = "client_movemouse"
    }
    client
    {
        modkey = {"Mod4"}
        button = "2"
        command = "client_zoom"
    }
    client
    {
        modkey = {"Mod4"}
        button = "3"
        command = "client_resizemouse"
    }
}

keys
{
    key
    {
        modkey = {"Mod4"}
        key = "Return"
        command = "spawn"
        arg = "exec urxvt"
    }
    key
    {
		modkey = {"Mod4"}
		key = "f"
		command = "spawn"
		arg = "exec firefox3"
    }
    key
    {
        modkey = {"Mod4"}
        key = "space"
        command = "tag_setlayout"
        arg = "+1"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "space"
        command = "tag_setlayout"
        arg = "-1"
    }
    key
    {
        modkey = {"Mod4"}
        key = "b"
        command = "statusbar_toggle"
    }
    key
    {
        modkey = {"Mod4"}
        key = "j"
        command = "client_focusnext"
    }
    key
    {
        modkey = {"Mod4"}
        key = "k"
        command = "client_focusprev"
    }
    key
    {
        modkey = {"Mod4"}
        key = "Tab"
        command = "focus_history"
        arg = "-1"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "j"
        command = "client_swapnext"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "k"
        command = "client_swapprev"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "j"
        command = "screen_focus"
        arg = "+1"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "k"
        command = "screen_focus"
        arg = "-1"
    }
    key
    {
        modkey = {"Mod4"}
        key = "h"
        command = "tag_setmwfact"
        arg = "-0.05"
    }
    key
    {
        modkey = {"Mod4"}
        key = "l"
        command = "tag_setmwfact"
        arg = "+0.05"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "h"
        command = "tag_setnmaster"
        arg = "+1"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "l"
        command = "tag_setnmaster"
        arg = "-1"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "h"
        command = "tag_setncol"
        arg = "+1"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "l"
        command = "tag_setncol"
        arg = "-1"
    }
    key
    {
        modkey = {"Mod4"}
        key = "Escape"
        command = "tag_viewprev_selected"
    }
    key
    {
        modkey = {"Mod4"}
        key = "Left"
        command = "tag_viewprev"
    }
    key
    {
        modkey = {"Mod4"}
        key = "Right"
        command = "tag_viewnext"
    }
    key
    {
        modkey = {"Mod4"}
        key = "m"
        command = "client_togglemax"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "Return"
        command = "client_zoom"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "space"
        command = "client_togglefloating"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "c"
        command = "client_kill"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "q"
        command = "quit"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "r"
        command = "exec"
        arg = "awesome"
    }
    key
    {
       modkey = {"Mod4"}
       key = "0"
       command = "tag_view"
    }
    keylist
    {
        modkey = {"Mod4"}
        command = "tag_view"
        keylist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
        arglist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "0"
        command = "tag_toggleview"
    }
    keylist
    {
        modkey = {"Mod4", "Control"}
        command = "tag_toggleview"
        keylist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
        arglist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
    }

    key
    {
        modkey = {"Mod4", "Shift"}
        key = "0"
        command = "client_tag"
    }
    keylist
    {
        modkey = {"Mod4", "Shift"}
        command = "client_tag"
        keylist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
        arglist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
    }

    key
    {
        modkey = {"Mod4", "Shift", "Control"}
        key = "0"
        command = "client_toggletag"
    }
    keylist
    {
        modkey = {"Mod4", "Shift", "Control"}
        command = "client_toggletag"
        keylist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
        arglist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
    }
}
```

---

### Post by Gigamo on 2008-01-22
> **~LoKe said:**
> The documentation is horrible. =/

I'm getting errors like crazy because I'm trying to remake my .awesomerc based on the new template, but the new one is all over the place.  Mouse binds in the taglist?  Images for layouts?  Errrg...

```
screen 0
{
    general
    {
        allow_lower_floats = false
        border = 1
        focus_move_pointer = false
        font = "sans-7"
        new_become_master = false
        new_get_focus = true
        opacity_unfocused = 100
        resize_hints = true
        sloppy_focus = true
        snap = 8
    }
    tags
    {
        tag main
        {
            layout = "tile"
        }
        tag devel
        {
            nmaster = 2
            layout = "tile"
        }
        tag misc
        {
            layout = "tile"
        }
    }
}
screen 1
{
    general
    {
        allow_lower_floats = false
        border = 1
        focus_move_pointer = false
        font = "sans-7"
        new_become_master = false
        new_get_focus = true
        opacity_unfocused = 100
        resize_hints = true
        sloppy_focus = true
        snap = 8
    }
    tags
    {
        tag term
        {
            layout = "tile"
            nmaster = 2
        }
        tag devel
        {
            nmaster = 2
            layout = "tile"
        }
        tag media
        {
            ncol = 2
            layout = "tile"
        }
        tag misc
        {
            layout = "tile"
        }
        tag email
        {
        layout = "max"
        }
    }
}
    colors
    {
        tab_border = "#6666ff"
        normal_border = "#222222"
        normal_bg = "#000000"
        normal_fg = "#a8bcff"
        focus_border = "#6666ff"
        focus_bg = "#000000"
        focus_fg = "orange"
        urgent_fg = "orange"
        urgent_bg = "orange"
    }
    layouts
    {
        layout tile { image = "@iconslayoutsdir@/tilew.png" }
        layout tileleft { image = "@iconslayoutsdir@/tileleftw.png" }
        layout max { image = "@iconslayoutsdir@/maxw.png" }
        layout spiral { image = "@iconslayoutsdir@/spiralw.png" }
        layout dwindle { image = "@iconslayoutsdir@/dwindlew.png" }
        layout floating { image = "@iconslayoutsdir@/floatingw.png" }
    }
    statusbar mystatusbar
    {
        position = "bottom"

        taglist mytaglist
        {
            mouse
            {
                button = "1"
                command = "tag_view"
            }
            mouse
            {
                button = "1"
                modkey = {"Mod4"}
                command = "client_tag"
            }
            mouse
            {
                button = "3"
                command = "tag_toggleview"
            }
            mouse
            {
                button = "3"
                modkey = {"Mod4"}
                command = "client_toggletag"
            }
            mouse
            {
                button = "4"
                command = "tag_viewnext"
            }
            mouse
            {
                button = "5"
                command = "tag_viewprev"
            }
        }
        layoutinfo mylayoutinfo
        {
            mouse
            {
                button = "1"
                command = "tag_setlayout"
                arg = "+1"
            }
            mouse
            {
                button = "4"
                command = "tag_setlayout"
                arg = "+1"
            }
            mouse
            {
                button = "3"
                command = "tag_setlayout"
                arg = "-1"
            }
            mouse
            {
                button = "5"
                command = "tag_setlayout"
                arg = "-1"
            }
        }
        tasklist mytasklist
        {
            mouse
            {
                button = "4"
                command = "client_focusnext"
            }
            mouse
            {
                button = "5"
                command = "client_focusprev"
            }
            mouse
            {
                modkey = {"Mod4"}
                button = "4"
                command = "client_swapnext"
            }
            mouse
            {
                modkey = {"Mod4"}
                button = "5"
                command = "client_swapprev"
            }
        }
    }
}

rules
{
    rule
    {
        name = "Firefox"
        tags = "main"
        float = false
        screen = 0
    }
    rule
    {
        name = "MPlayer"
        tags = "media"
        float = true
        screen = 1
    }
    rule
    {
        name = "gnome-terminal"
        tags = "term"        
        float = false
        screen = 1
    }
    rule
    {
        name = "Gimp"
        tags = "devel"
        float = false
        screen = 0
    }
    rule
    {
        name = "gedit"
        tags = "devel"
        float = false
        screen = 1
    }
    rule
    {
        name = "Thunderbird"
        tags = "email"
        float = false
        screen = 1
    }
}

mouse
{
    root
    {
        button = "3"
        command = "spawn"
        arg = "exec xterm"
    }
    root
    {
        button = "4"
        command = "tag_viewnext"
    }
    root
    {
        button = "5"
        command = "tag_viewprev"
    }
    client
    {
        modkey = {"Mod4"}
        button = "1"
        command = "client_movemouse"
    }
    client
    {
        modkey = {"Mod4"}
        button = "2"
        command = "client_zoom"
    }
    client
    {
        modkey = {"Mod4"}
        button = "3"
        command = "client_resizemouse"
    }
}

keys
{
    key
    {
        modkey = {"Mod4"}
        key = "Return"
        command = "spawn"
        arg = "exec urxvt"
    }
    key
    {
        modkey = {"Mod4"}
        key = "f"
        command = "spawn"
        arg = "exec firefox3"
    }
    key
    {
        modkey = {"Mod4"}
        key = "space"
        command = "tag_setlayout"
        arg = "+1"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "space"
        command = "tag_setlayout"
        arg = "-1"
    }
    key
    {
        modkey = {"Mod4"}
        key = "b"
        command = "statusbar_toggle"
    }
    key
    {
        modkey = {"Mod4"}
        key = "j"
        command = "client_focusnext"
    }
    key
    {
        modkey = {"Mod4"}
        key = "k"
        command = "client_focusprev"
    }
    key
    {
        modkey = {"Mod4"}
        key = "Tab"
        command = "focus_history"
        arg = "-1"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "j"
        command = "client_swapnext"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "k"
        command = "client_swapprev"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "j"
        command = "screen_focus"
        arg = "+1"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "k"
        command = "screen_focus"
        arg = "-1"
    }
    key
    {
        modkey = {"Mod4"}
        key = "h"
        command = "tag_setmwfact"
        arg = "-0.05"
    }
    key
    {
        modkey = {"Mod4"}
        key = "l"
        command = "tag_setmwfact"
        arg = "+0.05"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "h"
        command = "tag_setnmaster"
        arg = "+1"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "l"
        command = "tag_setnmaster"
        arg = "-1"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "h"
        command = "tag_setncol"
        arg = "+1"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "l"
        command = "tag_setncol"
        arg = "-1"
    }
    key
    {
        modkey = {"Mod4"}
        key = "Escape"
        command = "tag_viewprev_selected"
    }
    key
    {
        modkey = {"Mod4"}
        key = "Left"
        command = "tag_viewprev"
    }
    key
    {
        modkey = {"Mod4"}
        key = "Right"
        command = "tag_viewnext"
    }
    key
    {
        modkey = {"Mod4"}
        key = "m"
        command = "client_togglemax"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "Return"
        command = "client_zoom"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "space"
        command = "client_togglefloating"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "c"
        command = "client_kill"
    }
    key
    {
        modkey = {"Mod4", "Shift"}
        key = "q"
        command = "quit"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "r"
        command = "exec"
        arg = "awesome"
    }
    key
    {
       modkey = {"Mod4"}
       key = "0"
       command = "tag_view"
    }
    keylist
    {
        modkey = {"Mod4"}
        command = "tag_view"
        keylist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
        arglist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "0"
        command = "tag_toggleview"
    }
    keylist
    {
        modkey = {"Mod4", "Control"}
        command = "tag_toggleview"
        keylist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
        arglist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
    }

    key
    {
        modkey = {"Mod4", "Shift"}
        key = "0"
        command = "client_tag"
    }
    keylist
    {
        modkey = {"Mod4", "Shift"}
        command = "client_tag"
        keylist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
        arglist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
    }

    key
    {
        modkey = {"Mod4", "Shift", "Control"}
        key = "0"
        command = "client_toggletag"
    }
    keylist
    {
        modkey = {"Mod4", "Shift", "Control"}
        command = "client_toggletag"
        keylist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
        arglist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
    }
}
```

Just to be sure, can the old awesomerc be used in 2.1 or is it preferred to use a new one?

---

### Post by ~LoKe on 2008-01-22
> **Gigamo said:**
> Just to be sure, can the old awesomerc be used in 2.1 or is it preferred to use a new one?

The old one won't work at all.  It'll fail miserably and revert to the default (ew).

---

### Post by Gigamo on 2008-01-22
> **~LoKe said:**
> The old one won't work at all.  It'll fail miserably and revert to the default (ew).

Good to know :D Think I'll stick with the old version for a little longer.

---

### Post by ~LoKe on 2008-01-22
Not terribly fond of Awesome 2.1 so far.  It doesn't help that I'm forced to use icons instead of symbols for my layouts.

---

### Post by Gigamo on 2008-01-22
How are the spiral/dwindle layouts like?

---

### Post by ~LoKe on 2008-01-22
> **Gigamo said:**
> How are the spiral/dwindle layouts like?

I have no idea.  I'll try to figure them out.

---

### Post by ~LoKe on 2008-01-22
Yeah, I have no idea.  In fact, I don't even know how to change the layout on the fly.  I click the symbol and noting happens.  I'm a nub.

---

### Post by Gigamo on 2008-01-22
> **~LoKe said:**
> Yeah, I have no idea.  In fact, I don't even know how to change the layout on the fly.  I click the symbol and noting happens.  I'm a nub.

Nah. It's just a disadvantage of living on the bleeding edge. :D

Offtopic now, but did you actually stick to Arch? Or did you go back to Ubuntu?

---

### Post by ~LoKe on 2008-01-22
> **Gigamo said:**
> Nah. It's just a disadvantage of living on the bleeding edge. :D

Offtopic now, but did you actually stick to Arch? Or did you go back to Ubuntu?

Back to Ubuntu.  Arch was too much of a shock to me, and I couldn't get a bunch of things working.

---

### Post by mali2297 on 2008-01-22
> **Gigamo said:**
> How are the spiral/dwindle layouts like?

Whereas the ordinary tile/tileleft layouts split the screen into proportions 1, 1:1, 2:1:1, 3:1:1:1, 4:1:1:1:1 and so on, the spiral/dwindle layouts split the screen into 1, 1:1, 2:1:1, 4:2:1:1, 8:4:2:1:1,...
That is, all windows get different sizes (except the two smallest).

---

### Post by ~LoKe on 2008-01-22
> **mali2297 said:**
> Whereas the ordinary tile/tileleft layouts split the screen into proportions 1, 1:1, 2:1:1, 3:1:1:1, 4:1:1:1:1 and so on, the spiral/dwindle layouts split the screen into 1, 1:1, 2:1:1, 4:2:1:1, 8:4:2:1:1,...
That is, all windows get different sizes (except the two smallest).

Nice.  How do I "apply" these?  Also, I have a tag specifically for GIMP, would there be a way to have it tile in a way that would made the main panel small on the left, the main editor the largest in the middle, and the layers/etc small on the right?

---

### Post by mali2297 on 2008-01-22
> **~LoKe said:**
> Nice.  How do I "apply" these?  Also, I have a tag specifically for GIMP, would there be a way to have it tile in a way that would made the main panel small on the left, the main editor the largest in the middle, and the layers/etc small on the right?

I do not think that these new layouts will help you to achieve that. You could try messing with the variables *layout, mwfact* and *nmaster* inside one of the tag { } sections, but I do not know whether it is possible to specify the positions of the different GIMP windows.

---

### Post by mali2297 on 2008-01-22
> **~LoKe said:**
> Yeah, I have no idea.  In fact, I don't even know how to change the layout on the fly.  I click the symbol and noting happens.  I'm a nub.

What about Mod4+space?

> 
    key
    {
        modkey = {"Mod4"}
        key = "space"
        command = "tag_setlayout"
        arg = "+1"
    }


---

### Post by ~LoKe on 2008-01-22
> **mali2297 said:**
> What about Mod4+space?

Nope.  It's in my key bind list, but it doesn't "do" anything.  I'm probably trying to use it wrong.

---

### Post by shearn89 on 2008-01-23
I can't even compile 2.1... i guess i'll just have to miss out on the spiral layouts.

---

### Post by ~LoKe on 2008-01-23
Well, I got it working.  It's a lot more work but it seems worth it.  I must say, the config is kind of random, with mouse binds all split up.  I understand why, though.

---

### Post by ~LoKe on 2008-01-23
Here's my .awesomerc for **2.1 only**.

```
screen "0"
{
	general
	{
	    border = 1
	    snap = 8
	    resize_hints = true
	    opacity_unfocused = 100
	    focus_move_pointer = false
	    allow_lower_floats = false
	    sloppy_focus = true
	    new_become_master = true
	    new_get_focus = true
	    font = "sans-7"
	}
	statusbar "mystatusbar"
	{
		position = "top"
		height = 0
	    width = 0
	    taglist "mytaglist"
		{
			x = -1
			y = -1
			mouse 
			{
		        modkey = {}
		        button = "1"
				command = "tag_view"
			}
			mouse
			{
	        	modkey = {"Mod4"}
	        	button = "1"
		        command = "client_tag"
			}
      		mouse
			{
		        modkey = {}
    		    button = "3"
    		    command = "tag_toggleview"
    		}
      		mouse
			{
	        	modkey = {"Mod4"}
	        	button = "3"
	        	command = "client_toggletag"
		    }
      		mouse
			{
        		modkey = {}
        		button = "4"
        		command = "tag_viewnext"
      		}
      		mouse
			{
        		modkey = {}
        		button = "5"
        		command = "tag_viewprev"
      		}
		}
    	layoutinfo "mylayoutinfo"
		{
      		x = -1
      		y = -1
      		mouse
			{
        		modkey = {}
        		button = "1"
        		command = "tag_setlayout"
        		arg = "+1"
      		}
      		mouse
			{
        		modkey = {}
        		button = "4"
        		command = "tag_setlayout"
        		arg = "+1"
      		}
      		mouse
			{
        		modkey = {}
        		button = "3"
        		command = "tag_setlayout"
        		arg = "-1"
      		}
      		mouse
			{
        		modkey = {}
        		button = "5"
        		command = "tag_setlayout"
        		arg = "-1"
      		}
    	}
    	tasklist "mytasklist" 
		{
      		x = -1
      		y = -1
      		mouse
			{
        		modkey = {}
        		button = "4"
        		command = "client_focusnext"
        		# arg = ""
      		}
      		mouse
			{
        		modkey = {}
        		button = "5"
        		command = "client_focusprev"
        		# arg = ""
     		}
      		mouse
			{
        		modkey = {"Mod4"}
        		button = "4"
        		command = "client_swapnext"
        		# arg = ""
      		}
      		mouse
			{
        		modkey = {"Mod4"}
        		button = "5"
        		command = "client_swapprev"
       			# arg = ""
      		}
     		# fg = ""
      		# bg = ""
      		# focus_fg = ""
      		# focus_bg = ""
      		# font = ""
      		align = "left"
      		show_icons = false
      		show_all = false
    	}
		textbox mpd 
		{
			text = "-" #the - will be replaced by mpd playing
		}
  	}
  	tags
	{
	    tag ":main"
		{
			layout = "tile"
      		mwfact = 0.500000
      		nmaster = 1
      		ncol = 1
    	}
    	tag ":devel"
		{
	      	layout = "tile"
	      	mwfact = 0.500000
 	     	nmaster = 1
	      	ncol = 4
 	   }
 	   tag ":misc"
		{
 	     	layout = "tile"
 	     	mwfact = 0.500000
 	     	nmaster = 1
 	     	ncol = 1
	    }
	}
	colors
	{
		normal_border = "#777777"
        normal_bg = "#000000"
        normal_fg = "#a8bcff"
        focus_border = "#000000"
        focus_bg = "#000000"
        focus_fg = "orange"
    	urgent_bg = "#000000"
    	urgent_fg = "orange"
    	tab_border = "#ff0000"
	}
	layouts
	{
		layout "tile"		{image = "/usr/local/share/awesome/icons/layouts/tile.png"}
		layout "tileleft"	{image = "/usr/local/share/awesome/icons/layouts/tileleft.png"}
		layout "max"		{image = "/usr/local/share/awesome/icons/layouts/max.png"}
		layout "spiral"		{image = "/usr/local/share/awesome/icons/layouts/spiral.png"}
		layout "dwindle"	{image = "/usr/local/share/awesome/icons/layouts/dwindle.png"}
		layout "floating"	{image = "/usr/local/share/awesome/icons/layouts/floating.png"}
	}
	padding
	{
    	top = 0
    	bottom = 0
    	right = 0
    	left = 0
  	}
}
screen "1"
{
	general
	{
	    border = 1
	    snap = 8
	    resize_hints = true
	    opacity_unfocused = 100
	    focus_move_pointer = false
	    allow_lower_floats = false
	    sloppy_focus = true
	    new_become_master = true
	    new_get_focus = true
	    font = "sans-7"
	}
	statusbar "mystatusbar"
	{
		position = "top"
		height = 0
	    width = 0
	    taglist "mytaglist"
		{
			x = -1
			y = -1
			mouse 
			{
		        modkey = {}
		        button = "1"
				command = "tag_view"
			}
			mouse
			{
	        	modkey = {"Mod4"}
	        	button = "1"
		        command = "client_tag"
			}
      		mouse
			{
		        modkey = {}
    		    button = "3"
    		    command = "tag_toggleview"
    		}
      		mouse
			{
	        	modkey = {"Mod4"}
	        	button = "3"
	        	command = "client_toggletag"
		    }
      		mouse
			{
        		modkey = {}
        		button = "4"
        		command = "tag_viewnext"
      		}
      		mouse
			{
        		modkey = {}
        		button = "5"
        		command = "tag_viewprev"
      		}
		}
    	layoutinfo "mylayoutinfo"
		{
      		x = -1
      		y = -1
      		mouse
			{
        		modkey = {}
        		button = "1"
        		command = "tag_setlayout"
        		arg = "+1"
      		}
      		mouse
			{
        		modkey = {}
        		button = "4"
        		command = "tag_setlayout"
        		arg = "+1"
      		}
      		mouse
			{
        		modkey = {}
        		button = "3"
        		command = "tag_setlayout"
        		arg = "-1"
      		}
      		mouse
			{
        		modkey = {}
        		button = "5"
        		command = "tag_setlayout"
        		arg = "-1"
      		}
    	}
    	tasklist "mytasklist" 
		{
      		x = -1
      		y = -1
      		mouse
			{
        		modkey = {}
        		button = "4"
        		command = "client_focusnext"
        		# arg = ""
      		}
      		mouse
			{
        		modkey = {}
        		button = "5"
        		command = "client_focusprev"
        		# arg = ""
     		}
      		mouse
			{
        		modkey = {"Mod4"}
        		button = "4"
        		command = "client_swapnext"
        		# arg = ""
      		}
      		mouse
			{
        		modkey = {"Mod4"}
        		button = "5"
        		command = "client_swapprev"
       			# arg = ""
      		}
     		# fg = ""
      		# bg = ""
      		# focus_fg = ""
      		# focus_bg = ""
      		# font = ""
      		align = "left"
      		show_icons = false
      		show_all = false
    	}
	    textbox clock
		{
			text = "-" #the - will be replaced by the date and time
		}
  	}
  	tags
	{
	    tag ":term"
		{
			layout = "tile"
      		mwfact = 0.500000
      		nmaster = 1
      		ncol = 1
    	}
    	tag ":devel"
		{
	      	layout = "tile"
	      	mwfact = 0.500000
 	     	nmaster = 1
	      	ncol = 1
 	   }
 	   tag ":media"
		{
 	     	layout = "tile"
 	     	mwfact = 0.500000
 	     	nmaster = 1
 	     	ncol = 1
	    }
	    tag ":misc"
		{
  	    	layout = "tile"
 	     	mwfact = 0.500000
  	 	   	nmaster = 1
  	    	ncol = 1
		}
    	tag ":email"
		{
      		layout = "tile"
      		mwfact = 0.500000
     		nmaster = 1
      		ncol = 1
    	}
	}
	colors
	{
		normal_border = "#777777"
        normal_bg = "#000000"
        normal_fg = "#a8bcff"
        focus_border = "#000000"
        focus_bg = "#000000"
        focus_fg = "orange"
    	urgent_bg = "#000000"
    	urgent_fg = "orange"
    	tab_border = "#ff0000"
	}
	layouts
	{
		layout "tile"		{image = "/usr/local/share/awesome/icons/layouts/tile.png"}
		layout "tileleft"	{image = "/usr/local/share/awesome/icons/layouts/tileleft.png"}
    	layout "max"		{image = "/usr/local/share/awesome/icons/layouts/max.png"}
	    layout "spiral"		{image = "/usr/local/share/awesome/icons/layouts/spiral.png"}
	    layout "dwindle"	{image = "/usr/local/share/awesome/icons/layouts/dwindle.png"}
		layout "floating"	{image = "/usr/local/share/awesome/icons/layouts/floating.png"}
	}
	padding
	{
    	top = 0
    	bottom = 0
    	right = 0
    	left = 0
  	}
}
rules
	{
  	rule
	{
	    name = "Gimp"
		tags = ":devel"
	    float = "true"
	    screen = 0
	    not_master = false
	}
	rule
	{
	    name = "MPlayer"
		tags = ":media"
	    float = "true"
	    screen = 1
	    not_master = false
	}
	rule
	{
	    name = "Thunderbird"
		tags = ":email"
	    float = "true"
	    screen = 1
	    not_master = false
	}
	rule
	{
	    name = "gedit"
	    tags = ":devel"
    	float = "false"
    	screen = 1
    	not_master = false
  	}
	rule
	{
		name = "urxvt"
		tags = ":term"
		float = "true"
		screen = 1
		not_master = true
	}
	rule
	{
		name = "firefox"
		tags = ":main"
		float = "false"
		screen = "0"
		not_master = false
	}
}
keys
	{
	key
	{
	    modkey = {"Mod4"}
	    key = "Return"
	    command = "spawn"
	    arg = "exec urxvt"
	}
	key
	{
		modkey = {"Mod4"}
		key = "f"
		command = "spawn"
		arg = "exec firefox"
	}
  	key
	{
	    modkey = {"Mod4"}
	    key = "space"
	    command = "tag_setlayout"
	    arg = "+1"
	}
	key
	{
	    modkey = {"Mod4", "Shift"}
	    key = "space"
	    command = "tag_setlayout"
	    arg = "-1"
	}
	key
	{
	    modkey = {"Mod4"}
	    key = "b"
	    command = "statusbar_toggle"
	    # arg = ""
	}
	key
	{
	    modkey = {"Mod4"}
	    key = "j"
	    command = "client_focusnext"
	    # arg = ""
	}
	key
	{
	    modkey = {"Mod4"}
	    key = "k"
	    command = "client_focusprev"
	    # arg = ""
	}
	key
	{
	    modkey = {"Mod4"}
	    key = "Tab"
	    command = "focus_history"
	    arg = "-1"
	}
	key
	{
	    modkey = {"Mod4", "Shift"}
	    key = "j"
	    command = "client_swapnext"
	    # arg = ""
	}
	key
	{
	    modkey = {"Mod4", "Shift"}
	    key = "k"
	    command = "client_swapprev"
	    # arg = ""
  	}
	key
	{
	    modkey = {"Mod4", "Control"}
	    key = "j"
	    command = "screen_focus"
	    arg = "+1"
  	}
  	key
	{
	    modkey = {"Mod4", "Control"}
	    key = "k"
	    command = "screen_focus"
	    arg = "-1"
  	}
	key
	{
	    modkey = {"Mod4"}
	    key = "h"
	    command = "tag_setmwfact"
	    arg = "-0.05"
  	}
  	key
	{
	    modkey = {"Mod4"}
	    key = "l"
	    command = "tag_setmwfact"
	    arg = "+0.05"
  	}
  	key
	{
    	modkey = {"Mod4", "Shift"}
    	key = "h"
    	command = "tag_setnmaster"
    	arg = "+1"
  	}
  	key
	{
	    modkey = {"Mod4", "Shift"}
	    key = "l"
	    command = "tag_setnmaster"
	    arg = "-1"
  	}
  	key
	{
	    modkey = {"Mod4", "Control"}
	    key = "h"
	    command = "tag_setncol"
	    arg = "+1"
  	}
  	key
	{
	    modkey = {"Mod4", "Control"}
	    key = "l"
	    command = "tag_setncol"
	    arg = "-1"
  	}
 	key
	{
	    modkey = {"Mod4"}
	    key = "Escape"
	    command = "tag_viewprev_selected"
	    # arg = ""
  	}
  	key
	{
	    modkey = {"Mod4"}
	    key = "Left"
	    command = "tag_viewprev"
	    # arg = ""
  	}
  	key	
	{
	    modkey = {"Mod4"}
	    key = "Right"
	    command = "tag_viewnext"
	    # arg = ""
  	}
  	key
	{
	    modkey = {"Mod4"}
	    key = "m"
	    command = "client_togglemax"
	    # arg = ""
	}
  	key
	{
	    modkey = {"Mod4", "Control"}
	    key = "Return"
	    command = "client_zoom"
	    # arg = ""
  	}
  	key
	{
	    modkey = {"Mod4", "Control"}
	    key = "space"
	    command = "client_togglefloating"
	    # arg = ""
  	}
	key
    {
        modkey = {"Mod4", "Control"}
        key = "Left"
        command = "spawn"
        arg = "exec mpc prev"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "Right"
        command = "spawn"
        arg = "exec mpc next"
    }
  	key
	{
	    modkey = {"Mod4", "Shift"}
	    key = "c"
	    command = "client_kill"
	    # arg = ""
  	}
  	key
	{
	    modkey = {"Mod4", "Shift"}
	    key = "q"
	    command = "quit"
	    # arg = ""
  	}
  	key
	{
	    modkey = {"Mod4", "Control"}
	    key = "r"
	    command = "exec"
	    arg = "awesome"
  	}
  	key
	{
    	modkey = {"Mod4"}
    	key = "0"
    	command = "tag_view"
    	# arg = ""
  	}
  	key
	{
	    modkey = {"Mod4", "Control"}
	    key = "0"
	    command = "tag_toggleview"
	    # arg = ""
  	}
  	key
	{
	    modkey = {"Mod4", "Shift"}
	    key = "0"
	    command = "client_tag"
	    # arg = ""
	}
  	key
	{
	    modkey = {"Mod4", "Shift", "Control"}
	    key = "0"
	    command = "client_toggletag"
	    # arg = ""
  	}
  	keylist
	{
	    modkey = {"Mod4"}
	    keylist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
	    command = "tag_view"
	    arglist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
	}
  	keylist
	{
	    modkey = {"Mod4", "Control"}
	    keylist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
	    command = "tag_toggleview"
	    arglist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
  	}
  	keylist
	{
	    modkey = {"Mod4", "Shift"}
	    keylist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
	    command = "client_tag"
	    arglist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
  	}
  	keylist
	{
	    modkey = {"Mod4", "Shift", "Control"}
    	keylist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
    	command = "client_toggletag"
    	arglist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
  	}
}
mouse
	{
	root
	{
	    modkey = {}
	    button = "3"
	    command = "spawn"
	    arg = "exec xterm"
  	}
  	root
	{
	    modkey = {}
	    button = "4"
	    command = "tag_viewnext"
	    # arg = ""
  	}
  	root
	{
	    modkey = {}
	    button = "5"
	    command = "tag_viewprev"
	    # arg = ""
  	}
  	client
	{
	    modkey = {"Mod4"}
	    button = "1"
	    command = "client_movemouse"
	    # arg = ""
  	}
  	client
	{
	    modkey = {"Mod4"}
	    button = "2"
	    command = "client_zoom"
	    # arg = ""
  	}
  	client
	{
	    modkey = {"Mod4"}
	    button = "3"
	    command = "client_resizemouse"
	    # arg = ""
	}
}
```

---

### Post by Gigamo on 2008-01-23
Thanks ;)

---

### Post by shearn89 on 2008-01-24
Someone posted a PKGBUILD on the AUR, so i now have 2.1! It took a while to re-jig the config file to match my orig, and i think there are a bunch of keybindings i'll never use, but its pretty much back to normal. I just need to finish off my statusbar scripts.

---

### Post by Gigamo on 2008-01-24
> **shearn89 said:**
> Someone posted a PKGBUILD on the AUR, so i now have 2.1! It took a while to re-jig the config file to match my orig, and i think there are a bunch of keybindings i'll never use, but its pretty much back to normal. I just need to finish off my statusbar scripts.

When you finish the statusbar text, let me know how you did it. That's the only thing I can't get working in 2.1.

---

### Post by shearn89 on 2008-01-24
I've updated my Howto for 2.1 - it includes a bit on status texts, thanks to Loke's post about it on the same thread.

briefly:
```

echo 0 widget_tell <widgetname> "text" | awesome-client

```

Where widgetname is defined by:
```

textbox widgetname
      { text = "-" #to be changed by script }

```
in .awesomerc.

---

### Post by y-lee on 2008-03-07
It was a bit of work but here is my dwm desktop as it is now :)

[CENTER][IMG]http://www.fileden.com/files/2006/11/26/425005/sdwm0.jpeg[/IMG]
[Original image]("http://www.fileden.com/files/2006/11/26/425005/Images/Ubuntu/dwm0.jpeg")[/CENTER]

```
/* config.h  Configuration header file for the dynamic window manager for X 
			My custom file for dwm version 4.7
			 http://www.suckless.org/wiki/dwm					*/

/* appearance */
#define BARPOS			BarTop /* BarBot, BarOff */
#define BORDERPX		1
#define FONT			"-*-bitstream vera sans mono-medium-r-normal-*-16-*-*-*-*-*-*-*"
#define NORMBORDERCOLOR	"#777777"
#define NORMBGCOLOR		"#eeeeee"
#define NORMFGCOLOR		"#222222"
#define DMFGCOLOR			"#FF8700"
#define SELBORDERCOLOR	"#ff0000"
#define SELBGCOLOR			"#aaaaaa"
#define SELFGCOLOR			"#ffffff"
#define TOPBAR			True		/* False */

/* tagging */
const char tags[][MAXTAGLEN] = { "home","www", "rss", "im", "media", "code", "misc"};
Bool seltags[LENGTH(tags)] = {[0] = True};

Rule rules[] = {
	/* class:instance:title regex	tags regex	isfloating */

	{ "Firefox",				"www",		False },
	{ "swiftweasel",			"www",		True  },
	{ "liferea",				"rss",		False },
	{ "pidgin",				"im",		True  },
	{ "amsn",				"im",		True  },
	{ "prism",				"media",		True  },
	{ "xmms",				"media",		True  },
	{ "emacs21",				"code",		False },
	{ "gvim",					"code",		False },
	{ "Gimp",				NULL,		True  },
	{ "MPlayer",				NULL,		True  },
	{ "Acroread",				NULL,		True  },
};

/* layout(s) */
#define MWFACT			0.6		/* master width factor [0.1 .. 0.9] */
#define RESIZEHINTS		True	/* False - respect size hints in tiled resizals */
#define SNAP			32		/* snap pixel 32 */
Layout layouts[] = {
	/* symbol	function */

	{ "[f]",		floating },  /* first entry is default */
	{ "[t]",		tile },
};

/* key definitions */
#define MODKEY		Mod1Mask 	/* Alt key 	 */
#define WINKEY		Mod4Mask	/*Windows key */

Key keys[] = {
	/* modifier			key		function	argument */

	{ MODKEY,			XK_p,		spawn,
		"exe=`dmenu_path | dmenu -fn '"FONT"' -nb '"NORMBGCOLOR"' -nf '"NORMFGCOLOR"'"
		" -sb '"SELBGCOLOR"' -sf '"SELFGCOLOR"'` && exec $exe" },
	{ MODKEY,						XK_F2,		spawn,
		"exe=`dmenu_path | dmenu -fn '"FONT"' -nb '"NORMBGCOLOR"' -nf '"NORMFGCOLOR"'"
		" -sb '"SELBGCOLOR"' -sf '"SELFGCOLOR"'` && exec $exe" },
	{ MODKEY,						XK_F1,	       	spawn,		 "exec dwmhelp" },
	{ WINKEY,						XK_F3,	       	spawn,		 "exec conky" },
	{ WINKEY|ControlMask,			XK_F3,	       	spawn,		 "exec pkill conky" },
	{ MODKEY|ShiftMask,				XK_q,		quit,		NULL },
	{ WINKEY,						XK_Escape,	quit,		NULL },

	/* Open terminal programs	*/
	{ MODKEY|ShiftMask,				XK_Return,	spawn,		 "exec mrxvt" },
	{ MODKEY|ControlMask|ShiftMask,	XK_Return,	spawn,		 "exec mrxvt -name Root" },
	{ WINKEY,						XK_Return,	spawn,		 "exec mrxvt" },
	{ WINKEY,						XK_t,		spawn,		 "exec gnome-terminal" },
	{ WINKEY|ControlMask,			XK_t,		spawn,		 "exec gksu x-terminal-emulator" },

	/* dwm window control */
	{ MODKEY,						XK_space,	setlayout,	NULL },
	{ MODKEY,						XK_b,		togglebar,	NULL },
	{ MODKEY,						XK_j,		focusnext,	NULL },
	{ MODKEY,						XK_k,		focusprev,	NULL },
	{ MODKEY,						XK_h,		setmwfact,	"-0.05" },
	{ MODKEY,						XK_l,		setmwfact,	"+0.05" },	
	{ MODKEY,						XK_m,		togglemax,	NULL },
	{ MODKEY,						XK_Return,	zoom,		NULL },
	{ MODKEY,						XK_Tab,		viewprevtag,	NULL },
	{ MODKEY|ShiftMask,				XK_space,	togglefloating,NULL },
	{ MODKEY|ShiftMask,				XK_c,		killclient,	NULL },
			/* 	Alt+ 0 	View all windows with any tag. */
	{ MODKEY,						XK_0,		view,		NULL   },
			/*	Alt+ [1...n] 	View all windows with nth tag */
	{ MODKEY,						XK_1,		view,		tags[0] },
	{ MODKEY,						XK_2,		view,		tags[1] },
	{ MODKEY,						XK_3,		view,		tags[2] },
	{ MODKEY,						XK_4,		view,		tags[3] },
	{ MODKEY,						XK_5,		view,		tags[4] },
	{ MODKEY,						XK_6,		view,		tags[5] },
	{ MODKEY,						XK_7,		view,		tags[6] },
	{ MODKEY,						XK_8,		view,		tags[7] },
	{ MODKEY,						XK_9,		view,		tags[8] },
		/* Alt - Control [1..n]	Add/remove all windows with nth tag to/from the view. */
	{ MODKEY|ControlMask,			XK_1,		toggleview,	tags[0] },
	{ MODKEY|ControlMask,			XK_2,		toggleview,	tags[1] },
	{ MODKEY|ControlMask,			XK_3,		toggleview,	tags[2] },
	{ MODKEY|ControlMask,			XK_4,		toggleview,	tags[3] },
	{ MODKEY|ControlMask,			XK_5,		toggleview,	tags[4] },
	{ MODKEY|ControlMask,			XK_6,		toggleview,	tags[5] },
	{ MODKEY|ControlMask,			XK_7,		toggleview,	tags[6] },
	{ MODKEY|ControlMask,			XK_8,		toggleview,	tags[7] },
	{ MODKEY|ControlMask,			XK_9,		toggleview,	tags[8] },
		/* Apply all tags to current window. */
	{ MODKEY|ShiftMask,				XK_0,		tag,			NULL }, 	
		/* Alt - Shiftl [1..n]		Apply nth tag to current window.. */
	{ MODKEY|ShiftMask,				XK_1,		tag,			tags[0] },
	{ MODKEY|ShiftMask,				XK_2,		tag,			tags[1] },
	{ MODKEY|ShiftMask,				XK_3,		tag,			tags[2] },
	{ MODKEY|ShiftMask,				XK_4,		tag,			tags[3] },
	{ MODKEY|ShiftMask,				XK_5,		tag,			tags[4] },
	{ MODKEY|ShiftMask,				XK_6,		tag,			tags[5] },
	{ MODKEY|ShiftMask,				XK_7,		tag,			tags[6] },
	{ MODKEY|ShiftMask,				XK_8,		tag,			tags[7] },
	{ MODKEY|ShiftMask,				XK_9,		tag,			tags[8] },
		/*  Add/remove nth tag to/from current window. */
	{ MODKEY|ControlMask|ShiftMask,	XK_1,		toggletag,	tags[0] },
	{ MODKEY|ControlMask|ShiftMask,	XK_2,		toggletag,	tags[1] },
	{ MODKEY|ControlMask|ShiftMask,	XK_3,		toggletag,	tags[2] },
	{ MODKEY|ControlMask|ShiftMask,	XK_4,		toggletag,	tags[3] },
	{ MODKEY|ControlMask|ShiftMask,	XK_5,		toggletag,	tags[4] },
	{ MODKEY|ControlMask|ShiftMask,	XK_6,		toggletag,	tags[5] },
	{ MODKEY|ControlMask|ShiftMask,	XK_7,		toggletag,	tags[6] },
	{ MODKEY|ControlMask|ShiftMask,	XK_8,		toggletag,	tags[7] },
	{ MODKEY|ControlMask|ShiftMask,	XK_9,		toggletag,	tags[8] },
	
	/* Open applications	*/
	{ WINKEY,						XK_a,		spawn,		"exec amsn" },
	{ WINKEY,						XK_e,		spawn,		"exec emacs21 -i" },	
	{ WINKEY, 						XK_f,		spawn,		"exec pcmanfm" },
	{ WINKEY,						XK_g,	       	spawn,		"exec gedit" },
	{ WINKEY|ControlMask,			XK_g,	       	spawn,		"exec gksudo gedit" },
	{ WINKEY,						XK_l,	       	spawn,		"exec liferea" },
	{ WINKEY,						XK_p,		spawn,		"exec pidgin" },
	{ WINKEY,						XK_s,	       	spawn,		"dbus-launch swiftweasel" },
	{ WINKEY, 						XK_v,		spawn,		"exec gvim" },
	{ WINKEY, 						XK_x,		spawn,	 	"exec xmms" },

};
```


My launcher code is

```
#!/bin/sh
#
# launcher for dwm.
#
xrandr -s 1
feh --bg-scale /home/starhawk/Documents/Images/Goddess/BubbleBath.jpg
while true
do
echo "[`date '+%r'`] `keytest`"
sleep 2
done | dwm
xrandr -s 0
```

I use xrandr to change the screen resolution, dwm at first set the resolution to the max and I didn't care for that. I didn't really know how to change the screen resolution in X but found this after some research. It seems to work and note I reset the resolution after exiting dwm. I found out I had to do that because the gnome login screen was a mess otherwise.

The keytest function in the launcher is a small script I wrote to check the status of the Cap lock and Num lock key and display either C or N or both if they are set beside the time. It's a hack job and code I'mnot proud of. But I am kinda new to linux so .... Anyway couldn't really find a linux command to test keyboard status like that, I ended up using 

```
 xset -q|grep "LED mask:"|sed -e 's/auto repeat.* //'
```

and testing the output of that. I don't understand grep or sed in detail so I'm lucky I got that far. A better solution would be greatly appreciated btw. 

Also had to create a .gtkrc-2.0 file and a.gtkrc.mine file to make Gtk programs look right and avoid an error message pcmanfm (a file manager I'm using)  kept giving me. The first .gtkrc-2.0 was created by a program [gtk-chtheme]("http://plasmasturm.org/code/gtk-chtheme/") I installed, The other I made myself.

```
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/usr/share/themes/Human/gtk-2.0/gtkrc"

include "/home/starhawk/.gtkrc.mine"
```



```
gtk-icon-theme-name="Human"
gtk-icon-sizes="gtk-menu=16,16:
                gtk-button=16,16:
                gtk-small-toolbar=16,16:
                gtk-large-toolbar=16,16:
                gtk-dnd=16,16:
                gtk-dialog=16,16"
gtk-toolbar-style = GTK_TOOLBAR_ICONS

```

And my conky is pretty simple and straight forward

```
# Conky sample configuration
#
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=10

# Text alpha when using Xft
xftalpha 0.8

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 5.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour hotpink

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 25
gap_y 10

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16) 
#min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
#min_port_monitor_connections 256

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${font  Bitstream Vera Serif Roman:size=12}
${color lightgrey}${alignc}${time %a, } ${color #ddaa00}${time %B %e %G}$font
 
${color #ddaa00}${font  Bitstream Vera Serif Roman:size=12}$nodename ${hr 2}$font$color 
Ubuntu $sysname $kernel on $machine
${color #FF8700}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color white}${freq_dyn_g}Ghz 
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${font  Bitstream Vera Serif Roman:size=12}${color #ddaa00}CPU Usage:$font${color #cc2222} $cpu% ${cpubar}
${color red}${cpugraph 0000ff 00ff00}
${font  Bitstream Vera Serif Roman:size=12}${color #ddaa00}RAM Usage:$font$color $mem/$memmax - $memperc% 
${alignc}${color red} ${membar}
${font  Bitstream Vera Serif Roman:size=12}${color #ddaa00}Swap Usage:$font${alignc}$color $swap/$swapmax - $swapperc% 
${alignc}${color blue}${swapbar}
${font  Bitstream Vera Serif Roman:size=12}${color #ddaa00}File systems:$font
$color${fs_used /}/${fs_size /}${color red} ${fs_bar /}

${font  Bitstream Vera Serif Roman:size=12}${color #ddaa00}Networking:$font
Down:${color #8844ee} ${downspeed eth0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed eth0} k/s
${color #0000ff}${downspeedgraph eth0 32,150 ff0000 0000ff} ${color #22ccff}${upspeedgraph eth0 32,150 0000ff ff0000}
${color #ddaa00}${hr 2}$color
${font  Bitstream Vera Serif Roman:size=12}${color #ddaa00}Processes:$font$color $processes  ${color grey}Running:$color $running_processes
${color}Name              PID     CPU%   MEM%
${color #ddaa00} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}


```

And no desktop is really complete without a screensaver and lock screen ability so I installed and use [xscreensaver]("http://www.jwz.org/xscreensaver/"). It works beautifully with dwm, I'm impressed :)

One question tho for the linux and dwm gurus out there, When i sign in the gnome login screen under sessions dwm shows up as ** foo** but my usr/share/xsession/dwm.desktop file looks like

```
[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=dwm-launch
TryExec=dwm-launch
Name=DWM
Comment=DWM window manager
```

How can I change that so it shows up as dwm?

Anyway 2 more screen shots, [One]("http://www.fileden.com/files/2006/11/26/425005/dwm1.jpeg") and [Two]("http://www.fileden.com/files/2006/11/26/425005/Images/Ubuntu/dwm2.jpeg"). The  first shows the dmenu system in use and the second one I think shows Pandora using [mozillas Prism]("http://labs.mozilla.com/2007/10/prism/")

---

### Post by xpoulet on 2008-03-12
Hi all.

Can someone explain me the way to fix the compilation error shown in [ this post ](http://ubuntuforums.org/showpost.php?p=3968491&postcount=11), please ?

I can't find or don't understand what to do.
;)

---

### Post by y-lee on 2008-03-12
> **xpoulet said:**
> Hi all.

Can someone explain me the way to fix the compilation error shown in [ this post ](http://ubuntuforums.org/showpost.php?p=3968491&postcount=11), please ?

I can't find or don't understand what to do.
;)

Hmm looks like you may not have the X11 header files dwm needs, open synaptic and search for libx11-dev. Find it and install it and try to compile again. If it is installed or this doesn't work for ya  post back.

---

### Post by xpoulet on 2008-03-12
Hi y-lee

Fisrt of all, thanx for your help.
The package you mentioned is already installed : "libx11-dev is already the newest version."

---

### Post by y-lee on 2008-03-12
> **xpoulet said:**
> Hi y-lee

First of all, thanx for your help.
The package you mentioned is already installed : "libx11-dev is already the newest version."

Yeal looking thru the dwm.c  code the errors you are getting look like your header file is not been read or incorrect. All the variables it says are undefined should defined in there :confused:

What does your config.h file in the dwm directory look like? Would you post it here.

---

### Post by Thanoulis on 2008-06-01
Try to install the build-essential package too...

---

### Post by kaiju on 2008-06-20
nice thread. hope to see some more posts from you guys as awesome evolves :)

---

