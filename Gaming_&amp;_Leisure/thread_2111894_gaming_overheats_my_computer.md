---
title: "gaming overheats my computer"
date: 2013-02-03
forum: Gaming &amp; Leisure
---

### Post by gimchicoffee on 2013-02-03
hi, so ive tried to figure this out on my own. i had a decent enough gaming setup up until a month ago. it was ubuntu 11.10 on my toshiba satellite laptop which has a radeon 4200 HD card. it was good enough for me to easily play GTA san andreas, counter-strike source, HL2 level games with no problems or slowdowns. i had tweaked it with various installations and stuff. 
   unfortunately i had to reinstall 11.10 and don't remember what exactly I had done to get it in such good shape. so now i've done a clean install of 11.10, installed the latest AMD catalyst, which was the recommended driver for the radeon card and also updated fglrx. now when i play GTA san andreas my computer massively overheats to 95degrees or more according to jupiter and the game slows to a crawl. what else can i install or do?

---

### Post by ibjsb4 on 2013-02-03
11.10 will reach end of life in April, do you really want to set it up again?

12.04 is the current LTS release (has 5 years of support).

---

### Post by gimchicoffee on 2013-02-03
i should have mentioned, i tried installing 12.04 and got a black screen, apparently also related to my stupid radeon card.

unfortunately i didn't buy this laptop (years ago) with linux compatibility in mind, and at times its been great, lately not doing so well.

just any advice on something im forgetting to set up?

---

### Post by rudeboyskunk on 2013-02-03
You should clean the dust out of your fan.  My computer only gets that hot when it's dusty inside.  Go to youtube and type "clean dust from computer fan" or something like that and you'll find like 100 videos that are all helpful.

---

### Post by mastablasta on 2013-02-04
12.04 will have the latest and last AMD linux drivers for your chip.

---

### Post by superchar42 on 2013-02-04
a) clean your computer
b) have you thought of setting your cpu fans to kick in sooner?

here's a link about fancontrol and it's usage: [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

---

### Post by thnewguy on 2013-02-05
I suggest giving 12.04 another try and set the computer to boot using the kernel flag "nomodeset", that fixed the blank screen/freeze problem for me as my Radeon card is also problematic. Once the install is complete, then install the stable non-free Radeon driver and you should be fine.

---

### Post by houseworkshy on 2013-02-05
It may also be worth putting in a lighter gui, if your gameing, or doing anything other than looking at your desktop really, why bother with all the desktop effects?  All you really need is a way of getting into and out of your programs, so free up some ram.  You will need, for most programs, some sort of gui for the sake of X but it doesn't have to be funky topend.  There are several choices which are in the default repositories, lxde, Xfce and so on.  These can be chosen at boot once you've installed them.

---

### Post by holastickboy on 2013-02-06
Laptops are notorious for overheating and gaming.  Make sure you give it plenty of space when gaming (eg: dont keep it on your lap when playing games), and invest in a laptop cooling stand or riser (you can get them for a few dollars on ebay).  My mate had a similar problem recently, we opened it up, and found cat hair all over the delicate insides. Removed it all with some canned air, and it's good as new now!

---

### Post by gimchicoffee on 2013-02-07
thanks for the advice, i checked inside and will clean it out, i think i finally found the problem though.

i had installed the newest ATI driver, which apparently doesn't work well with this older card. so i'm now installing a legacy (old) version of ATI catalyst. we'll see if that helps

EDIT: i foolishly attempted to uninstall the catalyst driver, then restart to install fresh. now im running ubuntu off of a USB.

i get a black screen on loading my borked ubuntu

---

### Post by mörgæs on 2013-02-08
ATI has a bad habit of abandoning their cards after a very short time. I don't know with this particular one, but more often than not people have to use the default open-source (Radeon) drivers. 

If you don't use it for gaming, how does it work in X/Lubuntu 12.10 using Radeon drivers?

+1 for opening the case and cleaning dust from the fan and radiator.

---

### Post by DirtyPC on 2013-02-09
Integrated graphics on a laptop aren't really designed for gaming. The HD4200 will overheat often, from personal experience.

---

### Post by TOMBSTONEV2 on 2013-02-09
Usually I do not game on laptops, (especially if I want them to last a long time) If you do game I would encourage you to find a 5 volt rail, and put a switch in there to run the fan from thermal sensor, or from its maximum voltage source. Hard to explain, easy to do. I have done this with my xbox 360, as well as my hp mini for when I am being hard on them.

---

### Post by holastickboy on 2013-02-12
The 4200 shouldn't overheat naturally... they don't make cards that overheat on purpose.  That being said, indeed, AMD has abandoned the 4XXX series and below cards from the latest catalyst drivers.  The legacy catalyst drivers are still light years ahead of the Radeon drivers though with gaming.  How's the power control for laptop cards on the Radeon drivers, anyone know?

I recommend installing Ubuntu 12.04 instead of 12.10 if you are having problems with video cards.  12.10 has not included a great deal of files needed for proper graphics installation (they forgot linux-source, linux-headers and build-essential), that makes life a little harder.  With a default Ubuntu 12.04 installation, it should be a matter of installing than choosing the driver in the "Software Sources" program.

---

### Post by TOMBSTONEV2 on 2013-02-13
+1 for 12.04, It is all I ever use, So little problems. :KS Ultimatetly 12.04 is astounding in my opinion.

---

