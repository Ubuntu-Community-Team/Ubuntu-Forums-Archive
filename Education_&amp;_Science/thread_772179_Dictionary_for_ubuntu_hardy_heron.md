---
title: "Dictionary for ubuntu hardy heron"
date: 2008-04-28
forum: Education &amp; Science
---

### Post by andsmi on 2008-04-28
Hi there! I need a dictionary for my ubuntu hardy heron, it needs German to Norwegian translation, and English if possible.

I tried to find some in synaptic, but it was only plugins for openoffice. It needs to be a program and not a website.

Thanks:P

---

### Post by ajgreeny on 2008-04-28
Try Stardict which may help you.

Procedure to install Stardict dictionaries
The best English dictionaries I have been able to find for Ubuntu are Stardict's "Oxford Advanced Learners" and
"Longman Dictionary of Contemporary English"
(6.1 MB and 4.5 MB respectively, when compressed).
To install them:

1) Install 'Stardict' and 'Stardict-Common' from Ubuntu repositories

2) Download your preferred dictionary from:
[http://stardict.sourceforge.net/Dictionaries.php](http://stardict.sourceforge.net/Dictionaries.php)

(I wanted the ones under the first group, "dictd...dict.org, where I also found:the Concise Britannica (which is very concise indeed. Longman and Oxford are in the lower part of the list.)

Download each tarball-file to your "home" directory.

3) From here you have to use console/terminal
a) to extract the file you have downloaded, so:
cd into the directory with your downloaded file and
Write: tar -xjvf the_name_of_your_downloaded_file

b) to move the extracted files to Stardict, so:
cd into the new directory with your extracted files
write: mv * /usr/share/stardict/dic

Now quit console/terminal, and start stardict, In Kubuntu, which I am using, you will find Stardict under "utilities". However, the procedures above should apply to any flavour of Ubuntu.

---

### Post by andsmi on 2008-04-28
Thanks! It didn't have German - Norwegian though, but it had German - English, I suppose that will do;p

---

