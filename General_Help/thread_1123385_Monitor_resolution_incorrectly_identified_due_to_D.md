---
title: "Monitor resolution incorrectly identified due to DVI &gt; VGA adaptor"
date: 2009-04-12
forum: General Help
---

### Post by tekp2 on 2009-04-12
Hello,

I recently put 8.10 on a machine I'm planning to use as a media centre. It's a small form-factor machine based on an AOpen i945GMt-FSA mini-ITX board, which only has a DVI monitor output. I'm using the DVI>VGA adaptor that came with the board to connect this to a LG L1960TR monitor.

The problem I have is that Ubuntu appears to detect the DVI adaptor and the Monitor itself as two separate devices. If I do xrandr after booting the system, I get:

```
tom@tekp3:~$ xrandr
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1280 x 1024
VGA connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS-1 connected 1152x864+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0 +   75.0     60.0     60.0  
   1280x960       60.0  
   1152x864       75.0     75.0     70.0     60.0* 
   1024x768       75.0     75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     75.0     60.3     56.2  
   640x480        75.0     72.8     75.0     75.0     60.0     59.9  
   720x400        70.1  

```

The native resolution of the screen is 1280x1024, so I do:

```
tom@tekp3:~$ xrandr --output TMDS-1 --off
tom@tekp3:~$ xrandr
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1280 x 1024
VGA connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS-1 connected (normal left inverted right x axis y axis)
   1280x1024      60.0 +   75.0     60.0     60.0  
   1280x960       60.0  
   1152x864       75.0     75.0     70.0     60.0  
   1024x768       75.0     75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     75.0     60.3     56.2  
   640x480        75.0     72.8     75.0     75.0     60.0     59.9  
   720x400        70.1  
TV disconnected (normal left inverted right x axis y axis)
tom@tekp3:~$ xrandr --output VGA --mode 1280x1024
xrandr: cannot find mode 1280x1024
tom@tekp3:~$ xrandr --addmode VGA 1280x1024
tom@tekp3:~$ xrandr --output VGA --mode 1280x1024

```

And that gets the screen back to native resolution. The "Monitor Resolution Settings" widget then shows the monitor detected as LG Electronics 19" as switched off, and "Unknown" as running at the desired resolution.

What do I do to make this change "sticky" between reboots? Should I file a bug report somewhere?

Many thanks in advance for your help, and to all involved for building Ubuntu.

-tom

---

