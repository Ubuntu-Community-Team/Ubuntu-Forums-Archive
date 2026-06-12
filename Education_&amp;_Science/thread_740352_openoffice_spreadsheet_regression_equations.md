---
title: "openoffice spreadsheet regression equations"
date: 2008-03-30
forum: Education &amp; Science
---

### Post by scholzilla on 2008-03-30
I don't have any problems fitting a regression line to graphed data in OpenOffice, but I can't output the equation that is fit. In Excel, this is done under a statistics tab that gives you the option to display the equation on the chart. Not so in OpenOffice. Is there another way? Clearly the function is being computed, but I how do I get to it? This doesn't appear to be addressed in the help manual either. 

Thanks

---

### Post by whelanh on 2008-03-30
I am not sure what version of openoffice you are using.  I ran across the following discussion of the new features of openoffice 2.4 which includes being able to put the regression equation on the chart. 

See: [http://www.oooninja.com/2008/03/new-features-openofficeorg-240.html](http://www.oooninja.com/2008/03/new-features-openofficeorg-240.html)

Hope that helps.
Hugh

---

### Post by akniss on 2008-03-30
There isn't a direct way to add the regression equation, which is one of the reasons I use gnumeric instead of OOCalc.  In order to get the regression equation, you must use the =slope() and =intercept(), then use the =correl() function to get the r-squared.  Quite a pain if you ask me.

If we assume that we have 6 observations in rows 1 to 6, column A contains independent variables, and column B contains dependent variables, then:
=slope(b1:b6;a1:a6)
will provide the slope of the regression line, 
=intercept(b1:b6;a1:a6)
will provide the intercept of the regression line, and
=correl(b1:b6;a1:a6)^2
will provide the r-squared.

This is certainly not an ideal way to have to do this, and something I hope the OpenOffice.org team is planning on dealing with in the future.

---

### Post by akniss on 2008-03-30
[http://wiki.services.openoffice.org/wiki/Chart2/Features2.4](http://wiki.services.openoffice.org/wiki/Chart2/Features2.4)

Looks like it is an option in OOo version 2.4.

---

### Post by scholzilla on 2008-03-31
Thanks for the replies. Looks like only a short wait for 2.4. I also found the LINEST function which can be used on arrays via the function wizard.

---

### Post by earlycj5 on 2008-03-31
2.4 is out, what's to wait for?  :)

---

### Post by rouge568 on 2008-05-03
Open Office 2.4 is included by default in 8.04. Regression equations work like a charm!

---

### Post by Hagar Delest on 2008-05-03
If you don't want to upgrade the whole distro, just install the OOo 2.4 version: install the official version of OOo : [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

