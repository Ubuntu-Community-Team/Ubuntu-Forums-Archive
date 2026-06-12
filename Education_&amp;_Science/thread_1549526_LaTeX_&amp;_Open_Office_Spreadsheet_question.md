---
title: "LaTeX &amp; Open Office Spreadsheet question"
date: 2010-08-09
forum: Education &amp; Science
---

### Post by agm. on 2010-08-09
Hello,

I have been using LaTeX to write up my dissertation, but I have to use several different statistical programs to do most of the analysis depending upon the specific model specification.  One of the things that I've started to do (which might seem silly to some) is to use OOO spreadsheets to "make" my LaTeX tables since it is so much easier to insert columns and rows.  In this way, I can take my table directly from the statistical package, import it into Open Office with fixed column width and get all of my estimates rounded to the specific length necessary quite easily.  I then can insert columns of "&" and other necessary LaTeX commands without a lot of work.

This method works really well for me, but I have one complaint that I was hoping someone could help me solve:

When I paste my table into my .tex file, each cell is delimited by a "tab".  Is there a way to have this be delimited only by a "space" instead?  It slows down my workflow to have to go back and remove the tabs, but this method is still quicker (with fewer errors) than inputting the table directly into my .tex file by hand.  I have tried to paste the results into gedit first, then paste it into Kile (my LaTeX editor), but this does not work.

I know that most statistical packages can write tables and such to LaTeX, but for most of my research, I'm having to pick and choose only portions of results that need to be shown in different ways, so having the statistical package "write" a .tex file of the results is not the best option since I omit many of the reported results (like confidence intervals).

So if anyone knows of a way to fix this problem, I'd be really grateful!

Thanks!

---

### Post by Boffie on 2010-08-10
If you save your spreadsheet as .csv and check "Edit filter settings" you can choose "space" as your field delimiter. If you open the .csv file with a text editor, there will be spaces between your columns. Maybe this is faster...

---

### Post by jbrefort on 2010-08-10
You might use gnumeric instead of OOo spreadsheet.

---

### Post by agm. on 2010-08-10
> **Boffie said:**
> If you save your spreadsheet as .csv and check "Edit filter settings" you can choose "space" as your field delimiter. If you open the .csv file with a text editor, there will be spaces between your columns. Maybe this is faster...

This gets me much closer.  Thanks for the help.  However, now I have the problem that when I edit the filter settings, and load the .csv file into a text editor, I get "" surrounding all my text.  

So as an example, I'd have a line of the table and instead of it reading:

```
Variable  & 1.234 & 5.678 & 9 \tabularnewline
```It reads:

```
"Variable"  "&" 1.234 "&" 5.678 "&" 9 "\tabularnewline" 
```I tried to play with the "Edit Filter Settings", but for text, it only had two options, delimiting text with " or ' ... 

[QUOTE=jbrefort] You might use gnumeric instead of OOo spreadsheet.      [/QUOTE]

I'd like to fix this problem through Open Office if it is possible.  I haven't used gnumeric and it is not installed right now and while it wouldn't be that big of a deal to install it, I would think that it would have the same problems as I'm encountering now.  

If you've used it and can provide details on how to get it to do what I'm asking, I will definitely try it!


Any further suggestions?

Thanks!

---

### Post by Boffie on 2010-08-11
It indeed only shows " and ' as options for delimiting text, but in fact you can select and delete it. If you do this your text will not be surrounded by "".

---

### Post by agm. on 2010-08-11
> **Boffie said:**
> It indeed only shows " and ' as options for delimiting text, but in fact you can select and delete it. If you do this your text will not be surrounded by "".


Thanks for the heads up!  This provides a quick method for what I was trying to do!  I didn't know you could delete the " or ', but now that I do that, this provides the quickest method.

Thread marked as solved!

---

