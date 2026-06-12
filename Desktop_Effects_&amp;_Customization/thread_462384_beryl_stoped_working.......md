---
title: "beryl stoped working......"
date: 2007-06-02
forum: Desktop Effects &amp; Customization
---

### Post by kdarkentity on 2007-06-02
all i did was try to use skydome and beryl stoped working...

---

### Post by blackened on 2007-06-02
Go to the .beryl folder in your home directory and open the file named settings in gedit. Scroll down to the [cube] section and set s_skydome to false. You should be able to start beryl again after that.

Skydomes are very finicky about image size (I've had tons of problems related to this.). See associated info here [http://www.davidsterry.com/2007/04/creating-beryl-skydome-with-gimp.html]("http://www.davidsterry.com/2007/04/creating-beryl-skydome-with-gimp.html").

---

### Post by kdarkentity on 2007-06-02
the only way i can get beryl to work again is if i type beryl into a terminal and leave the terminal running....

---

### Post by kdarkentity on 2007-06-02
i tried changing the settings to false but it still wont work...it only works if i type beryl into the terminal.....

---

### Post by blackened on 2007-06-02
Try typing beryl-manager into the terminal and see what kind of error codes it gives you.

---

### Post by kdarkentity on 2007-06-02
i get no errors..... and it still doesent work

---

### Post by blackened on 2007-06-02
Try renaming the settings file in your .beryl directory. This should let beryl start clean. That way we can see if it's an errant setting causing the problem in the first place.

---

### Post by kdarkentity on 2007-06-03
all right man im set for now... i removed beryl and even removed the old folders in my home folder that associate with beryl ....than i reinstalled it.... it still didnt work.... i installed like every package from synaptic for beryl (except the unstable ones) and than i reinstalled emerald and installed a new theme.... restarted feisty.... logged in... beryl still didnt start soo... i typed beryl into the terminal ...played with some settings in the settings manager... and for some random reason it just starts up normally again ...lol

thanks for the help... just wait until i mess it up again lol

---

### Post by blackened on 2007-06-03
Not that I was really much help, but I'm glad you got it sorted out.

---

### Post by pavan_bitsgoa on 2007-06-16
hello every one
 i have exactly the same problem as said by kdarkentity
beryl  worked well for abt 3 days after installation 
was workin fine even after reboots(abt 12 reboots) then suddenly it stopped workin fr no reason
this is the second time it happend to me 

first time beryl stopped workin i reinstalled ubuntu (runnin fiesty fawn)
after reinstallin ubuntu i loaded beryl again it was fine fr another 5 days then again it stopped working again!!!

this time i uninstalled beryl through terminal n every other package linked with it tried installing it again. ubuntu just went blanck for about 3 restarts then there were my previous settings without beryl ie only window wobbling and workspace on a cube which come default with ubuntu.

finally when i tried runnin beryl through terminal it gives on errors but runs with the previous settings that i had before i uninstalled beryl

i have to keep the terminal window running for beryl to work when i close that terminal window sys just crashes

can any body help me pls

heres what is shown in the terminlal after i run beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

Reloading options
beryl: pixmap 0x120ed80 can't be bound to texture


rit now beryl works only when i load it through terminal n keep the terminal window running

pls can some one give me a solution
thanks in advance!

---

### Post by kdarkentity on 2007-06-16
first of all... does it stop working randomly? Or does it stop working after you change some settings?

ok my suggestions for you are to re install beryl if you haven't already done so ...after installation play with it and see if it works at all ...and if some parts are not working ...go to your home folder ...go to view show hidden files ... find the .beryl folder ...delete it and then start up beryl again and see if it works

let me know if this helps or not

---

### Post by ikkefc3 on 2007-06-16
> **pavan_bitsgoa said:**
> hello every one
 i have exactly the same problem as said by kdarkentity
beryl  worked well for abt 3 days after installation 
was workin fine even after reboots(abt 12 reboots) then suddenly it stopped workin fr no reason
this is the second time it happend to me 

first time beryl stopped workin i reinstalled ubuntu (runnin fiesty fawn)
after reinstallin ubuntu i loaded beryl again it was fine fr another 5 days then again it stopped working again!!!

this time i uninstalled beryl through terminal n every other package linked with it tried installing it again. ubuntu just went blanck for about 3 restarts then there were my previous settings without beryl ie only window wobbling and workspace on a cube which come default with ubuntu.

finally when i tried runnin beryl through terminal it gives on errors but runs with the previous settings that i had before i uninstalled beryl

i have to keep the terminal window running for beryl to work when i close that terminal window sys just crashes

can any body help me pls

heres what is shown in the terminlal after i run beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

Reloading options
beryl: pixmap 0x120ed80 can't be bound to texture


rit now beryl works only when i load it through terminal n keep the terminal window running

pls can some one give me a solution
thanks in advance!
Open Beryl-manager, click right on the beryl icon, goto Choose Windowmanager and choose beryl, if Beryl is already selected, click reload windowmanager.

---

### Post by pavan_bitsgoa on 2007-06-17
thank u for ur prompt reply
im happy that the problem is for now temporarly solved i followed the method of kdarkentity

currently beryl loads without that terminal 
i added it at start up frm the adress /usr/bin/beryl

now i have a different problem

the red diamond ie the icon of beryl doesnt appear in the notification area even though the beryl is running
so i couldn try ikkefc3's method

i have a new broblem now i cant even run the emerald theme manager nor can i edit the other settings that normally come on right clickin on that red diamond thing in notification area

so can u help me out for gettin the red diamond in the notification area when i run beryl?
thank you

---

### Post by kdarkentity on 2007-06-17
Go to system tools beryl manager

all of your options should be in there

---

### Post by pavan_bitsgoa on 2007-06-17
hei i know that every thing is there in systools>beryl manager

but i cant get that red diamond icon in the notification area still every thing else is fine only the _red diamond in notification area_  

thnaks any specific instructions regarding that

---

### Post by kdarkentity on 2007-06-17
umm try typing beryl setting manager into the terminal and see what happens

---

### Post by pavan_bitsgoa on 2007-06-18
well no change at all just that beryl which was runnin previously now only runs through terminal 
still no sign of that red diamond in notification area!!

---

### Post by kdarkentity on 2007-06-18
what is the output in the terminal if u type beryl

and also go to system>preferences>sessions and see if beryl is checked off

---

