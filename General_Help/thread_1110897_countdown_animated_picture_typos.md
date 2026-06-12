---
title: "countdown animated picture typos"
date: 2009-03-30
forum: General Help
---

### Post by Dayofswords on 2009-03-30
sorry if this is the wrong place, there is like 2000 forums


i was looking at the animated picure of the countdown noticed on the frame showing the dates at the said as an alt text "frame 6"

found this in the [http://www.ubuntu.com/files/countdown/904/countdown-9.04-1/countdown.html](http://www.ubuntu.com/files/countdown/904/countdown-9.04-1/countdown.html)

```
<li><img src="1_desktop.png" alt="For your desktop" /></li>
		<li><img src="2_laptop.png" alt="For your laptop" /></li>
		<li><img src="3_netbook.png" alt="For your netbook" /></li> 
		<li><img src="4_server.png" alt="For your server" /></li>
		<li><img src="5_cloud.png" alt="In the cloud" /></li>
		<li><script type="text/javascript">document.write('<img src="'+days+'.png" alt="Frame 6">');</script></li>
		<noscript><li><img src="00.png" alt="Frame 6" alt="Ubuntu 9.04: Coming soon"/></li></noscript>
```

2 alts at the end plus there is this "...+days+'.png" alt="Frame 6">, should be replace  with the "Ubuntu 9.04: Coming soon" 

with the alts at the end in noscript, its going with the first which is "frame 6", must have been left there during the html writing

---

