---
title: "Gnumeric - Errorbars won't show the right percentage"
date: 2011-10-26
forum: Education &amp; Science
---

### Post by Nightkitten on 2011-10-26
Hey everyone!


I use Gnumeric to visualize my Lab-Data, but stumbled on a problem now. I want the error bars to show the percentage (in relation to the individual cellcount) of the standard error.

I want to make a XY-chart with Cellcount against time, easypeasy so far, but now the problem: If I just use the standard error for the errorbars, the bars will get longer and longer, since the cellcount gets higher. But then the comparison makes absolutely no sense. So I calculated the percentage of the standard error in relation to the cell count, to make them comparable. But Gnumeric cant show that in any way it would make sense. Do you know which setting I have to choose to show the right percentage?


I hope I explained my problem comprehensable and really look forwavd to any suggestions. :D

Nightkitten

PS: I am a newbie to either Gnumeric and Ubuntu. My brother forced me to use ubuntu and now I'm fighting my way through. So please be a little patient with me. :oops:

---

### Post by jbrefort on 2011-10-27
Please file a bug report at bugzilla.gnome.org (product gnumeric, or, better libgoffice), and if possible, attach a sample file. This should be easy to fix.

---

### Post by jbrefort on 2011-10-27
Reading again, I don't think there is a bug there. You can use different error values for each point instead of the same error for all points. The easiest way is to evaluate each error in the sheet and use the range as input for the error values (select the entry and then drag the mouse through the cells containing the errors). Hope this helps.

---

### Post by gleedadswell on 2012-01-23
> **Nightkitten said:**
> 
I use Gnumeric to visualize my Lab-Data, but stumbled on a problem now. I want the error bars to show the percentage (in relation to the individual cellcount) of the standard error.


A spreadsheet (whether it is gnumeric, libre office or [gasp!] excel) is really not the best for scientific plotting.  Error bars are a case in point.  It is usually a struggle to get any spreadsheet to display error bars properly.

You want a scientific plotting program.  The one I'm most familiar with is grace.  Do an install via

apt-get install grace

I'm afraid it's not terribly friendly, but if you read the available documentation you should have it working fairly quickly.  You want your data, including error bar sizes, in a raw text file with a .dat extension (so you might calculate the error bar sizes in gnumeric but then have it export the data to the text file for plotting by grace).  You can then import it into grace as "block data".

Another option is gnuplot, which I haven't used in a long time but I don't think it is even as friendly as grace.

---

