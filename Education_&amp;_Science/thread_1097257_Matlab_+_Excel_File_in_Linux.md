---
title: "Matlab + Excel File in Linux"
date: 2009-03-15
forum: Education &amp; Science
---

### Post by lvleph on 2009-03-15
In windows it is pretty easy to import data from Excel Files using Matlab. However, when I try to import data from an Excel File using Matlab in Linux I get the following error:
```
Warning: XLSREAD has limited import functionality on non-Windows platforms
or in basic mode.  Refer to HELP XLSREAD for more information.
> In xlsread at 198
  In beeplot at 4
Warning: XLSREAD has limited import functionality on non-Windows platforms
or in basic mode.  Refer to HELP XLSREAD for more information.
> In xlsread at 198
  In beeplot at 6
??? Error using ==> xlsread at 211
In basic mode, sheet argument must be a string.

Error in ==> beeplot at 6
[data2, header2] = xlsread(file.name, 2);
```
I haven't a clue why this is not working. The file has been converted to xls instead of xlsx.

---

### Post by hubie on 2009-03-16
When invoked in Windows, xlsread relies on Excel running as a COM server.  If xlsread cannot access the COM server, it runs in basic mode.  Are you able to access the spreadsheet in Windows in basic mode?  The limitations of basic mode are listed [here]("http://www.mathworks.com/support/solutions/data/1-ZITZK.html?solution=1-ZITZK").

Also, in basic mode if you specify a sheet name, it has to be a quoted string that is also case-sensitive.  From the help:
> num = xlsread(filename, sheet, range, 'basic') imports data from the spreadsheet in basic import mode. xlsread uses this mode on systems where Excel software is not installed. Import ability is limited. xlsread ignores the value for range and, consequently, imports the whole active range of a sheet. (You can set range to the empty string ('').) Also, in basic mode, sheet is case sensitive and must be a quoted string.

For your code, you might want to try
```
[data2, header2] = xlsread(file.name, 'Sheet2', '', 'basic')
```
You can double-check by running that in Windows and see whether you can still get at the data.

---

### Post by Betty1978 on 2009-03-16
Matlab is working in both Windows and Ubuntu in the same way to me. I am able to extract data easily.

---

### Post by hubie on 2009-03-16
The other thing you can try, and I saw this somewhere in a Matlab help topic, is that you can save your Excel file in Win95 format.  Apparently you have to go back that far to ensure there aren't any screwy formatting things that have been added over the years, which are the things that aren't handled well in basic mode.

---

### Post by lvleph on 2009-03-16
Okay, I figured out the problem. I was using a number instead of the sheet name. In windows this works just fine, but in linux it requires a sheet name. Everything is working now. Thanks for your help.

---

### Post by jingpro on 2009-05-02
> **lvleph said:**
> Okay, I figured out the problem. I was using a number instead of the sheet name. In windows this works just fine, but in linux it requires a sheet name. Everything is working now. Thanks for your help.

So you mean, for sheet name, we shall use 'texts' and avoid use 'number'? In this way, we can directly import 2003/2007 excel files with lots of rows?

---

### Post by lvleph on 2009-05-02
That is how I did it. But I still ended up having trouble with getting all the rows. I ended up just converting each sheet to a csv. It was much easier that way.

---

