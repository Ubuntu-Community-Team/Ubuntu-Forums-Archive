---
title: "move Maximize,Minimize,Close to right side?"
date: 2010-03-07
forum: Desktop Environments
---

### Post by Zaphrod on 2010-03-07
Hi,

I have been trying to get the window buttons moved back to the right side since the last update but they won't move. I have changed the button layout settings in gconf-editor to menu:minimize,maximize,close but it doesn't work, I have rebooted and checked the settings have remained as I set them and they do but the buttons stubbornly stay on the left. I have tried running gconf-editor with and without gksudo.

Any Ideas?

---

### Post by nilarimogard on 2010-03-07
":minimize,maximize,close" will give you a broken metacity because of the border around the maximize button. So you must put the maximize before minimize. Still, it should have worked anyway.

Try running this in a terminal and see if anything changes:
```
gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:maximize,minimize,close"
```

---

### Post by Zaphrod on 2010-03-07
That did the trick thanks very much.

---

### Post by kastlemaster on 2010-03-07
Thanks, that worked very well. :popcorn:

Ubuntu 10.4 amd64

---

### Post by RedG on 2010-03-26
Thanks!
I had the colon on the wrong side of the list of bottons.
ie.
was
/apps/metacity/general/button_layout "maximize,minimize,spacer,close:"
when corrected
/apps/metacity/general/button_layout ":maximize,minimize,spacer,close"

---

### Post by nilarimogard on 2010-03-26
The latest version of the themes also supports :minimize,maximize,close ... finally!

---

### Post by plapczynski on 2010-04-09
Thanks!  That was driving me nuts!

---

### Post by superstargoddess on 2010-04-10
Awesome, thanks!  This was just what I was looking for!  I can't stand that stuff being on the left side!

---

### Post by Mies on 2010-04-29
Thanks, drove me mental as well.

---

### Post by vittalp88 on 2010-05-03
Thank you.

---

### Post by jahn surf irie on 2010-05-03
nilarimogard > thanks much, that was driving me nuts as well!!  :D

---

### Post by thefallofroy on 2010-06-21
Thanks a million nilarimogard!

---

### Post by felixq78 on 2011-06-09
> **nilarimogard said:**
> ":minimize,maximize,close" will give you a broken metacity because of the border around the maximize button. So you must put the maximize before minimize. Still, it should have worked anyway.

Try running this in a terminal and see if anything changes:
```
gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:maximize,minimize,close"
```

And a thank you from me as well.
Cheers

---

### Post by emma00 on 2011-06-09
My minimize,maximize and close has gone after changing some compiz settings i have unchecked them but these are not coming back for any menu any suggestion????

---

### Post by Copper Bezel on 2011-06-09
Are the buttons gone, or is the entire title bar gone?

---

### Post by emma00 on 2011-06-09
only these three buttons are gone

---

### Post by Copper Bezel on 2011-06-09
Did you try running the command above?

---

### Post by emma00 on 2011-06-09
yup done this but no luck:(

---

### Post by felixq78 on 2011-06-09
> **nilarimogard said:**
> ":minimize,maximize,close" will give you a broken metacity because of the border around the maximize button. So you must put the maximize before minimize. Still, it should have worked anyway.

Try running this in a terminal and see if anything changes:
```
gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:maximize,minimize,close"
```

I've discovered a neat trick with Ubuntu 11.04.
This [minimize,maximize,close] operation won't work with 11.04 but if you log out of Unity and then back into Gnome classic it will work. Then log back into Unity and the buttons move from side to side when appropriate. If Unity needs the buttons on the left because there's other stuff on the right e.g. Calender/Time/login name, whatever,.. it places the buttons on the left, but if there's no need it automatically places them on the right. 
Cool,  eh ?

---

### Post by KirbySmith on 2011-06-12
Forced to upgrade from 9.10 to 10.04.2, I wish to bestow a kudos upon nilarimogard for providing the fix for this introduced inefficiency.  Maybe someone involved in Office 2007 ribbon development was allowed to meddle with Ubuntu.

kirby

---

