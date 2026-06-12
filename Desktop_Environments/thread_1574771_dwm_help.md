---
title: "dwm help"
date: 2010-09-14
forum: Desktop Environments
---

### Post by finzxz on 2010-09-14
So I just installed DWM and I'm using xinitrc and config.def.h files I found around the web.

I have a list of things that aren't working and that I'd like fixed so I'd appreciate any help I get.

here is a screen cap of my desktop
[http://ompldr.org/vNWpqYQ](http://ompldr.org/vNWpqYQ)


things i'd liked to work:
-Make feh remember my desktop background so I don't have to change it each time I log in
-have a clock in the panel at the bottom
-customize the GTX2 theme colours. i'm using LXAppearance and it doesn't have the option to change window colours.
-change the way DWM tiles windows. right now it tiles the main window horizontally across the screen, i'd rather it tiled it vertically.
-conky doesn't start on start up, pretty much nothing does.

here are my config files.
xinitrc
```
#!/bin/sh
#
# ~/.xinitrc

setxkbmap -option terminate:ctrl_alt_bksp &
eval `cat /home/fin/.fehbg` &
numlockx &
xscreensaver -no-splash &

# Dzen & conky
(sleep 15s && conky | dzen2 -x '500' -e '' -fg '#dcdcdc' -bg '#3f3f3f' -w '650' -ta r -fn '-*-terminus-*-r-normal-*-*-120-*-*-*-*-iso8859-*' -p ) &

# Start dwm
exec ck-launch-session
```.conkyrc
```
background no
out_to_console yes
update_interval 2
total_run_times 0
use_spacer none
double_buffer yes
TEXT
${if_existing /sys/class/power_supply/BAT0/present}^fg(#999999)BAT^fg()${battery_percent}%${else}AC${endif} * CPU ${cpu cpu1}%  RAM ${memperc}% * / ${fs_used_perc /}%  /home ${fs_used_perc /home}% * PKG ${execpi 900 ~/Scripts/pacman-up.pl} * ${if_existing /proc/net/route ra0}Down ${downspeedf ra0}K/s Up ${upspeedf ra0}K/s ${else} ${if_existing /proc/net/route eth0} Down ${downspeedf ra0}K/s Up ${upspeedf ra0}K/s${endif} ${endif}* ${time %I:%M%P}
```config.def.h
```
/* See LICENSE file for copyright and license details. */

/* appearance */
static const char font[]            = "-*-terminus-medium-r-*-*-16-*-*-*-*-*-*-*";
static const char normbordercolor[] = "#cccccc";
static const char normbgcolor[]     = "#cccccc";
static const char normfgcolor[]     = "#000000";
static const char selbordercolor[]  = "#0066ff";
static const char selbgcolor[]      = "#0066ff";
static const char selfgcolor[]      = "#ffffff";
static const unsigned int borderpx  = 1;        /* border pixel of windows */
static const unsigned int snap      = 32;       /* snap pixel */
static const Bool showbar           = True;     /* False means no bar */
static const Bool topbar            = True;     /* False means bottom bar */

/* tagging */
static const char *tags[] = { "1", "2", "3", "4", "5", "6", "7", "8", "9" };

static const Rule rules[] = {
    /* class      instance    title       tags mask     isfloating   monitor */
    { "Gimp",     NULL,       NULL,       0,            True,        -1 },
    { "Firefox",  NULL,       NULL,       1 << 8,       False,       -1 },
};

/* layout(s) */
static const float mfact      = 0.55; /* factor of master area size [0.05..0.95] */
static const Bool resizehints = True; /* True means respect size hints in tiled resizals */

static const Layout layouts[] = {
    /* symbol     arrange function */
    { "[]=",      tile },    /* first entry is default */
    { "><>",      NULL },    /* no layout function means floating behavior */
    { "[M]",      monocle },
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
static const char *termcmd[]  = { "uxterm", NULL };

static Key keys[] = {
    { MODKEY,            XK_F10,        spawn,        {.v = volupcmd } },
    { MODKEY,            XK_F11,        spawn,        {.v = voldowncmd } },
    { MODKEY,            XK_F12,        spawn,        {.v = mutecmd } },
    { MODKEY,            XK_m,        spawn,        {.v = dmenucmd } },
    { MODKEY,            XK_Return,    spawn,          "exec gnome-terminal" }, \
    { MODKEY,            XK_f,        spawn,        "exec firefox" }, \
    { MODKEY,            XK_p,        spawn,        "exe=`dmenu_path | dmenu` && exec &exe" }, \
    { MODKEY,            XK_b,        togglebar,      {0} },
    { MODKEY,                       XK_j,        focusstack,     {.i = +1 } },
    { MODKEY,                       XK_k,        focusstack,     {.i = -1 } },
    { MODKEY,                       XK_h,        setmfact,       {.f = -0.05} },
    { MODKEY,                       XK_l,        setmfact,       {.f = +0.05} },
    { MODKEY,                       XK_Return,    zoom,           {0} },
    { MODKEY,                       XK_Tab,        view,           {0} },
    { MODKEY|ShiftMask,             XK_c,        killclient,     {0} },
    { MODKEY,                       XK_t,        setlayout,      {.v = &layouts[0]} },
    { MODKEY,                       XK_f,        setlayout,      {.v = &layouts[1]} },
    { MODKEY,                       XK_q,        setlayout,      {.v = &layouts[2]} },
    { MODKEY,                       XK_e,        setlayout,      {.v = &layouts[3]} },
    { MODKEY|ShiftMask,        XK_d,        setlayout,      {.v = &layouts[4]} },
    { MODKEY,                       XK_space,    setlayout,      {0} },
    { MODKEY|ShiftMask,             XK_space,    togglefloating, {0} },
    { MODKEY,                       XK_0,        view,           {.ui = ~0 } },
    { MODKEY|ShiftMask,             XK_0,        tag,            {.ui = ~0 } },
    { MODKEY,                       XK_comma,    focusmon,       {.i = -1 } },
    { MODKEY,                       XK_period,    focusmon,       {.i = +1 } },
    { MODKEY|ShiftMask,             XK_comma,    tagmon,         {.i = -1 } },
    { MODKEY|ShiftMask,             XK_period,    tagmon,         {.i = +1 } },
    { MODKEY|ShiftMask,        XK_q,        quit,        {0} },
    { MODKEY,            XK_Down,    spawn,        {.v = mpcpause } },
    { MODKEY,            XK_Up,        spawn,        {.v = mpcplay } },
    { MODKEY,            XK_Right,    spawn,        {.v = mpcnext } },
    { MODKEY,            XK_Left,    spawn,        {.v = mpcprev } },
    { MODKEY|ControlMask,        XK_j,        pushdown,    {0} },
    { MODKEY|ControlMask,        XK_k,        pushup,        {0} },
    TAGKEYS(                    XK_1,        0)
    TAGKEYS(                    XK_2,        1)
    TAGKEYS(                    XK_3,        2)
    TAGKEYS(                    XK_4,        3)
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

```.fehbg
```
feh --bg-scale '/home/fin/Pictures/dark_striped.png'
```i appreciate any help i get. i'm pretty sure most of my files need a huge over haul.

---

### Post by AllRadioisDead on 2010-09-27
Most of your questions can be answered here: [http://wiki.archlinux.org/index.php/Dwm](http://wiki.archlinux.org/index.php/Dwm)
For additional tiling modes, check the patches available at [http://dwm.suckless.org](http://dwm.suckless.org)
Also, for your wallpaper issue I would recommend using Nitrogen instead (It's available in the Repo's) because I believe feh has been abandoned since 2006.
Simply add Nitrogen to your startup script: 
```

nitrogen -r

```It should restore the background you set in your last session.

---

### Post by UnsafeData on 2013-01-27
I'm bumping this thread since dwm has changed. The Arch wiki mentions that 'horizontal' is the default, so I don't know what else to do to get this to be vertical. :neutral:	

Anyone have any ideas?

---

