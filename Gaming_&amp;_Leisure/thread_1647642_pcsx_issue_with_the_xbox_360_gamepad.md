---
title: "pcsx issue with the xbox 360 gamepad?"
date: 2010-12-17
forum: Gaming &amp; Leisure
---

### Post by honeybear on 2010-12-17
Hi

I would like to have the left stick working but it is ultra too sensible. 

For the moment I have : dfinput.cfg
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


How to fix that please ?

---

