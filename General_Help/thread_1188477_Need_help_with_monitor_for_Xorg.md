---
title: "Need help with monitor for Xorg"
date: 2009-06-15
forum: General Help
---

### Post by ufly on 2009-06-15
[SIZE=2]Hiya!

I am a new Ubuntu user. I installed Jaunty on my PC last weekend (dual-booted) with XP. I have two problems at the moment. First is that the monitor resolutions don't seem to be set up. My monitor came with my PC with no info at all! Typing xrandr gives the following:

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1280 x 1200
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 337mm x 270mm
   1280x1024      60.0 +   75.0     60.0  
   1024x768       75.0*    75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  

However, some of these resolutions are not supported by my monitor.

The following information is all I have managed to get.

[/SIZE][SIZE=2]Monitor is EM-170 TFT 17 inch.[/SIZE]
 [SIZE=2]The Following are the Product Specifications:[/SIZE]
 [SIZE=2]17 inches Monitor Size[/SIZE]
 [SIZE=2]0.264 mm Dot Pitch[/SIZE]
 [SIZE=2]1280 X 1024 Maximum Monitor Resolution[/SIZE]
 [SIZE=2]Plug & Play[/SIZE]
 [SIZE=2]Flat Screen[/SIZE]
 [SIZE=2]On Screen Display[/SIZE]
 [SIZE=2]522 mm Height[/SIZE]
 [SIZE=2]540 mm Width[/SIZE]
 [SIZE=2]225 mm Depth[/SIZE]
 [SIZE=2]9.5 kg Weight[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]Refresh rate of 75Hz.[/SIZE]
 [SIZE=2]
[/SIZE] [SIZE=2]Using XP, adjusting screen resolution and color quality in Display Properties, the monitor displays the frequencies for each setting:[/SIZE]
 [SIZE=2]
[/SIZE] **[SIZE=2]Resolution:800 by 600 pixels[/SIZE]**
 [SIZE=2]16 bit color; Frequencies: H:37.8KHz V:60.2Hz[/SIZE]
 [SIZE=2]32 bit color; Frequencies: H:37.8KHz V:60.2Hz[/SIZE]
 
 **[SIZE=2]Resolution:1024 by 768 pixels[/SIZE]**
 [SIZE=2]16 bit color; Frequencies: H:48.2KHz V:59.8Hz[/SIZE]
 [SIZE=2]32 bit color; Frequencies: H:48.4KHz V:60.0Hz[/SIZE]
 
 **[SIZE=2]Resolution:1152 by 864 pixels[/SIZE]**
 [SIZE=2]16 bit color; Frequencies: H:53.8KHz V:60.1Hz[/SIZE]
 [SIZE=2]32 bit color; Frequencies: H:53.6KHz V:59.9Hz[/SIZE]
 
 **[SIZE=2]Resolution:1280 by 720 pixels[/SIZE]**
 [SIZE=2]16 bit color; Frequencies: H:44.7KHz V:59.9Hz[/SIZE]
 [SIZE=2]32 bit color; Frequencies: H:44.9KHz V:60.2Hz[/SIZE]
 
 **[SIZE=2]Resolution:1280 by 768 pixels[/SIZE]**
 [SIZE=2]16 bit color; Frequencies: H:44.7KHz V:59.8Hz[/SIZE]
 [SIZE=2]32 bit color; Frequencies: H:44.7KHz V:60.0Hz[/SIZE]
 
 **[SIZE=2]Resolution:1280 by 960 pixels[/SIZE]**
 [SIZE=2]16 bit color; Frequencies: H:59.9KHz V:59.9Hz[/SIZE]
 [SIZE=2]32 bit color; Frequencies: H:59.9KHz V:59.9Hz[/SIZE]
 [SIZE=2]
[/SIZE] **[SIZE=2]Resolution:1280 by 1024 pixels[/SIZE]**
 [SIZE=2]16 bit color; Frequencies: H:64.2KHz V:60.2Hz[/SIZE]
 [SIZE=2]32 bit color; Frequencies: H:63.9KHz V:59.9Hz[/SIZE]
 [SIZE=2]
Now, I need Ubuntu to recognise these modes. Also need to enter the correct HorizSync and VertRefresh values, which I don't have.

[/SIZE][SIZE=2]I am a bit clueless about how to go about this. I have used XF86config many moons ago and Xorg is completely new to me!

Second problem is getting my ATI 9550 card set up, but I will leave that until I get the resolution modes sorted.

Any help appreciated-especially with help finding what I should enter for [/SIZE][SIZE=2]HorizSync and VertRefresh values![/SIZE]

Cheers!

---

### Post by ufly on 2009-06-15
Ok.maybe I jumped the gun a bit here.

I found a program called ddcprobe that gave me the info I needed.

However, it told me that my ATI card is    	 	 	 	 	[SIZE=2]ATI RADEON 9600 PRO rather than 9550!

:confused:
[/SIZE]

---

