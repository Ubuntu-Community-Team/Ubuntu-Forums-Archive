---
title: "Graphical Averaging Tools - Specifically Scanning Probe Microscopy"
date: 2008-08-05
forum: Education &amp; Science
---

### Post by rshuavee on 2008-08-05
I am looking for software tools to quickly average large amounts of data.  What would be nice is if I could plot 2D plots that have been exported as ASCII files and then average them together to reduce noise.  A bonus would be the ability to easily remove data points.  Right now I do all this in Excel or Calc, and it is rather time consuming.

I suspect there are general math tools to do this, but maybe there are others who use Scanning Tunneling Microscopy and have the desire to quickly average spectroscopy data.

I am using RHK Technology's SPM32 software.  The native software (and its big brother XPM Pro) will only average spectra that are in the same file.  It will not allow averaging across different files, even if spectra are combined into the same plot.

I have tried Gwyddion, but while they support RHK topography, they do not seem to support spectroscopy data.  (Because of this, I didn't take the time to see if I could average as I wanted anyway).

Is there anyone who could suggest some software tools, whether in Ubuntu or Windows?

---

### Post by meatpan on 2008-08-05
Just a heads up, this suggestion might be overkill for your purpose.

I frequently perform filtering and aggregate statistical calcs on fairly large data sets (10GB or so).  I almost always use a variation of the following idiom:

file 1 and 2 each contain a single column of #'s:

```

paste file1.txt file2.txt \
  | awk '{sum1 += $1; sum2 += $2} END{print sum1/NR "\t" sum2/NR}'

```

Filters can be added in to the awk statement, of by inserting a grep after paste:

```

paste file1.txt file2.txt \
  | grep -vi 'nan' \
  | awk ...

```

---

### Post by ahmatti on 2008-08-06
> **meatpan said:**
> Just a heads up, this suggestion might be overkill for your purpose.

I frequently perform filtering and aggregate statistical calcs on fairly large data sets (10GB or so).  I almost always use a variation of the following idiom:

file 1 and 2 each contain a single column of #'s:

```

paste file1.txt file2.txt \
  | awk '{sum1 += $1; sum2 += $2} END{print sum1/NR "\t" sum2/NR}'

```



Cool suggestion meatpan! I think though that he wants to average the columns together (into a new column) rather than compute the average of the columns? In that case you only need small modification (in case rshuavee is not familiar with awk):

```

paste file1.txt file2.txt \
  | awk '{print ($1+$2)/2}' > averaged.txt

```

I know that the original request was for graphical tools, but if you handle a lot data then it is _really_ worth of it to learn how to use the command line :)

---

### Post by rshuavee on 2008-08-06
Thank you both.  That will definitely save me time in cases when I don't need to eliminate any erroneous data points.

Identification and elimination of data points may require a graphical interface, but being new to the command line I could certainly be wrong.

Still, finding good third party software that accepts the native RHK spectra format would be a godsend.

---

