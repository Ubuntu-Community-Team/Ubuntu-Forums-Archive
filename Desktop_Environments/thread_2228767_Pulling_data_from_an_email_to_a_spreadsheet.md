---
title: "Pulling data from an email to a spreadsheet"
date: 2014-06-09
forum: Desktop Environments
---

### Post by foxy123 on 2014-06-09
I receive a weekly email with some data and I would like to pull the data into a spreadsheet to make a graph and update it on a weekly basis. I wonder what is the easiest way to do it. I did a similar thing at work on Windows with Outlook and Excel using VBA and scripting. However, in this case I need it for personal use and I usually read my emails on my Android phone. So I do not know what would be the best solution.

---

### Post by tgalati4 on 2014-06-09
You could open an evernote account and set a filter in your mail service to forward the desired emails directly to evernote.  Then within evernote, cut and paste the data into a usable form.

For a linux solution, you would need to set the filter to send the mail to your machine using a mail reader then write a script to extract the data and plot it.

Write out the steps that you would perform to do it manually.

---

### Post by sudodus on 2014-06-09
I don't know how to do it in a phone, but in a computer with linux I would

- extract the relevant data as text lines from the weekly email
- make a script that creates a new line, that fits for the graph to be updated on a weekly basis
- append the new line into the file with lines (one line per week)
- view this text file with (comma, TAB, space ... separated values in each line) from a spreadsheet program

or

- copy and paste the relevant data as text lines from the weekly email into a spreadsheet
- make this spreadsheet create the relevant data points for the graph (could be more complicated than simply reading one line 'per week', but still possible without a VB script)

-o-

You can select different levels of automation - don't make it too fancy unless you enjoy doing it :-)

---

### Post by amanchesterman on 2014-06-10
I've no idea how to do it on a phone, but on a laptop or PC with LibreOffice I would simply highlight the data in the email and copy it to clipboard, then 'paste special' into LO Calc. Get the 'paste special' options right (e.g. if the data are separated by spaces, tabs, commas or whatever) and it's a breeze.

---

