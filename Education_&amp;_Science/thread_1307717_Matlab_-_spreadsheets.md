---
title: "Matlab - spreadsheets"
date: 2009-10-31
forum: Education &amp; Science
---

### Post by il pepe on 2009-10-31
I'm working on a programming piece, and i would like to output data in a spreadsheet. .ods would be great.
XLSwrite works perfect in the software.
but there doesn't seem to be something equivalent for another format.
xlswrite works with activeX so i suppose you'll need excel installed to get it working.
Or is there another way to make xlswrite work?

Is there another way to output my data?
Problem is, it isn't all data, there are also strings involved and csvwrite seems to make a lot of trouble of that.

---

### Post by Gibsonbc on 2011-02-05
I'm having a similar issue.  I noticed you posted this a while ago, and I'm wondering if you've had any luck.   I am trying to export data that is 2001 rows x 6 columns.  I don't know matlab that well, so I would like to just export the data into a spreadsheet in excel.  Also, this data will be used on my professor's computer as well, which is windows. I have excel running in virtual box on my ubuntu host but it obviously doesn't show up as installed to matlab

I'm using 

% Writes the history data from invBed5,6,7 and the fobj to a spreadsheet for Excel

d={'Slip','Trishear (rads)', 'P/S', 'Ramp (rads)', 'Tipline X', 'Tipline Y'};
xlswrite('hi5_x.xls', d, 'A1')
xlswrite('hi5_x.xls', hi5.x, 'A2')


I would like the first line to print as the title for each column, and the data in the file "hi5.x" to print underneath it.  however, since excel isn't installed, it just exports everything as a .csv file and ignores my row parameters.  Also text is horrible in .csv files.

---

### Post by jbrefort on 2011-02-06
I never used Matlab, but I suppose that you can export your data as simple text, then any spreadsheet (calc or gnumeric or excel) will be able to import the text and save as an .xls file.

---

### Post by supergrav on 2011-02-08
+1 to what jbrefort said...I'm using Matlab quite often and I have to interact with Windows' users. Using 'xlswrite' led me to various problems of compatibility with Windows' applications. So you'd better export data to a simple .txt or .dat file.

---

### Post by Blutkoete on 2011-02-09
You could add some automation to the process by using a (I don't know whether there a free ones) CSV-to-Excel converter; you could call a command line converter from within MATLAB with a *system* command (or write your own m file).

Another option - but's that like using nuclear missiles to kill a mosquito : You might use the database connector toolbox to save your data to an SQL database and read the data with Excel from there.

All just in case you need to automate the process and xlswrite won't work.

---

