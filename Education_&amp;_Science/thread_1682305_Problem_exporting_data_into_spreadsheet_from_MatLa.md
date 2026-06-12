---
title: "Problem exporting data into spreadsheet from MatLab"
date: 2011-02-05
forum: Education &amp; Science
---

### Post by Gibsonbc on 2011-02-05
So, I am both new to MatLab and linux, and hopefully someone out there can help me.
I have data in a matlab file called hi5.x which is a list of numbers that  is 2001 rows x 6 columns.  I would  like to just export the data into a spreadsheet in Excel (or even OpenOffice, but my professor that will also be using this data only uses Excel which means I'd have to convert everything first).  I  have excel running in virtual box on my ubuntu host but it obviously  doesn't show up as installed to matlab which runs in ubuntu.  I would like the data to start on the second row, under their respective column titles.  Here's the code I've started with using xlswrite.

% Writes the history data from invBed5,6,7 and the fobj to a spreadsheet for Excel

d={'Slip','Trishear (rads)', 'P/S', 'Ramp (rads)', 'Tipline X', 'Tipline Y'};
xlswrite('hi5_x.xls', d, 'A1')
xlswrite('hi5_x.xls', hi5.x, 'A2')

What I get is an error message.  If I try exporting the data alone, matlab saves it as a .csv file, which is fine, but I have to manually add a row at the top and type in the titles.  If I try exporting only the titles, .....crap.  Text strings read horribly into .csv files.  

Thanks in advance for anyone who can offer some insight, or a work around.

---

