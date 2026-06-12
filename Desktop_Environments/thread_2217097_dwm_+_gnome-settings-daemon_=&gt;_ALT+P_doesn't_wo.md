---
title: "dwm + gnome-settings-daemon =&gt; ALT+P doesn't work"
date: 2014-04-15
forum: Desktop Environments
---

### Post by vajorie on 2014-04-15
I was hoping someone could point me in the right direction. 

I installed dwm and have it spawn thru my .xsession file. However, if I include gnome-settings-daemon to launch, the ALT+P shortcut (to launch dmenu_run) stops working. The screen flashes when I ALT+P but nothing comes up. This occurs **until I switch to another tty and back to the desktop (ie CTRL+ALT+F1, then CTRL+ALT+F7)**, after which point ALT+P continues working as expected. 

Below are all my configurations files: 

/usr/share/xsession/dwm.desktop
```

[Desktop Entry]
Encoding=UTF-8
Name=Dwm
Comment=Dynamic window manager
Exec=/etc/X11/Xsession
Icon=dwm
Type=XSession

```

~/.xsession

```

#!/usr/bin/env bash

# All the startup applications here

while true; do
   xsetroot -name "$( date +"%F %a %R" )"
   sleep 1m    # Update time every minute
done &

feh --bg-scale ~/desktop_background.jpg &

trayer --widthtype request --align right --edge top --height 16 --transparent true --alpha 0 --tint 0x0B0B0B --margin 0 --distancefrom right --distance 130 &

nm-applet &

# From the Unity startup app pref:

/usr/lib/at-spi2-core/at-spi-bus-launcher --launch-immediately &
/usr/bin/gnome-keyring-daemon --start --components=pkcs11 &
/usr/lib/gnome-disk-utility/gdu-notification-daemon &

/usr/bin/dropbox start -i &

#/usr/lib/gnome-settings-daemon/gnome-settings-daemon &  #<== Offending line, dmenu works if this is commented out
/usr/bin/gnome-keyring-daemon --start --components=gpg &

/usr/bin/indicator-multiload &

/usr/lib/gnome-settings-daemon/gnome-fallback-mount-helper &

/bin/mount Media &
/home/mehmet/bin/start-localhost-mpd &

/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &
/usr/bin/start-pulseaudio-x11 &
/usr/bin/gnome-screensaver &
/usr/bin/gnome-keyring-daemon --start --components=secrets &
/usr/bin/gnome-keyring-daemon --start --components=ssh &
/usr/bin/zeitgeist-datahub &

#exec dwm  
dbus-launch --exit-with-session dwm  # using either this or the above line doesn't make a difference. also I have no idea what the difference is...

```

dwm's config.h (includes bottom stack patch + keyboard shortcut for it + setting it as default + other changes)

