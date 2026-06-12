---
title: "Data issues in ubuntu"
date: 2009-06-29
forum: Desktop Environments
---

### Post by GabrielsHorn314 on 2009-06-29
Hey guys,
  I have a problem (im not exactly sure that it should be in this forum, so please let me know), which is, i need to open up very large excel and .dbf files in ubuntu. Open office and Gnumeric do not have the capacity to open these files, and i may have to buy a new tower or partition to windows if i cant find a solution for this. if anyone else out there works with large amounts of data as i do please tell me how you do it. thanks a lot for your help.

-cory

P.S. I need to open at least 1.56x10^8 cells at one time. (maybe there arent any programs in ubuntu that can handle this, but my windows comp at work can)

---

### Post by pytheas22 on 2009-06-29
You could try installing Microsoft Office in Ubuntu using wine.  I believe Office 2007 should install with no hitches in the latest version of Ubuntu, and I know from my own experience that Office 2003 works great.  If you don't have a license for another copy of Office, you could download just Excel Viewer, which should also work fine.

You might also think about converting the Office files to a native OpenOffice format before opening them; that may help OO deal with them properly (you don't mention why exactly it was failing to open them--did you receive an error message or did it just crash?).

If all else fails, virtualizing Windows using an application like VirtualBox, and installing MS Office in that, should work.

---

### Post by GabrielsHorn314 on 2009-06-29
OO and gnumeric can only handle 65.536 rows of data, whereas I need a few million. it gives me an error message and just displays the most that it can possibly handle.

I have wine installed, but havent quite figured out how to install programs inside of it. I thought that this could be a very feasible solution, but am not sure how to install and run programs inside of wine, as well as how to get a copy of microsoft office. (would a store-bought copy just work fine installed in wine?)  If you could give me some insight as to how I would go about doing this, I would appreciate it. Driving 25 minutes every time I come across a .dbf file that exceeds 65536 rows is incredibly annoying. 

-cory

---

### Post by GabrielsHorn314 on 2009-06-29
I just saw u lived in b-more. just to give you an idea, i drive from Columbia to UMD-CP every time I have the problem.

---

### Post by pytheas22 on 2009-06-29
You install programs in wine just like you would in Windows--start the .exe file and an installer opens.  To launch the .exe, you will need to right-click and select "Open with WINE Windows Program Loader."  Double-clicking the .exe won't work, for security reasons.  Autorun from a CD probably also won't work, so if you have an Office CD that you're trying to install from, you will need to browse the CD contents, find the .exe for installing Office, and execute that manually.

Once the installer opens, just follow the instructions on the screen just as you would in Windows.

A store-bought copy of Office would work fine.  You can also download Excel Viewer for free [here]("http://www.microsoft.com/downloads/details.aspx?FamilyID=c8378bf4-996c-4569-b547-75edbd03aaf0&displaylang=EN").

And yes, you shouldn't have to drive that far just to open a file :)  (On that note, is remote access to your Windows computer a possibility?  You could connect using VNC or Windows' built-in desktop sharing software).

---

### Post by GabrielsHorn314 on 2009-06-29
I never know which comp will be open seeing as I do research for the university, so remote access is kind of out of the question. I will try to install office in wine and let u know how it goes. thanks a lot for the help

---

### Post by oldfred on 2009-06-29
When you talk about large numbers of records I think of databases not spreadsheets. This goes back to SuperCalc only allowing enough columns and rows for 2 sheets of greenbar paper. I converted to dBase for many years then to MS Access. I am playing with Kexi and Knoda which are linux front ends for databases. Knoda defaults to MySql but supposedly will import dbase with an addin. Kexi will import Access. MySql will directly import comma separated data. There are also python and perl scripts that do many conversions.  So in the short term you may want to use Windows since that works for now, but I suggest looking at databases for the future.

---

### Post by mtbsoft on 2009-06-29
Another option, if the wine approach doesn't work, would be to use a virtual machine (VirtualBox, VMWare or others) and install Windows and Office in there.

Just a fallback position for if the other approaches don't work.

---

### Post by GabrielsHorn314 on 2009-06-29
Oldfred, thanks for the advice, but kexi wont open the type of files i am trying to open. i thought it was gonna work for a second there though, would have be a great solution. 

mtbsoft, I may try the virtualbox if i cant get wine to run it, but i dont think i have my vista disk laying around anywhere after i put ubuntu on this comp. 

pytheas22, im still trying to get it to work in wine, i may just have some corrupted files, if i cant get it to work by tomorrow i may have some more questions because im probably just doing something wrong


thanks for all the help guys

cory

---

