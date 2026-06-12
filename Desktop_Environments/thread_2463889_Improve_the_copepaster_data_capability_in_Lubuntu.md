---
title: "Improve the cope/paster data capability in Lubuntu?"
date: 2021-06-20
forum: Desktop Environments
---

### Post by zhuxysoler on 2021-06-20
Hi. I switch to Lubuntu desktop in ubuntu 20.04lts recently. Some display or use problems don't happen again. But when a large amount of data columns are copied from LibreCal and pasted in other software, the system could freeze, LibreCal will be stuck. So are there some optimization or customization methods to improve the data transmission during copy and paste operation?

---

### Post by GhX6GZMB on 2021-06-20
Either more RAM or a swap partition.

---

### Post by zhuxysoler on 2021-06-20
> **ml9104 said:**
> Either more RAM or a swap partition.

The computer has 20GB RAM and gave 15GB for SWAP. When coping data, the RAM usage and SWAP didn't change suddenly before the system freeze.

---

### Post by guiverc on 2021-06-20
It may help if we know what release you're asking about.

---

### Post by zhuxysoler on 2021-06-20
> **guiverc said:**
> It may help if we know what release you're asking about.

Sorry for missing this information. I use Lubuntu desktop in ubuntu 20.04 lts.

---

### Post by monkeybrain20122 on 2021-06-21
Does it take long time for your data to load? What format is the table in (csv, ods, xsl, xlsx)? What application do you cut and paste to?

Yes, when the volume is huge it does take a while for operation to complete. It may help a bit if you enable multuthreading. 

open Calc, go to tools > options > Libreoffice Calc > Calculate > check the "Enable multithread calculation" under CPU threading settings if it is not already checked.

I use  a big test file with random entries (with three different versions .csv, .ods, and .xlsx, the ods is 10 MB, the XLSX is 16 MB, the .csv is 40M, maybe because I lost the original and created this from the .ods.) to see how long it takes to load and save, It is very fast for .csv. both loading and saving, but it does take a while for the .ods and .xlsx and the window turns grey but not nearly as bad as some people reported (takes maybe 1 minutes, with 6G of Ram) .  the .csv is issue free, .ods is ok except maybe slower, The .XLSX  is most resource demanding performs worst is often becomes unresponsive when editing,
  
