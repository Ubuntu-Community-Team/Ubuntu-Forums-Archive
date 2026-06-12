---
title: "workspace switcher has changed,"
date: 2009-06-24
forum: General Help
---

### Post by makoshark55 on 2009-06-24
My workspace switcher has changed I now have a blank space below the two panels.
I don't know when it happen, I was having some trouble getting PHPMyAdmin installed and working. I have  included a screen shot (croped) to show what I am talking about. can anyone tell me how to restore it?
[IMG]http://www.nilandsplace.com/images/Screenshot.jpg[/IMG]

---

### Post by gettinoriginal on 2009-06-24
Columns 2, Rows 2 for the square look, Columns 4 Rows 1 for the long one

---

### Post by makoshark55 on 2009-06-25
Thanks For answering my post!!! > My workspace switcher has changed I now have a blank space below the two panels.
I don't know when it happen, I was having some trouble getting PHPMyAdmin installed and working. I have included a screen shot (croped) to show what I am talking about. can anyone tell me how to restore it?
I guess I shout have included the fact that I had already tried different settings. this is what happens when I set it to 4[IMG]http://www.nilandsplace.com/images/Screenshot2.jpg[/IMG] I still have this grey bar along the bottom. Originally I had 2 rectangles side by side. Also It my be important at this time I am using the nvidia drivers downloaded via ubuntu version 180. I have a nvidia 6200 AGP x8 256Mb card. Thanks for looking James

---

### Post by gettinoriginal on 2009-06-26
I cannot seem to duplicate the problem
The initial 2 cubes is default.  What window manager are you running ??
Have you tried removing it from panel and then adding it back ??  
Then check synaptic for gnome-panel and gnome-panel-data to make sure they are installed (just guessing on that one  :confused: )

---

### Post by gettinoriginal on 2009-06-26
Just had another thought, try right clicking panel > new panel > and add the applet to the new panel to see if you get the same results.  If it works on new panel, just move anything else to new panel and delete the bad one.  :D

---

### Post by makoshark55 on 2009-06-27
More interesting facts: I got the switcher back for a short while went my application menu got gone. I used this to get it back```
sudo debconf gnome-panel
```After runing the code in the terminal it was right until I rebooted then it went back to the wrong way. If I add rows I still have the Gray bottom half that is un-click-able. Thinking about it more I think it went wrong after my failed terminal install of PhpMyAdin and I hade to fix the broken package in safe mode. I don't know if any of this helps? but it is great to get any help. Thanks Jim

---

### Post by makoshark55 on 2009-06-27
Well Problem solved. It seems when I ran the aforementioned code I was now able to delete the old one and put a new one that is correct in its place. In newbish:
Open a terminal applications>accessories>Terminal  at the prompt run this code:```
sudo debconf gnome-panel
``` reboot:
Then you should be able right click the offending workspace switcher an click on remove. Next click on the panel and click add. Navigate to the selection for workspace switcher, caution there are others that are SIMULAR make sure you add "workspace switcher". Most likely It wont land in the right position so you will need to right click it and select move to get it were you want it.

---

