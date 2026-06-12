---
title: "Qcad"
date: 2006-05-07
forum: Education &amp; Science
---

### Post by cssutto on 2006-05-07
I sent by email a drawing to myself.

The drawing was made on a windows machine and retrieved by evolution.

When I tired to open it with Qcad, I get the message that it is unable because I don't have permission.

How can that be?

A drawing made on a windows machine normally, and this did not, does not have any permission restrictions.

CSSJR

---

### Post by nanotube on 2006-05-08
so... save the attached file to disk (eg, to your desktop), and then try again. if still no dice, right click it, select properties, go to the permissions tab, and give yourself read/write permissions.

---

### Post by cssutto on 2006-05-08
I did.

Read, write and execute for everyone.

No difference.

The file is a .dwg file.  If Qcan can't read that, and if that is the problem and I expect it might be, they might as well throw it away because that is the format used to transmit most drawings by email.

I have sent and received hundreds of them using various forms of cad; both windows and Mac.

CSSJR

---

### Post by garner_nc on 2006-05-08
QCad only works with dxf files. Dwg files are a proprietary AutoDesk (AutoCAD) format. 
   I usually ask my customer to save the file as a dxf and then email to me. I get very little resistance to this.
   If you need to use dwg files there are a number of proprietary CAD programs available to Linux. 

All the Best,
Doug White

---

### Post by cssutto on 2006-05-08
Thans for clearing that up.

I suspected that.

CSSJR

---

### Post by nab on 2006-07-31
Hi cssutto,

I don't know if you solved your problem with importing dwg's into QCad.

I convert dwg files into dxf-files with dwg2dxf.

I downloaded the actual binaries as rpm-file (dwg2dxf-2.1-alt3.i586.rpm) and converted it with alien (without any options) into a deb file (dwg2dxf_2.1-1_i386.deb).

After installing the deb-file I used it to convert my dwg's. 

Upto now I had only the problem that I can only open the files from within QCad. Open these files with double clicking QCad complaines about not having the right permissions :confused: 

Well, but I'm happy everything is working fine for me :p 

Hope this works for you too.

Regards,
Niko

---

### Post by impeteperry on 2006-12-12
I do not have any Windows on main computer
Have turboCAD on MS 98 2ed  on backup.
My client uses AutoCAD 2006.

QCad reads AutoCAD "dxf" files fine.
I add info to drawing
E-mail changed drawing (dxf) bact to AutoCAD
Drawings open, but text is screwed up.

E-mail same changed drawings (dxf) to my MS 98
Open them in TurboCAD. (perfect copy!!)
Save as "dwg".
E-mail back to AutoCAD.
All is good with AutoCAD

Why can't QCad write dxf that is compatable with AutoCAD? I am not asking for dwg conversion.

Qcad dxf are 4 x size of TurboCAD's dwg.

QCad is great to work with, the best I've come accross. Keep it up.

---

### Post by impeteperry on 2007-02-12
The reason my Qcad files were so big, they carried all the AutoCAD baggage. Original QCad driawigs were fine.

Mre there any Qcad  (not RibbonSoft) people monitoring this form?

---

### Post by nanotube on 2007-02-14
> **impeteperry said:**
> 
Mre there any Qcad  (not RibbonSoft) people monitoring this form?
my guess is "no" :)

---

