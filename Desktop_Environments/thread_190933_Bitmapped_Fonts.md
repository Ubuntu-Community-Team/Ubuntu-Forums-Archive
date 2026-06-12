---
title: "Bitmapped Fonts"
date: 2006-06-06
forum: Desktop Environments
---

### Post by JAW on 2006-06-06
Is there any reason why the Bitmapped fonts are not available for selection in the System->Preferences->Fonts config?  I don't see the harm in including both Scalable and Bitmapped types, and personally I much prefer the look of non-antialised bitmapped fonts compared to the blurry scalable anti-aliased fonts. 

After some searching I found i had to run;

sudo dpkg-reconfigure fontconfig

and then tell it to install Bitmapped fontsets.

I then went into System->Preferences->Fonts and was able to choose Helvetica with Courier as my fixed width font, and now all my Ubunto menus and apps look crisp and clean... mmmmm... :-)

Although it turned out to be trivial to get the fonts enabled (as above) I don't see why they are not available as standard?


Thanks,
James


My Desktop with lovely clear fonts!!!

[http://www.jigsawdezign.com/images/Screenshot.png](http://www.jigsawdezign.com/images/Screenshot.png)

---

