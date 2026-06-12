---
title: "Fesity Compiz &amp; Integrated VIA S3 KM400"
date: 2007-05-15
forum: Desktop Effects &amp; Customization
---

### Post by happybrick on 2007-05-15
I have integrated graphics as above but cannot get desktop effects to work. I receive the error "Desktop Effects Could Not Be Enabled".

glxinfo output indicates direct rendering is set to yes.

I've had a look around forums but haven't been able to find a solution. I know that Desktop Effects is experimental but it'd be nice if I could get them to work.

Anyone have any suggestions?

I'm new to linux so please be explicit if giving instructions. :)

---

### Post by abhaysahai on 2007-08-09
I have the same problem. 
My card is also Via KM400. I have checked that I already have unichrome drivers installed and 
" glxinfo | grep render" 
shows that direct rendering is enabled. 
Any help ?

---

### Post by psyopper on 2007-08-09
I poked around on VIA's website [here]("http://www.via.com.tw/en/products/chipsets/k7-series/km400/") and [here]("http://www.via.com.tw/en/resources/pressroom/2003_archive/pr030410km400.jsp")

Beryl/Compiz et al require per-pixel shading to function. I couldn't find a reference to the VIA Unichrome VGA adapter supporting per pixel shading. This may be the problem.

---

### Post by abhaysahai on 2007-08-14
Thanks for giving some more details.
I think we are stuck till we get better drivers, as this same card works perfectly with its windows drivers and give good results. They produce decent eye candy with windows blinds.

---

