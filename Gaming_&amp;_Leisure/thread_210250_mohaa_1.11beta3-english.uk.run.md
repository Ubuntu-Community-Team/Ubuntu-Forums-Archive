---
title: "mohaa_1.11beta3-english.uk.run?"
date: 2006-07-06
forum: Gaming &amp; Leisure
---

### Post by Rackerz on 2006-07-06
How do I install this?

I've tried sudo ./mohaa_1.11beta3-english.uk.run

But that doesn't work :(. And if I try it without sudo it just says permission denied.

---

### Post by Iarwain ben-adar on 2006-07-06
Try 
```
chmod 755 mohaa_1.11beta3-english.uk.run
or sudo chmod 755 mohaa_1.11beta3-english.uk.run
```

I think that's the way to make it executable :D


Iarwain

---

### Post by xarx on 2006-07-06
from my utter ignorance, try
```
sudo chmod +x mohaa_1.11beta3-english.uk.run
sudo ./mohaa_1.11beta3-english.uk.run
```
or
```
sudo sh mohaa_1.11beta3-english.uk.run
```
hope it helps... :)

@larwain ben-adar: i think that that changes file permissions only, but may be wrong!

---

### Post by Iarwain ben-adar on 2006-07-06
Could very well be =)

And i think that i am more likely to be wrond :D


Iarwain

---

