---
title: "Unable to change the resolution of newly connected monitor"
date: 2011-09-15
forum: Desktop Environments
---

### Post by psrdotcom on 2011-09-15
Hi,

I have connected my Ubuntu 11.04 to a monitor with max resolution support 1366x768.

But in Ubuntu it is having maximum of 1024x768.

Please help to change my desktop resolution.

The detect monitor button doesn't have any effect.

---

### Post by FormatSeize on 2011-09-15
When you set the resolution to the maximum setting, what does it look like? My monitor has a max resolution of 1440x900, but the max resolution setting provided in 11.04 works great. I have yet to see an option in any OS that provides the resolution of my specific monitor, but usually the max setting works.

---

### Post by psrdotcom on 2011-09-15
Where I can set the screen resolution to MAX .. In Monitors .. it was displaying only 1024*780 resolution .. There is no option like MAX setting resolution.

Do you need any more inputs?

---

### Post by realzippy on 2011-09-15
Which monitor model is it?
What does 
```
xrandr -q
```
show ?

---

### Post by psrdotcom on 2011-09-16
When I ran the command I got the following output.

$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 410mm x 230mm
   1366x768       59.8 +
   1024x768       75.1     60.0* 
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1

I don't know, how the problem resolved.

I created one user and logged in to that user account. My screen resolution automatically changed.

$ xrandr -q
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 410mm x 230mm
   1366x768       59.8*+
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1

---

