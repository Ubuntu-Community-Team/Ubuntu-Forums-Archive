---
title: "OpenOffice won't print anymore."
date: 2009-05-05
forum: General Help
---

### Post by BslBryan on 2009-05-05
Hey guys.  :-)

Okay, so I was printing off some completed work to stick in a portfolio for a final exam in a class of mine.  OpenOffice printed fine.  Then I printed an image from GIMP.  

Next thing I know, OpenOffice doesn't want to print. ](*,)

The printer icon pops up in the panel, but goes away after about three seconds. :-k

So, now anytime I want to print a text document, I have to export it to PDF and open it with Gimp.  This is a fine workaround for now, but will be rather irritating in the long run.  

Suggestions?

---

### Post by Tamlynmac on 2009-05-06
You didn't define what type of printer your using.

I believe in 8.04 the original default printer is PDF and stores the result in the PDF folder. 

You might also check and see if:

1. Your printer is the default printer and not PDF. I believe this should show in OO. If not check "printing" in the admin section of your menu.
2. I'm not certain but if you recently updated and had a kernel modification your print driver may no longer be supported and requires updating. Especially, if it's an HP. Go here if you need a new HP driver. [http://hplipopensource.com/hplip-web/install.html](http://hplipopensource.com/hplip-web/install.html)

I've experienced similar issues with older HP print drivers and after updating everyting just worked.

Good Luck and Hope this helps.

---

### Post by BslBryan on 2009-05-06
Thanks for the reply. :)

Unfortunately, that doesn't seem to be my problem as I have a Brother MFC 420CN, which is currently set as my default.  

Any ideas? :popcorn:

EDIT:  All right, so I suppose it was just a temporary fluke, as now OpenOffice prints fine, and I didn't change anything.  I'm worried about it potentially repeating this behavior in the future, but I suppose I'll cross that bridge when I come to it.  

Thanks again, Tamlynmac, for your advice. :-)

---

### Post by Tamlynmac on 2009-05-06
BslBryan

No, I'm sorry. I did a search for the issue in both OO and brother. Neither listed any issues (known bugs) similar to the one you posted.

Perhaps it was just a fluke. If the problem arises again you may will to check the cups error log "filesystem/var/cups/error log". It may identify what the resultant error was. Of course you could do that now, potentially it stored the error.

Good Luck

---

### Post by Pza3.14159 on 2009-05-12
I had a similar problem with my Brother printer, a FAX 2820, which intermittently spat out Postscript garbage, but then would inexplicably fix itself. Drove me nuts.
This may or may not be relevant to your problem, but since it looks like it happened to you on Tuesday, let me suggest, from [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/255161](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/255161), the following solution that worked for me:


> So it's not a problem w/ openoffice.org, cups, or the brother printer drivers. It is a bug in the `file` utility, and documented at [https://bugs.launchpad.net/ubuntu/+source/file/+bug/248619](https://bugs.launchpad.net/ubuntu/+source/file/+bug/248619).

Now, I cannot recommend a fix, but here is my workaround hack:
make a change in file /usr/local/Brother/lpd/filterMFC420CN

change:
  ```
cat > $INPUT_TEMP
```

to:
  ```
cat | sed -e 's/^%%CreationDate: (Tue/%%CreationDate: (tue/' > $INPUT_TEMP

```
This will identify a pattern that matches "%%CreationDate: (Tue" at the start of a line, and change "Tue" to "tue".

In my installation, the INPUT_TEMP was actually INPUT_TEMP1, so I used that instead, but it solved the problem.

good luck,
bruce

---

