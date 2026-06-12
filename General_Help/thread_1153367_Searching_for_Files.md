---
title: "Searching for Files"
date: 2009-05-08
forum: General Help
---

### Post by Robbyx on 2009-05-08
When I search for a file I see the first part of the url not the end part so can not find where the file is saved. I remember there may be a way of altering the location string so that it is truncated but fully shown. Is there a way of doing this?

Robin

---

### Post by mb_webguy on 2009-05-09
How exactly are you searching for the files?

---

### Post by Robbyx on 2009-05-11
The actual search that caused the problem was a search for a file from within wine, but I have had the problem generally. It arise after the file is found and I click on its properties. The location is usually truncated.

---

### Post by andrew.46 on 2009-05-12
Hi Robbyx,

Are you interested in searching for files from the commandline?

Andrew

---

### Post by Robbyx on 2009-05-12
> **andrew.46 said:**
> Hi Robbyx,

Are you interested in searching for files from the commandline?

Andrew


I don't like command line instructions because they are hard to repeat the next time I need them, in a month's time. I usually do not remember the syntax or even the command. It would be different if I knew of a storage program that would drop the command lines into the terminal rather like a password manager. Pending a gui solution what command line do you suggest?



R

---

### Post by andrew.46 on 2009-05-12
Hi Robbyx,

> **Robbyx said:**
> Pending a gui solution what command line do you suggest?

I have perhaps tricked you into asking for a link to a guide I have just recently written :-)

Linux Basics: A gentle introduction to 'find'
[http://ubuntuforums.org/showthread.php?t=1128937](http://ubuntuforums.org/showthread.php?t=1128937)

The syntax actually becomes quite intuitive after a while and thus does not need to be actually *memorised*. Try the following which will quickly find all the mp3s in your home directory:

```
find $HOME -iname '*.mp3'
```

Easy?

Andrew

---

