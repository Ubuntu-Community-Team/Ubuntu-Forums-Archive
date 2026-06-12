---
title: "Openoffice Base likes the year 1970"
date: 2005-11-04
forum: Desktop Environments
---

### Post by psusi on 2005-11-04
I create a new database, create a new table, give it a date column, and save the layout.  Open the table to add some rows and enter a date, say 3/18/2002.  When I save the row, i.e. by tabbing off the last column to the next row, the date is changed to 3/18/1970.  Every time I enter a date, when the row is saved, the year switches to 1970.  

WTF?

---

### Post by MakubeX on 2005-11-05
You might wanna post this in the openoffice.org forum as well..

---

### Post by robinchew on 2005-11-05
yo there,

i have a similar problem like that before.
not sure if it's exactly related

but go here and check it out anyway [http://ubuntuforums.org/showthread.php?t=83224](http://ubuntuforums.org/showthread.php?t=83224)

now im having problems creating forms with quite an advanced combobox
this is wat i want to do:

there are 2 comboboxes

depending what you choose in combobox1, the options in combobox2 will change

so this is how I attempt to do it:

combobox1 has
[COLOR="Blue"]name: cboAccountNo
data field: AccountNo
type of list content: sql
list content: select "AccountNo" from "tblAccount"[/COLOR]

above seems to work so far, but I can't get the 2nd combobox to work below:

combobox2 has 
[COLOR="Blue"]name: cboType
data field: Type
type of list content: sql
list content: 
select "Type" from "tblAccountType" where "AccountNo" =[/COLOR][COLOR="Red"]cboAccountNo[/COLOR]

i dunno how the red colored code is properly written.
but if you do that in microshit access, it will work

I just don't know how openoffice.org base writes it or if it even works that way.

I might make a new thread about this as well.

i will value anyones input,
thanks,
Robin

---

### Post by psusi on 2005-11-07
That other thread talks about getting errors with dates.  I don't get any error messages, and the dates retain the correct day and month, just the year goes back to 1970.

---

### Post by Marcos.Rufino on 2005-11-07
[QUOTE=psusi]I create a new database, create a new table, give it a date column, and save the layout.  Open the table to add some rows and enter a date, say 3/18/2002.  When I save the row, i.e. by tabbing off the last column to the next row, the date is changed to 3/18/1970.  Every time I enter a date, when the row is saved, the year switches to 1970.  

WTF?[/QUOTE]

Maybe because 1970 was a very important year. The year I was born :-)

---

### Post by psusi on 2005-11-08
So nobody else has this problem?  

Any amd64 users?

---

### Post by greenpenguin on 2005-11-08
I have this problem, except the date is reset to 01/01/70 every time.
:confused:

---

### Post by ahood on 2005-11-13
Yep, I have this problem too with Base. When I enter a date, it reverts to 01/01/70. I am using OpenOffice2 that ships with Ubuntu Breezy. This is a seriously annoying bug and should be fixed. Oh wait, Ubuntu installs a beta version of Openoffice2 and the final release has been released. So my options are to wait (for how long?) or install OpenOffice again, effectively creating 3 versions of OpenOffice on this machine. To me, that is a waste of space. I could uninstall the other 2 versions, but not sure if Synaptic will update a version that I install myself. 

:mad: 

Hmmm............

I got around the formatting problem by choosing 'Text (fixed)' and limiting the number of characters to 10 and inserting 'mm/dd/yyyy' as the default text. Don't know if this will work when it comes to queries, but we shall see.

---

