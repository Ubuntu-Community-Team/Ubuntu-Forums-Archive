---
title: "MIcrosoft Access 2003"
date: 2009-04-14
forum: General Help
---

### Post by gdonwallace on 2009-04-14
I hope I am in the correct forum for this question.

I am running Ubuntu 8.10. I have MS Access installed on a windows box that is accessed by everyone in our location (about 20 people, so no big load) I use Terminal server to get onto the box and do what I need in Access. 

Today I decided to run a query to find out if there are any duplicates in the master table.  What I found was really weird.  I saved the file (CSV) on a network drive, moved it to my Ubuntu box and opened it in OOo Calc.  I found a entry that said that it was in my master table 21 times.  I re-ran the query and did the same thing again, just to make sure something wasn't a little freaky when I ran the query the first time.  Same results.  So I manually searched for the information in the master table, and it is there only 1 time.  I opened the exported CSV file and searched for the information, and it shows a count of 1 in the CSV.  I then switched over to my Ubuntu box, navigated to the windows share for that directory and opened it with a text editor.  Found that it was listed with a count of 1.  But when I moved that file onto my actual Ubuntu box, opened it in text editor, the count changes to 21.  I can't see anything that should be causing that.  Moving from Windows to Ubuntu should not change the data, as I do it all day long.

Any thoughts?

(I Know it's confusing, sorry)

Thanks

---

