---
title: "Conky + else"
date: 2009-05-05
forum: General Help
---

### Post by iamallama on 2009-05-05
```

   ${if_existing /proc/net/route eth0}
		${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth0}
		${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth0} Kb/s 
		${upspeedgraph eth0 20,140 000000 ffffff}
		  
		${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth0}
		${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth0} Kb/s 
		${downspeedgraph eth0 20,140 000000 ffffff}	
   ${else}
   ${if_existing /proc/net/route wlan0}
		${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup wlan0}
		${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed wlan0} Kb/s 
		${upspeedgraph wlan0 20,140 000000 ffffff}
		  
		${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown wlan0}
		${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed wlan0} Kb/s 
		${downspeedgraph wlan0 20,140 000000 ffffff}
   ${endif}


```

What i wanted was if eth0 was up then it would just show that information even if wlan0 was up aswell. But when i have both wlan0 and eth0 up it shows both. I thought it would stop after eth0 was detected as up. Could someone help me fix this :)

Thanks

---

### Post by phinullfermata on 2009-05-05
try putting two ${endif} 's at the end, see if that works

---

