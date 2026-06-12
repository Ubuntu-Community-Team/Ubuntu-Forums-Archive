---
title: "pcsx-df cannot move into medal of honor"
date: 2010-12-18
forum: Gaming &amp; Leisure
---

### Post by honeybear on 2010-12-18
Into underground , all keys are working but not the move to walk

here is my dfinput.cfg

> 
[general]
pcsx_style      = 1
use_threads     = 1
use_analog      = 0
[pad 1]
devicefilename  = /dev/input/js0
minzero = -250
maxzero = 250
event_l2       = A0P4+
event_r2       = A0P5-
event_l1       = B0P4
event_r1       = B0P5
event_triangle = B0P3
event_circle   = B0P1
event_cross    = B0P0
event_square   = B0P2
event_select   = B0P14
event_lanalog  = ???
event_ranalog  = ???
event_start    = B0P6
event_up       = B0P10
event_right    = B0P13
event_down     = B0P11
event_left     = B0P12
event_lanax    = ???
event_lanay    = X0P3v0
event_ranax    = ???
event_ranay    = ???
[macro 1]
event_launch  = ???
events        =
interval      =
[macro 2]
event_launch  = ???
events        =
interval      =
[macro 3]
event_launch  = ???
events        =
interval      =
[pad 2]
devicefilename  = /dev/input/js1
minzero = -250
maxzero = 250
event_l2       = A1P2-
event_r2       = A1P5-
event_l1       = B1P4
event_r1       = B1P5
event_triangle = B1P3
event_circle   = B1P1
event_cross    = B1P0
event_square   = B1P2
event_select   = A1P0-
event_lanalog  = ???
event_ranalog  = ???
event_start    = B1P6
event_up       = B1P10
event_right    = B1P13
event_down     = B1P11
event_left     = B1P12
event_lanax    = ???
event_lanay    = ???
event_ranax    = ???
event_ranay    = ???
[macro 1]
event_launch  = ???
events        =
interval      =
[macro 2]
event_launch  = ???
events        =
interval      =
[macro 3]
event_launch  = ???
events        =
interval      =




---

### Post by honeybear on 2010-12-18
I got it wokring !! now the dfinput.cfg looks like this and it works !!

```
[general]
pcsx_style      = 1
use_threads     = 1
use_analog      = 0
[pad 1]
devicefilename  = /dev/input/js0
minzero = -250
maxzero = 250
event_l2       = 
event_r2       = 
event_l1       = B0P4
event_r1       = B0P5
event_triangle = B0P3
event_circle   = B0P1
event_cross    = B0P0
event_square   = B0P2
event_select   = B0P14
event_lanalog  = 
event_ranalog  = 
event_start    = B0P6
event_up       = B0P10
event_right    = B0P13
event_down     = B0P11
event_left     = B0P12
event_lanax    = 
event_lanay    = 
event_ranax    = A0P4+
event_ranay    = A0P5-
[macro 1]
event_launch  = 
events        =
interval      =
[macro 2]
event_launch  = 
events        =
interval      =
[macro 3]
event_launch  =
events        =
interval      =
[pad 2]
devicefilename  = /dev/input/js1
minzero = -250
maxzero = 250
event_l2       = A1P2-
event_r2       = A1P5-
event_l1       = B1P4
event_r1       = B1P5
event_triangle = B1P3
event_circle   = B1P1
event_cross    = B1P0
event_square   = B1P2
event_select   = A1P0-
event_lanalog  = ???
event_ranalog  = ???
event_start    = B1P6
event_up       = B1P10
event_right    = B1P13
event_down     = B1P11
event_left     = B1P12
event_lanax    = ???
event_lanay    = ???
event_ranax    = ???
event_ranay    = ???
[macro 1]
event_launch  = ???
events        =
interval      =
[macro 2]
event_launch  = ???
events        =
interval      =
[macro 3]
event_launch  = ???
events        =
interval      =

```

---

