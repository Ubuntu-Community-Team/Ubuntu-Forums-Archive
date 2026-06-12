---
title: "Count &quot;up&quot; timer is what I'm looking for"
date: 2009-04-30
forum: General Help
---

### Post by BooNality on 2009-04-30
Hey everyone,
So the timer applet is decent but what I actually need the ability to do is count the amount of time that has passed since a date and time.  I need the ability to count up to see how long it has been since a date and time that has occured in the past.

I can't find anything for ubuntu, does anyone have anything that works like that?

---

### Post by blazemore on 2009-04-30
There's a good app for this online, but it isn't realtime, and it only does up to the precision of days:
[http://www.timeanddate.com/date/duration.html](http://www.timeanddate.com/date/duration.html)

---

### Post by VCoolio on 2009-04-30
There is a perl script [here]("http://conky.linux-hardcore.com/?page_id=363"), which is meant as countdown in conky but also does "up" time once the deadline has passed, up to seconds. You can run it from the commandline e.g. count back to January 1st, 12:00:00:
perl howlong.pl "01 01, 09 12:00:00"
The output is gave me:
3m 4w 1d 0:43
or import it in whatever app you want. You need perl of course and another small dependency which is also mentioned in the link I gave you. As you can see it counts months as 30 or 31 days, so the output can be 3 months 4 weeks etc which sounds a little strange. But it works.

---

### Post by Herman on 2009-04-30
I would use an Open Office.org spreadsheet for that.

You can see the available functions for making your spreadsheets do tricks in you open up a spreadsheet and then click 'Help'-->'OpenOffice.org Help', and look under the heading: 'How to Work With OpenOffice.org Calc'. There should be a link 'List Functions by Category', and after you click on that, you should see the category 'Date & Time'.

For example, you might have a spreadsheet with eight columns, 'A' to 'H'.
In cell A1, you insert your date, and in cell B1, your time for the answers to be calculated from.

Cell A3 contains: =TODAY()
and cell B3 contians: =NOW()

C2 might contain: =(YEAR(A3-A1)-1900)
D2 might contain: =MONTH(A3-A1)-1
E2 might contain: =DAY(A3-A1)-1
F2 might contain: =HOUR(B3-B1)
G2 might contain: =MINUTE(B3-B1)
H2 might contain: =SECOND(B3-B1)

Just check to make sure that works correctly, I'm a little bit sleepy right now and may have made a mistake somewhere, but that should give you some ideas to get you started at least.


	 	 	 	 	  [B]
[/B]

---

### Post by BooNality on 2009-04-30
> **Herman said:**
> I would use an Open Office.org spreadsheet for that.

You can see the available functions for making your spreadsheets do tricks in you open up a spreadsheet and then click 'Help'-->'OpenOffice.org Help', and look under the heading: 'How to Work With OpenOffice.org Calc'. There should be a link 'List Functions by Category', and after you click on that, you should see the category 'Date & Time'.

For example, you might have a spreadsheet with eight columns, 'A' to 'H'.
In cell A1, you insert your date, and in cell B1, your time for the answers to be calculated from.

Cell A3 contains: =TODAY()
and cell B3 contians: =NOW()

C2 might contain: =(YEAR(A3-A1)-1900)
D2 might contain: =MONTH(A3-A1)-1
E2 might contain: =DAY(A3-A1)-1
F2 might contain: =HOUR(B3-B1)
G2 might contain: =MINUTE(B3-B1)
H2 might contain: =SECOND(B3-B1)

Just check to make sure that works correctly, I'm a little bit sleepy right now and may have made a mistake somewhere, but that should give you some ideas to get you started at least.


	 	 	 	 	  [B]
[/B]

Oh my... why didn't I think of that.  Not even a month ago I developed a MS excel spreadsheet that has the date the spreadsheet is opened at the top of column A and then each calendar day afterward for 30 days below it based on a formula so it never had to be changed.  I did that so my wife could print blood pressure sheets to document her blood pressure for the dr. office.  Now we're doing kick counts and having contractions :)  Much more fun. 

Thanks for the info, I can probably get it working this morning :)

---

### Post by radsqd on 2009-04-30
there is also days untill which is a google gadget. Details on [http://leancode.com/daysuntil/](http://leancode.com/daysuntil/)

---

