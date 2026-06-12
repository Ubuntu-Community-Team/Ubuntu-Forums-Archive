---
title: "Help improving firefox"
date: 2011-07-28
forum: Desktop Environments
---

### Post by lucacerone on 2011-07-28
Dear all,
lately I'm experiencing a few issues with Firefox 5.0
on my Ubuntu 11.04 installation.

First of all, when I try to open pdf files, I often get a black
page and I've to try to reload it many times before I can effectively
read the pdf (even for small-size ones).

Secondly Firefox doesn't record settings about my preferred applications.
If, for example,  I want a file .torrent to be opened by deluge I have to 
enter manually /usr/bin/deluge because by default it would be opened by gedit. No matter if I select "use as default application"
the next time the issue will be present again.

Could you help me solving these few issues? (especially the first one)
I've to read a lot of pdf and it would really improve my working experience
just being able to open the page once :)

Thanks a lot for your help in advance,
Cheers, Luca

---

### Post by lovinglinux on 2011-07-28
Which application are you using to open PDF files?

You could use Evince with mozplugger plugin. Don't waste your time with Adobe, since they will not support Linux in the future versions and the current available is a bloatware. Alternatively, there are several extensions that open PDF files using Google Docs, like [gPDF]("https://addons.mozilla.org/en-US/firefox/addon/14814/"). That is what I use.

About the preferred application, try closing Firefox and deleting the file *mimeTypes.rdf* from your profile, located under ~/.mozilla/firefox/<profilename>/mimeTypes.rdf.

---

### Post by lucacerone on 2011-07-29
Hi lovinglinux, 
thanks for your help.
Unfortunately removing the .rdf file had no effect on the preffered applications :(

I've installed mozplugger but I had no occasion to go through pdf to test it yesterday,
hopefully I'll be able to do it today :)
Thanks again for your help,
Luca

---

