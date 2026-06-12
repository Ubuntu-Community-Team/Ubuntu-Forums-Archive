---
title: "Form Builder--application OpenSource and Free"
date: 2009-10-11
forum: Education &amp; Science
---

### Post by shuttleworthwannabe on 2009-10-11
I am looking for easy to use form builder for my project at school--I have about 10+ questionnaires that collect data from Children and their mothers. I want to collect data on paper and then later enter this data on the web-based tool. I have seen a number of tools on the web, e.g. Wufoo, surveymonkey--but these things are very expensive; Google Docs Forms comes close, but there is no way to make this a data entry tool. Also I wish to relate the children with the mothers (1 mother--many children relationships) using unique ID, and relate function. Wufoo I think has this facility.One other requirement, is that multiple data entry clerks can enter the data at same time. Note: i do want to install a server on my PC--I am looking for an online tool. Data must be accessible in DBF or CSV format.

Anyone know what is out there I could use?

---

### Post by shuttleworthwannabe on 2009-10-15
Hi Guys, anyone?

---

### Post by shuttleworthwannabe on 2010-01-03
One more try albeit 3 months later..anyone?

---

### Post by ugm6hr on 2010-01-04
If such a tool existed, it would be very popular indeed. Unfortunately, I don't know of any.

For medical purposes, this kind of database / data collection application is distributed as an EMR (Electronic Medical Record), albeit often with a much more complex data structure.

I think the only way to do this with a custom-made database would be by programming the PHP yourself on to a MySQL (or similar) server.  Even then, I'm not 100% sure how you could get the MySQL data into a csv file.

If it is just an issue of collecting raw data, some Wikis allow forms.  I know Foswiki will allow you to create appropriate forms.  However, the one-to-many relationships may be problematic, and I do not think it stores form data in an easily retrievable fashion.  Maybe do some googling on alternative wikis to see if they might offer a solution?

---

### Post by shuttleworthwannabe on 2010-01-04
Thanks for the suggestion; I will explore further.

---

### Post by gunksta on 2010-01-05
Disclaimer - I have never used either of these, but I do intend to use them ---- and soon. I want to do something similar to what you describe, and replace the monstrosity known as MS Access.

[LimeSurvey]("http://www.limesurvey.org/")
[EpiData]("http://www.epidata.dk/")

I'd like to hear how this project works out for you.

---

### Post by shuttleworthwannabe on 2010-01-06
I am currently using Epidata--it is single most vaulable tool in the field of work that I do. its biggest limitation is that it not be used a amultiuser data entry tool. Only one person can enter data at atime--and not networkable.

---

### Post by hsweet on 2010-01-06
If you have a web host,and know how or are willing to learn,  you can use mysql and php to build an on line survey.  Or install Moodle, and add the feeback module.

---

