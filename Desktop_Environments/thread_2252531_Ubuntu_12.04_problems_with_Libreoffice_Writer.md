---
title: "Ubuntu 12.04 problems with Libreoffice Writer"
date: 2014-11-12
forum: Desktop Environments
---

### Post by eightbits2010 on 2014-11-12
Using Ubuntu 12.04
 

 LibreOffice 3.5.7.2  
 Build ID: 350m1(Build:2)
 

 After a recent update, Office _Writer_ will no longer allow Table Borders to set a double line around

 a group of cells. Also, can't change the line width setting even though the display for setting borders 
indicates the new values are entered. After inserting a table and then selecting a group of cells to edit, the table display

 on the screen starts to blink while the selected table cells are displayed.
I tested cell formating in the LibreOffice _spread sheet_ and it works as expected with no problems.
So, the issue seems to be with Writer. Any suggestions or help ?

---

### Post by ajgreeny on 2014-11-12
Why not try the newer version of Libreoffice, Version: 4.3.3.2, available from the ppa at [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu).

I have been using the ppa for a long time without any real problems or difficulties, though a quick look at my installation suggests that a double line border is not possible any more, or is certainly not in the list of styles as far as I can see.

---

### Post by eightbits2010 on 2014-11-13
ajgreeney: When using Writer and inserting a _table_ and selecting  a group of cell's. right clicking on table
which produces a drop down list. From this list I select Table which produces a tabbed window which I then select borders.
I made a partial screen shot. The screen shot displays the double border selection.
I will look into the version 4 you mentioned.  Thanks for the suggestion.

---

### Post by ajgreeny on 2014-11-13
My mistake; my LO 4.3.3.2 also has that double lined border showing, I simply missed it last time (must get my eyes tested again!) and it also gives me that double line when I ask it to do so.

Not having played with this too much before, I now see also that as you increase the point size or thickness of the border lines, so you get many more styles of lines to use up to a max size of 9pts.

---

### Post by eightbits2010 on 2014-11-14
ajgreeny: Well, I went back this morning, tried it again, and now it works as expected.Some times my Ubuntu 12.04 does strange things. Yesterday, I even rebooted and it did not change the error.  Oh well.......
BTW,  what is PPA ?

---

### Post by ajgreeny on 2014-11-14
PPAs are Personal Package Archives.
See [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas) for all the details.  Iuse several in my Xubuntu 12.04 and they enable me to install more updated versions of some packages than those in the normal repos, eg gimp, LibreOffice, or some packages that are not in the normal repos at all, eg audio-recorder.

---

