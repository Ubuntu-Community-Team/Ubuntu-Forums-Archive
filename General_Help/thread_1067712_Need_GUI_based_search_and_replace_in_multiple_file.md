---
title: "Need GUI based search and replace in multiple files"
date: 2009-02-12
forum: General Help
---

### Post by Torning on 2009-02-12
Hi, 

I am new to linux. 

I recently managed to download a massive package of multiple viruses onto my windows install. 

To my fortune I had a linux install running on a different hard drive (I had just wanted to take a peek, since I could install it from within windows). I can recommend F-Prot virus scanner for scanning a windows install from linux.

But I digress, one of the wonderful viruses that I had the fortune to experience, is the HTML/FRAMER virus. Its not so bad as it is messy.

Basically it's an IFrame exploit, so at one point a now killed virus went through all my local HTML files and appended this little thing at the bottom:

```
...
<iframe src="http://Z**i**e**F.**pl/**rc/" width=1 height=1 style="border:0"></iframe>
</body>
</html>
```
[I](I have changed the domain above remove all "**" to visit, but [COLOR="Red"]**its a MALWARE SITE.**[/COLOR]
[/I]

Basically, this Iframe now sits at the bottom of every single HTML file I have stored locally, in case someone wants to open it in IE 5.5 that would allow me to download even more virus (How do they make these things up...).

I need a tool, that will run through all files ending with *.html and exchange: 

```
<iframe src="http://Z**i**e**F.**pl/**rc/" width=1 height=1 style="border:0"></iframe>
```

With nothing.

I have seen Perl and regular expression and I did a small test but all the special chars breaks it for me. Removing "Z**i**e**F" alone from one folder was easy (and very fast). But I would really feel more comfortable doing this kind of stuff in a GUI tool, before running through my 500 GB of documents recursively opening them and deleting and all the other bad stuff I may engage in due to lack of competence. For me the terminal is still new and so is regEx ^.^

Are there any clean Linux GUI based Search replace tools? 

I cant find one via google...

---

### Post by Torning on 2009-02-12
Looking at this: [http://www.liamdelahunty.com/tips/linux_search_and_replace_multiple_files.php](http://www.liamdelahunty.com/tips/linux_search_and_replace_multiple_files.php)

---

### Post by Mario13 on 2009-08-07
Try installing the package **kfilereplace**. It's nice and powerful.

---

