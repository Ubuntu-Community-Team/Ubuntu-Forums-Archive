---
title: "May Be Time To Get A New Video Card??????"
date: 2009-06-05
forum: General Help
---

### Post by Spaceman9 on 2009-06-05
I have an ATI ALL-IN-WONDER 128 PRO, AGP 4x, made in 2000. I was able to set the res for 1280 x 1024 in Ubuntu 8.04 but not in 9.04. 

I don't want to buy a whole new computer just to keep using Ubuntu. That's too much like the bad old days when I used Windows. 

What is the oldest ATI card Ubuntu will support now at 1280 x 1024? Thanks for any help.


I included this stuff below in case anyone knows how to do 1280 x 1024 with an old ATI card.

I ran this "lspci -nn | grep VGA"

and I got this:

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS [1002:5046]

---

### Post by overdrank on 2009-06-05
I have a laptop with the ATI 7500 and it works good. It does not work like my new laptop with the Nvidia 8200 m but I watch video's and it does run the visual effects. :)

---

### Post by Spaceman9 on 2009-06-05
But can they do 1280 x 1024? It's things like this that make PCLOS look pretty good.

---

### Post by overdrank on 2009-06-05
> **Spaceman9 said:**
> But can they do 1280 x 1024? It's things like this that make PCLOS look pretty good.

On my ATI laptop I can reach 1400 x 1050 :) with Jaunty

---

### Post by Spaceman9 on 2009-06-05
> **overdrank said:**
> On my ATI laptop I can reach 1400 x 1050 :) with Jaunty

Ok, good. Then may be a 9500 would keep me safe for a while. May be a few years anyway.

---

### Post by Youresorock on 2009-06-05
If 8.10 could do it, 9.04 should be able to as well.  What driver are you using?  9.04 may have defaulted to a newer driver that is less compatible.

Also, how much video memory does that card have?  
("lspci -v" will tell you.)

---

### Post by Spaceman9 on 2009-06-05
All I know is the ATI driver in 1.6 xorg in Ubuntu 9.04 is new. 1.4 was in 8.04. The old driver I need just isn't there anymore.

My card has 32 megs of memory and it's AGP 4x. The problem is getting to 1280 x 1024. I tried using Envy and it showed none of the new drivers can be used with my video card.

I have no problems doing 1280 x 1024 in PCLOS and Puppy Linux. May be they still use the old ATI driver.

---

