---
title: "How to change date format in Ubuntu v12.04??"
date: 2016-03-04
forum: Desktop Environments
---

### Post by martin172 on 2016-03-04
Almost all of my applications display the date with the year as only 2 digits.  The only one that displays a 4-digit year is (so far) Nautilus.  How can I change the format generally to be a 4-digit year?  (I would upgrade to v14 but it won't run nicely on my hardware, HP Elite 8000.)  Thanks for any help. 
... Martin

---

### Post by mörgæs on 2016-03-04
When you say

> **martin172 said:**
>  v14 won't run nicely on my hardware, HP Elite 8000.

does that also apply to X/Lubuntu?

---

### Post by martin172 on 2016-03-04
No, I haven't tried X/Lubuntu.  Would it make a difference?  I have been using Linux off and on since the heyday of Mandrake and can't recall any distro I have used that defaulted to a 2-digit year.  A 4-digit year is so logical and helps one to tell which end of the date format is which, if you know what I mean.  A 2-digit year invites Y2K-like problems.  Is there any way to change it?

---

### Post by slickymaster on 2016-03-04
The time format is dependent on your **locale**, which is a regional setting you can change, but not all programs in Ubuntu will show the date in the same format.

You can usse **dconf-editor** to use a custom format. It's part of the package dconf-tools, which you'd need to install first by running```
sudo apt-get install dconf-tools
```

---

### Post by martin172 on 2016-03-04
Thanks, Slickymaster.  I have tinkered with the region settings and found a combination that at least gives me dd-mm-yy date order, which is more familiar to me.  But it appears there is no combination that has a 4-digit year format.  So I have dconf-editor running now and will figure out what needs changing there.  :-)  Thanks very much and I think you have put me on the right track.  
... Martin

---

### Post by martin172 on 2016-03-05
Well, there seems to be no way to display the year as 4 digits as a default in all applications in Ubuntu v12.04.  I have got the date order as dd-mm-yy which is easier for my brain to "read" than yy-mm-dd (I know, it is "illogical") but the year remains as yy instead of yyyy.  The solution, if any, must be deeper than can be reached using dconf-editor.  If anyone knows a trick that will solve this ...  otherwise, I am resigning myself to the yy "and all that that entails".   ... Martin

---

### Post by mörgæs on 2016-03-07
> **martin172 said:**
> No, I haven't tried X/Lubuntu.  Would it make a difference?
Yes, if speed is what keeps you away from 14.04.

My Lubuntu has dd-mm-yyyy by default.

---

### Post by martin172 on 2016-03-07
Thanks,  mörgæs, this little problem does bug and I will certainly consider switching as you suggest .  I hadn't bothered to check out Lubuntu until you mentioned it.  Thanks for the tip.     ... Martin

---