So this experiment kind of confirms the general point that spreadsheet data should be in .csv rather than EXCEL (for example) for ease to process and interportability.(well TBH the real answer is one shouldn't use a spreadsheet program for serious data processing period but a real data analysis software like R or Python)

 LO 7.1.4.2


I think calc also has a limit for number of columns so for csv with a large number of columns I use gnumeric to view the file instead.

---

### Post by zhuxysoler on 2021-06-21
> **monkeybrain20122 said:**
> Does it take long time for your data to load? What format is the table in (csv, ods, xsl, xlsx)? What application do you cut and paste to?

Yes, when the volume is huge it does take a while for operation to complete. It may help a bit if you enable multuthreading. 

open Calc, go to tools > options > Libreoffice Calc > Calculate > check the "Enable multithread calculation" under CPU threading settings if it is not already checked.

I use  a big test file with random entries (with three different versions .csv, .ods, and .xlsx, the ods is 10 MB, the XLSX is 16 MB, the .csv is 40M, maybe because I lost the original and created this from the .ods.) to see how long it takes to load and save, It is very fast for .csv. both loading and saving, but it does take a while for the .ods and .xlsx and the window turns grey but not nearly as bad as some people reported (takes maybe 1 minutes, with 6G of Ram) .  the .csv is issue free, .ods is ok except maybe slower, The .XLSX  is most resource demanding performs worst is often becomes unresponsive when editing,
  
So this experiment kind of confirms the general point that spreadsheet data should be in .csv rather than EXCEL (for example) for ease to process and interportability.(well TBH the real answer is one shouldn't use a spreadsheet program for serious data processing period but a real data analysis software like R or Python)

 LO 7.1.4.2


I think calc also has a limit for number of columns so for csv with a large number of columns I use gnumeric to view the file instead.

Thanks for introducing your experience. I open csv and txt files in LibreCal, usually txt files. The txt and csv files have a much larger size than xlsx. The "Enable multithread calculation" was checked by default.  I test the copy performance. For example, I copy 90000 rows * 1 column data. After click copy, the system got stuck for a while, about half minute. Ram usage increases from 8GB to 11GB. After LibreCal restored operation again. The data can be pasted in Qtiplot. So during the system stuck time, no operations can be done, just wait a moment.  At least, the data process can be done except taking more time. 
Yes. use code to process giant amount of data is a better way. I also use matplotlib to visuallize the data in some cases, but need more time to write code.

---

### Post by zhuxysoler on 2021-06-21
> **monkeybrain20122 said:**
> Does it take long time for your data to load? What format is the table in (csv, ods, xsl, xlsx)? What application do you cut and paste to?

Yes, when the volume is huge it does take a while for operation to complete. It may help a bit if you enable multuthreading. 

open Calc, go to tools > options > Libreoffice Calc > Calculate > check the "Enable multithread calculation" under CPU threading settings if it is not already checked.

I use  a big test file with random entries (with three different versions .csv, .ods, and .xlsx, the ods is 10 MB, the XLSX is 16 MB, the .csv is 40M, maybe because I lost the original and created this from the .ods.) to see how long it takes to load and save, It is very fast for .csv. both loading and saving, but it does take a while for the .ods and .xlsx and the window turns grey but not nearly as bad as some people reported (takes maybe 1 minutes, with 6G of Ram) .  the .csv is issue free, .ods is ok except maybe slower, The .XLSX  is most resource demanding performs worst is often becomes unresponsive when editing,
  
So this experiment kind of confirms the general point that spreadsheet data should be in .csv rather than EXCEL (for example) for ease to process and interportability.(well TBH the real answer is one shouldn't use a spreadsheet program for serious data processing period but a real data analysis software like R or Python)

 LO 7.1.4.2


I think calc also has a limit for number of columns so for csv with a large number of columns I use gnumeric to view the file instead.

THX. I have a try. I try some cases gnumeric is  quicker than LibreCal.

---

### Post by TheFu on 2021-06-22
IDK, but does copying just the values, not the formatting make it work faster?
Also, are non-ASCII characters used?  Just another point of information - if characters are unicode, they could be 4x larger.

For anything larger than 500 rows, I'd look for a batch solution and avoid the GUI completely.

---

### Post by monkeybrain20122 on 2021-06-22
So I copied one column with 1048576 rows form my test csv in Cacl and paste it to the text editor just as an experiment. I don't experience the problem you described. Copy was instantaneous with no lockup at all , paste took longer and text editor turned grey for a little while indicating high usage of memory but that lasted for only a few seconds and there was no systrm lockup even when the text editor window was grey, I could still switch to Firefox. I have only 6 G of ram on this machine running Ubuntu 20.04 (with unity desktop, haven't tested it on gnome) My column consists of random gibberish  (long strings with both alphabets and numerals)

---

### Post by zhuxysoler on 2021-06-22
> **monkeybrain20122 said:**
> So I copied one column with 1048576 rows form my test csv in Cacl and paste it to the text editor just as an experiment. I don't experience the problem you described. Copy was instantaneous with no lockup at all , paste took longer and text editor turned grey for a little while indicating high usage of memory but that lasted for only a few seconds and there was no systrm lockup even when the text editor window was grey, I could still switch to Firefox. I have only 6 G of ram on this machine running Ubuntu 20.04 (with unity desktop, haven't tested it on gnome) My column consists of random gibberish  (long strings with both alphabets and numerals)

So I am confused by the computer performance which is not high enough as expected. At least it is a more efficient by using gnumeric to handle the current job.
The software in long-time working occupies a heavy load in RAM : [https://imgur.com/a/qTrn2oG](https://imgur.com/a/qTrn2oG)[COLOR=unset][/COLOR]

---

### Post by zhuxysoler on 2021-06-22
> **TheFu said:**
> IDK, but does copying just the values, not the formatting make it work faster?
Also, are non-ASCII characters used?  Just another point of information - if characters are unicode, they could be 4x larger.

For anything larger than 500 rows, I'd look for a batch solution and avoid the GUI completely.

Yes. I had an attempt to visualize the giant data by matplotlib coding.

---

### Post by ActionParsnip on 2021-06-22
Could use a clipboard manager like Parcellite and so on

---

### Post by TheFu on 2021-06-22
For huge datasets, avoid the GUI completely.
Scripts can pull data from spreadsheets as CSV.  Then that CSV can be fed into Qtiplot on the command line. According to the manual, 
> The name can also refer to an ASCII file:


qtiplot ASCII_file_name

In this latter case, a new "untitled" project will be created, containing a table or matrix with the ASCII data from the file. The file is read and interpreted using the current settings from the Import -> Import ASCII... command dialog. 

That would bypass the clipboard and any limitations it may have.  I don't have a clipboard. Prefer to use the X-buffer instead, but I don't know if libreOffice or Gnumeric will work with that.  Could quickly try a "Copy ..." --> values only test.  I suspect the extra formatting is getting in the way.

As for tools that can read spreadsheets - every scripting language like perl, python, ruby, has a module for that. Avoiding the GUI should make it 10x faster, at least. It might be instantaneous.

---

### Post by zhuxysoler on 2021-06-22
> **TheFu said:**
> For huge datasets, avoid the GUI completely.
Scripts can pull data from spreadsheets as CSV.  Then that CSV can be fed into Qtiplot on the command line. According to the manual, 


That would bypass the clipboard and any limitations it may have.  I don't have a clipboard. Prefer to use the X-buffer instead, but I don't know if libreOffice or Gnumeric will work with that.  Could quickly try a "Copy ..." --> values only test.  I suspect the extra formatting is getting in the way.

As for tools that can read spreadsheets - every scripting language like perl, python, ruby, has a module for that. Avoiding the GUI should make it 10x faster, at least. It might be instantaneous.

Yes. This is a good way to import huge datasets by qtiplot. It works! Because of the operation habit, I mostly import the data by GUI and copy/paste operation. 'import ASCII' is very good function, avoiding system stuck during copy/paste. The command 'qtiplot xxx.txt' also works, it will import the single file and plot automatically. It is suitable to deal with just one file instead of a project.

---

