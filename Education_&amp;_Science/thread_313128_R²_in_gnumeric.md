---
title: "R² in gnumeric"
date: 2006-12-05
forum: Education &amp; Science
---

### Post by Paradoxx on 2006-12-05
Hi

I've just started using Gnumeric spreadsheet, and like it quite much.
But when i make a linear regression, the R² seems to be wrong compared to Excel.

What is wrong ??

---

### Post by akniss on 2006-12-06
> **Paradoxx said:**
> Hi

I've just started using Gnumeric spreadsheet, and like it quite much.
But when i make a linear regression, the R² seems to be wrong compared to Excel.

What is wrong ??

I'd be willing to bet that Excel is what is wrong...
Read this:  [http://www.csdassn.org/reportdetail.cfm?ID=508]("http://www.csdassn.org/reportdetail.cfm?ID=508")

If you really need to find out which package is providing the erroneous value, you need to use an actual statistics package (SAS, R, Stata, SPSS, etc.).  NEVER assume Excel is correct with statistics.

---

### Post by Paradoxx on 2006-12-06
I think i've figured out what the problem is. I'm trying to find Hubble's constant (the expanding of the universe), and this data's doesn't follow a linear regression very well.
So Gnumeric skips the worst data, but still get the same eqation.
So I guess Gnumeric is smarter than Excel ;)

---

