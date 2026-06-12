---
title: "I don't how to configure DWM right..."
date: 2009-05-07
forum: Desktop Environments
---

### Post by tombom62 on 2009-05-07
Hey everyone.  I'm trying DWM.  I have a big enough screen and a slow enough computer :P  I don't really understand the tag system, how to open programs, or anything.  I know about the config.h and here's mine based off some ranodm ones I found online:
> /* See LICENSE file for copyright and license details. */

/* appearance */
static const char font[]            = "-*-terminus-medium-r-normal-*-14-*-*-*-*-*-*-*";
static const char normbordercolor[] = "#cccccc";
static const char normbgcolor[]     = "#cccccc";
static const char normfgcolor[]     = "#000000";
static const char selbordercolor[]  = "#0066ff";
static const char selbgcolor[]      = "#0066ff";
static const char selfgcolor[]      = "#ffffff";
static unsigned int borderpx        = 1;        /* border pixel of windows */
static unsigned int snap            = 32;       /* snap pixel */
static Bool showbar                 = True;     /* False means no bar */
static Bool topbar                  = True;     /* False means bottom bar */
static Bool usegrab                 = False;    /* True means grabbing the X server
                                                   during mouse-based resizals */

/* tagging */
static const char tags[][MAXTAGLEN] = { "main", "media", "im", "other" };
static unsigned int tagset[] = {1, 1}; /* after start, first tag is selected */

static Rule rules[] = {
	/* class:instance:title regex			tags regex	isfloating */ \
	{ "skype",					"im",		False }, \
	{ "epiphany",					"main",		True }, \
	{ "mrxvt",					"main",		False }, \
	{ "pcmanfm",                                    "main",		False }, \
	{ "gimp",					"media",	False }, \
	{ "vlc",					"media",	True }, \
	{ "gedit",					"main",		False }, \
	{ "gpicview",					"media",	False }, \
	{ "xine",					"media",	True }, \
};

/* layout(s) */
static float mfact      = 0.55; /* factor of master area size [0.05..0.95] */
static Bool resizehints = True; /* False means respect size hints in tiled resizals */

static Layout layouts[] = {
	/* symbol     arrange function */
	{ "|  tile",      tile },    /* first entry is default */
	{ "|  float",      NULL },    /* no layout function means floating behavior */
	{ "|  monocle",      monocle },
};

/* key definitions */
#define MODKEY Mod1Mask
#define TAGKEYS(KEY,TAG) \
	{ MODKEY,                       KEY,      view,           {.ui = 1 << TAG} }, \
	{ MODKEY|ControlMask,           KEY,      toggleview,     {.ui = 1 << TAG} }, \
	{ MODKEY|ShiftMask,             KEY,      tag,            {.ui = 1 << TAG} }, \
	{ MODKEY|ControlMask|ShiftMask, KEY,      toggletag,      {.ui = 1 << TAG} },

/* helper for spawning shell commands in the pre dwm-5.0 fashion */
#define SHCMD(cmd) { .v = (const char*[]){ "/bin/sh", "-c", cmd, NULL } }

/* commands */
static const char *dmenucmd[] = { "dmenu_run", "-fn", font, "-nb", normbgcolor, "-nf", normfgcolor, "-sb", selbgcolor, "-sf", selfgcolor, NULL };
static const char *termcmd[]  = { "exec mrxvt", NULL };

static Key keys[] = {
	/* modifier                     key        function        argument */
	{ MODKEY,                       XK_F3,     spawn,          {.v = dmenucmd } },
	{ MODKEY,                       XK_F2,     spawn,          {.v = termcmd } },
	{ MODKEY,                       XK_b,      togglebar,      {0} },
	{ MODKEY,                       XK_j,      focusstack,     {.i = +1 } },
	{ MODKEY,                       XK_k,      focusstack,     {.i = -1 } },
	{ MODKEY,                       XK_h,      setmfact,       {.f = -0.05} },
	{ MODKEY,                       XK_l,      setmfact,       {.f = +0.05} },
	{ MODKEY,                       XK_Return, zoom,           {0} },
	{ MODKEY,                       XK_Tab,    view,           {0} },
	{ MODKEY,                       XK_F4,     killclient,     {0} },
/*	{ MODKEY,                       XK_t,      setlayout,      {.v = &layouts[0]} },
	{ MODKEY,                       XK_f,      setlayout,      {.v = &layouts[1]} },
	{ MODKEY,                       XK_m,      setlayout,      {.v = &layouts[2]} },*/
	{ MODKEY,                       XK_space,  setlayout,      {0} },
	{ MODKEY|ShiftMask,             XK_space,  togglefloating, {0} },
	{ MODKEY,                       XK_0,      view,           {.ui = ~0 } },
	{ MODKEY|ShiftMask,             XK_0,      tag,            {.ui = ~0 } },
	TAGKEYS(                        XK_1,                      0)
	TAGKEYS(                        XK_2,                      1)
	TAGKEYS(                        XK_3,                      2)
	TAGKEYS(                        XK_4,                      3)
	TAGKEYS(                        XK_5,                      4)
	{ MODKEY|ShiftMask,             XK_q,      quit,           {0} },
};

/* button definitions */
/* click can be a tag number (starting at 0),
 * ClkLtSymbol, ClkStatusText, ClkWinTitle, ClkClientWin, or ClkRootWin */
static Button buttons[] = {
	/* click                event mask      button          function        argument */
	{ ClkLtSymbol,          0,              Button1,        setlayout,      {0} },
	{ ClkLtSymbol,          0,              Button3,        setlayout,      {.v = &layouts[2]} },
	{ ClkWinTitle,          0,              Button2,        zoom,           {0} },
	{ ClkStatusText,        0,              Button2,        spawn,          {.v = termcmd } },
	{ ClkClientWin,         MODKEY,         Button1,        movemouse,      {0} },
	{ ClkClientWin,         MODKEY,         Button2,        togglefloating, {0} },
	{ ClkClientWin,         MODKEY,         Button3,        resizemouse,    {0} },
	{ ClkTagBar,            0,              Button1,        view,           {0} },
	{ ClkTagBar,            0,              Button3,        toggleview,     {0} },
	{ ClkTagBar,            MODKEY,         Button1,        tag,            {0} },
	{ ClkTagBar,            MODKEY,         Button3,        toggletag,      {0} },
};
I guess I can somehow setup keyboard shortcuts to open stuff?  That'd be great if someone could tell/show me how.

Thanks,
tombom:popcorn:

---

### Post by tombom62 on 2009-05-07
anyone?

---

### Post by tombom62 on 2009-05-08
no one knows about dwm?

---

### Post by kaig on 2009-05-16
> **tombom62 said:**
> Hey everyone.  I'm trying DWM.  I have a big enough screen and a slow enough computer :P  I don't really understand the tag system, how to open programs, or anything.  I know about the config.h and here's mine based off some ranodm ones I found online:

I guess I can somehow setup keyboard shortcuts to open stuff?  That'd be great if someone could tell/show me how.

Thanks,
tombom:popcorn:

Search your own config for termcmd and duplicate the corresponding lines with obvious changes.  For example, to start Firefox you would replace termcmd with firefoxcmd and "exec mrxvt" with "exec firefox" and assign a new key.

---

