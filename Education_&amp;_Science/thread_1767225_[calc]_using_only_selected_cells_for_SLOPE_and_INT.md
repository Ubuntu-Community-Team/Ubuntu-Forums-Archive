---
title: "[calc]: using only selected cells for SLOPE and INTERCEPT"
date: 2011-05-25
forum: Education &amp; Science
---

### Post by R33D3M33R on 2011-05-25
I have cells from A1:A20 and B1:B20. A's are the X values and B's the Y values. I would like to do a linear regression on some of the points and ignore others. For example: I'm interested in SLOPE and INTERCEPT value of points A2:B2, A3:B3, A4:B4 and A6:B6. I have not found a way yet to do this. Here are some examples that don't work (SLOPE):
 
```

SLOPE(B2:B4,B6;A2:A4,A6)
SLOPE("B2:B4","B6","A2:A4","A6")
SLOPE("B2:B4,B6","A2:A4,A6")
SLOPE("B2:B4"&"B6","A2:A4"&"A6")
SLOPE(B2:B4&B6,A2:A4&A6)
SLOPE("B2:B4&B6","A2:A4&A6")
SLOPE("B2:B4;B6","A2:A4;A6")
```And so on. Any ideas? Thank you for your help in advance!

---