```

/* See LICENSE file for copyright and license details. */

/* appearance */
static const char font[]            = "-*-terminus-medium-r-*-*-16-*-*-*-*-*-*-*";
static const char normbordercolor[] = "#2D2D2D";
static const char normbgcolor[]     = "#2D2D2D";
static const char normfgcolor[]     = "#CCCCCC";
static const char selbordercolor[]  = "#CCCCCC";
static const char selbgcolor[]      = "#4C4C4C";
static const char selfgcolor[]      = "#CCCCCC";
static const unsigned int borderpx  = 0;        /* border pixel of windows */
static const unsigned int snap      = 32;       /* snap pixel */
static const Bool showbar           = True;     /* False means no bar */
static const Bool topbar            = True;     /* False means bottom bar */

/* tagging */
static const char *tags[] = { "1", "2", "3", "4", "5", "6", "7", "8", "9" };

static const Rule rules[] = {
	/* class      instance    title       tags mask     isfloating   monitor */
	{ "Gimp",     NULL,       NULL,       0,            True,        -1 },
};

/* layout(s) */
static const float mfact      = 0.55; /* factor of master area size [0.05..0.95] */
static const int nmaster      = 1;    /* number of clients in master area */
static const Bool resizehints = True; /* True means respect size hints in tiled resizals */

#include "bstack.c"
#include "bstackhoriz.c"
static const Layout layouts[] = {
	/* symbol     arrange function */
	{ "BOTTOM",      bstack },    /* first entry is default */
	{ "TILE",      tile },
	{ "BOTTOMH",      bstackhoriz },
	{ "FLOAT",      NULL },    /* no layout function means floating behavior */
	{ "MONOCLE",      monocle },
};

/* key definitions */
#define MODKEY Mod4Mask /* was Mod1Mask which is left ALT key */
#define TAGKEYS(KEY,TAG) \
	{ MODKEY,                       KEY,      view,           {.ui = 1 << TAG} }, \
	{ MODKEY|ControlMask,           KEY,      toggleview,     {.ui = 1 << TAG} }, \
	{ MODKEY|ShiftMask,             KEY,      tag,            {.ui = 1 << TAG} }, \
	{ MODKEY|ControlMask|ShiftMask, KEY,      toggletag,      {.ui = 1 << TAG} },

/* helper for spawning shell commands in the pre dwm-5.0 fashion */
#define SHCMD(cmd) { .v = (const char*[]){ "/bin/sh", "-c", cmd, NULL } }

/* commands */
static const char *dmenucmd[] = { "dmenu_run", "-fn", font, "-nb", normbgcolor, "-nf", normfgcolor, "-sb", selbgcolor, "-sf", selfgcolor, NULL };
static const char *termcmd[]  = { "gnome-terminal", NULL };
static const char *lockcmd[]  = { "gnome-screensaver-command", "-a", NULL };

static Key keys[] = {
	/* modifier                     key        function        argument */
	{ MODKEY,                       XK_p,      spawn,          {.v = dmenucmd } },
	{ MODKEY|ShiftMask,             XK_Return, spawn,          {.v = termcmd } },
	{ MODKEY|ControlMask,           XK_l,      spawn,          {.v = lockcmd } },
	{ MODKEY,                       XK_j,      focusstack,     {.i = +1 } },
	{ MODKEY,                       XK_k,      focusstack,     {.i = -1 } },
	{ MODKEY,                       XK_i,      incnmaster,     {.i = +1 } },
	{ MODKEY,                       XK_d,      incnmaster,     {.i = -1 } },
	{ MODKEY,                       XK_h,      setmfact,       {.f = -0.05} },
	{ MODKEY,                       XK_l,      setmfact,       {.f = +0.05} },
	{ MODKEY,                       XK_Return, zoom,           {0} },
	{ MODKEY,                       XK_Tab,    view,           {0} },
	{ MODKEY|ShiftMask,             XK_c,      killclient,     {0} },
	{ MODKEY,                       XK_b,      setlayout,      {.v = &layouts[0]} },
	{ MODKEY,                       XK_t,      setlayout,      {.v = &layouts[1]} },
	{ MODKEY,                       XK_f,      setlayout,      {.v = &layouts[3]} },
	{ MODKEY,                       XK_m,      setlayout,      {.v = &layouts[4]} },
	{ MODKEY,                       XK_space,  setlayout,      {0} },
	{ MODKEY|ShiftMask,             XK_space,  togglefloating, {0} },
	{ MODKEY,                       XK_0,      view,           {.ui = ~0 } },
	{ MODKEY|ShiftMask,             XK_0,      tag,            {.ui = ~0 } },
	{ MODKEY,                       XK_comma,  focusmon,       {.i = -1 } },
	{ MODKEY,                       XK_period, focusmon,       {.i = +1 } },
	{ MODKEY|ShiftMask,             XK_comma,  tagmon,         {.i = -1 } },
	{ MODKEY|ShiftMask,             XK_period, tagmon,         {.i = +1 } },
	TAGKEYS(                        XK_1,                      0)
	TAGKEYS(                        XK_2,                      1)
	TAGKEYS(                        XK_3,                      2)
	TAGKEYS(                        XK_4,                      3)
	TAGKEYS(                        XK_5,                      4)
	TAGKEYS(                        XK_6,                      5)
	TAGKEYS(                        XK_7,                      6)
	TAGKEYS(                        XK_8,                      7)
	TAGKEYS(                        XK_9,                      8)
	{ MODKEY|ShiftMask,             XK_q,      quit,           {0} },
};

/* button definitions */
/* click can be ClkLtSymbol, ClkStatusText, ClkWinTitle, ClkClientWin, or ClkRootWin */
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

```

---

