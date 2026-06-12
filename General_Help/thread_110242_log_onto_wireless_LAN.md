---
title: "log onto wireless LAN"
date: 2005-12-30
forum: General Help
---

### Post by shoshu on 2005-12-30
well...I want to log onto wireless LAN. I have some questions.
I key in "iwlist" and see many parameters of different APs.
But I don't know how to choose the AP which has the best quality base on 
these parameters.
1.what does  "Last beacon" mean?
2.there's a parmeter "quality", does the AP with the highest number means 
that it has best quality? What does it mean? 
3.Is there any other command I can use to know which AP has the best quality?
thanks a lot:) !

---

### Post by 0MG on 2005-12-30
Running an iwlist scan will give you a lot of info, some of it you don't really need if you just want to find out which AP will give you the best connection.

What you want to look for is the Signal Level rating. Anything stronger than -70 dBm (closer to 0) will give you a decent connection as long as the noise level is low. Since these are negative numbers, -60 is stronger than -80. 

If you are right on top of an AP, it will give you a reading in the area of -30 dBm. As these numbers get further from 0, the signal starts to degrade. You can still get a connection in the -80 dBm range, but you might get a lot of packet loss. 

Basically, look for the strongest signal level. Quality is a good indicator of signal:noise ratio also.

---

