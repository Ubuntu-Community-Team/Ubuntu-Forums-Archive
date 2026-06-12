---
title: "Importing svn log output into spreadsheet"
date: 2009-02-26
forum: General Help
---

### Post by brianbourke75 on 2009-02-26
So at my place of employment I often have to produce svn logs for changes to various branches of code that we work on for the testing group so that they can develop a test plan based on the changes.  They would like for this to svn output to be in a spreadsheet, so I have had to do this by hand.

Does anyone know of any tools to make this a bit more automated?  Something which can take the svn log output (in all likelyhood formated into xml) and either converting this to a csv or perhaps a filter in open office which will directly import it?

thanks,
B

---

### Post by deeem119 on 2009-02-26
Does it absolutely, positively need to be a spreadsheet, or would a  simple table layout suffice?

If so, it shouldn't be too hard to code an XSL stylesheet for the XML to make it more friendly to look at.

---

### Post by FluffyElmo on 2009-02-26
I don't have a svn log file handy to look at, but I think your best bet would be to convert the XML to CSV and then import into OpenOffice. You could create an XSLT stylesheet to do the conversion or there may be utilities already out there that would be suitable. Here is a blog post that may be helpful? [http://blog.mclaughlinsoftware.com/oracle-sql-programming/how-to-convert-xml-to-csv-and-upload-into-oracle/](http://blog.mclaughlinsoftware.com/oracle-sql-programming/how-to-convert-xml-to-csv-and-upload-into-oracle/)

Good Luck!

---

### Post by brianbourke75 on 2009-02-26
Yeah, I was reading online about XSLT, and I was hoping to avoid this if at all possible.  It's looks fairly complicated and since I have never touched this before, I was hoping someone would have something in place for this.

It does not have to output to a spreadsheet directly, but that is the end goal of this since the group who will be receiving the output will be using excel.

B

---

### Post by FluffyElmo on 2009-02-26
Just adid a few Google searches and assuming this isn't your blog this may be useful ;)

[http://www.vectorns.com/blog/3-svn-log-parser-from-xml-to-csv-using-perl](http://www.vectorns.com/blog/3-svn-log-parser-from-xml-to-csv-using-perl)

---

### Post by brianbourke75 on 2009-02-26
I found that blog as well, he is using a closed soure windows program called xml2csv to be doing most of the heavy lifting, the the perl script is hardcoded for his library.  It's a neet idea of wrapping everything together, but I would still need to be able to port the xml2csv to linux.

---

