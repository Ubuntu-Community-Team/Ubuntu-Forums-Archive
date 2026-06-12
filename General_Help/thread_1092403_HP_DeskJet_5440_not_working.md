---
title: "HP DeskJet 5440 not working"
date: 2009-03-10
forum: General Help
---

### Post by 6205 on 2009-03-10
Any idea how to get this printer to work? I have default Ubuntu 8.10 installation with all updates, but printing seems to be problem..

When i plug in this printer, in few seconds pop-up notifies me of successful installation using hplip drivers of 5400 series, but i'm unable to print anything, not even a test page :(

Printer always prints in header of A4 paper one line of some pictograms like Webdings or Windings or various other fonts, but that's all.

---

### Post by rbmorse on 2009-03-10
From the top panel, System > Administrating > Printing 

Right click on the printer's icon and click on "properties"

Look at the line "make and model".  Is this correct?  If not, click on the "change" button and select the correct driver:

On the selection dialog page make sure the "select printer from database" button is selected, select the HP line on the scroll box then click on "forward" Find "Desktet 5400" in the scroll box in the next window (left side) and verify "HP Deskjet 5400 series Foomatic/hpijs[en] (recommended) is selected and click on forward.  Follow the prompts from there.

---

### Post by apsot on 2009-03-29
> **rbmorse said:**
> From the top panel, System > Administrating > Printing 

Right click on the printer's icon and click on "properties"

Look at the line "make and model".  Is this correct?  If not, click on the "change" button and select the correct driver:

On the selection dialog page make sure the "select printer from database" button is selected, select the HP line on the scroll box then click on "forward" Find "Desktet 5400" in the scroll box in the next window (left side) and verify "HP Deskjet 5400 series Foomatic/hpijs[en] (recommended) is selected and click on forward.  Follow the prompts from there.

I' ve got exactly the same problem with 6205 and the advise above didn't help (followed the instructions despite that the line "make and model" was correct 2 b sure). Does anybody have any idea? it would be REALLY appreciated

---

### Post by apsot on 2009-03-30
it finaly worked! I downloaded the ppd file for my printer (5440 and not 5400) from here: [http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi) 
then in the printer properties pressed change at make and model
and after checking the Provided ppd box browsed for the downloaded file.

---

### Post by oiio on 2009-04-26
apsots site and rbmorses "change" worked perfectly !

thx guys

---

### Post by 6205 on 2009-05-05
In Ubuntu 9.04 is HP 5440 not only properly detected but also working great :)

---

