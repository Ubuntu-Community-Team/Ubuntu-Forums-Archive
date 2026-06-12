---
title: "Wine + Dreamweaver + Independant Display problems"
date: 2009-10-22
forum: Desktop Environments
---

### Post by ShapeShiftme on 2009-10-22
Good day all. Due to the many variables that go into this problem im not sure to which section this should be posted. So i thought here.

The Scenario:
I am a web application developer and programmer that eventually couldn't take vista anymore so decided to switch to Linux. Kubuntu won it for me hands down over the other distributions after giving it a try. But more to the point after trying Quanta and Kompozer they just did not have all the features im used to compared to dreamweaver so i was able to install wine them ported dreamweaver CS3 onto it. I also installed ies4linux "I have to check my apps on IE for development reasons"

Now all this works great While just using my laptop this all goes PEAR Shaped when i connect my dual display.

The problem :
I have a new HP Pavilion dv7 2104tx. It coes with a wonderfull ATI HD 4650 1 GB Scrren card. Which is awsome after spending 3 hours trying to get it set up. Well i did get it set up and im using the propriety drivers . Configured with independant displayes. So i can drag windows across and then maximes them and they wont expand over both monitors. And the monitors are are configured with different resolutions.  "Im not using Big Desktop Setting"  

So now when i open dreamweaver or ie6 my screen goes blank "Black".  I Thought my displayed had died but i saw my mouse curser "It had hung - i couldnt move it" but it was 3 times the normal size. so im guessing that when i try open dreamweaver that opens in full screen it is trying to change my resolution and that is where it hangs. Does the exact same with IE4linux.

But then if i reboot without the second monitor it all works great and i can code away without any problem. exept haing to  alt-tab between many many windows.

My Thoughts:
I originally thought that perhaps wine does not support dual display but that is not the case as if i start EMS SQL Manager (Another app im used to from my windows days
I can switch the app between the monitors without any problems.

So from here i am stuck. Does anyone have any susgestions of things i could try. I really dont have to have to load my VM every time i want to work. That is there for a last resort.

Regards
Donovan Hoare

---

### Post by earthpigg on 2009-10-23
try a different version of WINE, either newer ***or*** older?

try modifying the options in WINE?

---

### Post by ShapeShiftme on 2009-10-26
Ok ive tried a newer version on wine.
I even tried a newer version of ubuntu (I just installed karmic)
That did not seem to work at all.

Dreamweaver works 100% when run with no extra monitors. So im gathering that it hased to be caused by the display drivers or how wine handles it. Does anyone have any other idea&#347; or has someone else had this problem.

Regards
Donovan Hoare

---

### Post by earthpigg on 2009-10-26
what if...

start it with only one monitor in, when it works fine. then, set it not to run in full screen or maximized.

instead of trying to maximize it across both screens, move it to the upper left of the left screen and manually resize the window so it takes up both screens?

ive played video games like that in 'windowed' mode taking up both displays, i dont know why i didnt think of that earlier.

---

### Post by ShapeShiftme on 2009-10-26
> **earthpigg said:**
> what if...

start it with only one monitor in, when it works fine. then, set it not to run in full screen or maximized.

instead of trying to maximize it across both screens, move it to the upper left of the left screen and manually resize the window so it takes up both screens?

ive played video games like that in 'windowed' mode taking up both displays, i dont know why i didnt think of that earlier.

Ok i started with monitor and gave it a try by minimizing it.
That did not work exactly the same problem

I opened another post regading piping wineoutput to a file. I havnt got that to work but i did see that it bombs around a line that sayed something about audio.
So i gathered that my monitor (2nd one) is HDMI with Audio perhaps that is the conflict. So i plugged in a normal VGA cable. 

Perhaps the HDMI Audio is causing Somehting, That didnt work either. so now im stumped.
Not working and i cant even get wine to pipe to a log file to read where everything goes wrong.

Any other Ideas Perhaps. 

(The URL to the wine output is) [http://ubuntuforums.org/showthread.php?t=1302262](http://ubuntuforums.org/showthread.php?t=1302262) 
In case anyone has an idea there.


Regards
Donovan Hoare

---

