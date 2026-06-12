---
title: "Strange Directories in home folder - Am I Hacked???"
date: 2005-10-04
forum: Desktop Environments
---

### Post by tophfisher on 2005-10-04
So about a week ago I saw a new directory in my home folder, named "1".

It had many sub folders and files, but they were all small in size and I knew I had not created the folder, so I delted the folder.

Now yester day the folder is back! The directory stucture is quite deep, but is only 8k in total size, do give you an idea, when I run ls -R on the directory it get:

Snip:

```
chrisf@fishtu:~/1$ ls -R
.:
10  11  12  13  14  15  16  17  18  19  2  20  21  22  3  32  4  5  542  6  676  7  8  9

./22:
23  24  25  26  27  28  29  30  31

./32:
209  33  34  35  36  37  38  39  40  41  42  43  44  45  46  468  47  48  49  50  51  52  57

./32/209:
210  211  212  213  214  215  216  217  218  219  220  221  222  246  267  317  386

./32/209/222:
223  224  225  226

./32/209/222/226:
227  228  229  230  231  232  233  234  235  236  237  238  239  240  241  242  243  244  245

./32/209/246:
247  248  249  250  251  252

./32/209/246/252:
253  254  255  256  257  258  259  260  261  262  263  264  265  266

./32/209/267:
268  269  270  271  272  273  274  275  276  277  278  279  280  281  282  283  284  299  302

./32/209/267/284:
285  286  287  288  289  290  291  292  293  294  295  296  297  298

./32/209/267/299:
300  301

./32/209/267/302:
303  304  305  306  307  308  309  310  311  312  313  314  315  316

./32/209/317:
318  319  320  321  322  323  324  325  326  327  328  329  330  331  332  333  334  335  336  337  338  352  355  372

```

And it goes on, and on! 

Is this a virus? What is this? Any one seen this before?

---

### Post by Perfect Storm on 2005-10-04
That seems strange, you could examin if it's virus: [http://ubuntuforums.org/showthread.php?t=25421](http://ubuntuforums.org/showthread.php?t=25421)

---

### Post by tophfisher on 2005-10-04
Good link A.I. but it looks like it is not a Virus:

----------- SCAN SUMMARY -----------
Known viruses: 40407
Engine version: 0.87
Scanned directories: 92
Scanned files: 0
Infected files: 0
Data scanned: 0.00 MB
Time: 0.727 sec (0 m 0 s)

Any other ideas?

---

### Post by skoal on 2005-10-04
Has the system performed any recent fsck runs on your /home partition?

\\//_

---

