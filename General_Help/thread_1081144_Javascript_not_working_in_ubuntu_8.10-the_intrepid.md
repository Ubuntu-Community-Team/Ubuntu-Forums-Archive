---
title: "Javascript not working in ubuntu 8.10-the intrepid ibex"
date: 2009-02-26
forum: General Help
---

### Post by bhaskar_goel on 2009-02-26
i tried running a simple script in the above mentioned ubuntu system. no output is coming. this is the script
:-

<SCRIPT language=”javascript”>
document.write("hello”);
</SCRIPT>


i have installed the sun java plugin- sun-java-5

can someone point the way?

---

### Post by 3rdalbum on 2009-02-26
Firstly, I'll just point out that Java has nothing to do with Javascript. The names are similar, but Java is a difficult language that's used to write full applications, and Javascript is an easier language that's used solely to give commands to web browsers. So installing the Java package is useful but has no bearing on your problem.

Secondly, what does your DTD (document type definition) line say? It should define the document as HTML 4.0 Transitional. If it says "XHTML", then the document.write command won't work - this is true on all platforms, not just Linux. [SIZE="1"]If you don't have a DTD, it's possible that Firefox assumes the document is XHTML.[/SIZE] (EDIT: Actually, I've just checked, this doesn't seem to be the case)

EDIT: Another explanation I've just thought of is that you might have the NoScript extension installed in Firefox, or you might have Javascript turned off in Firefox. Probably better look in the settings before worrying about your HTML document's DTD. :-)

The reason for all this? The W3C decreed that "document.write" shouldn't be allowed in XHTML. Fortunately for us, the browser developers are shunning the W3C's "standards" now, and are developing a relevant standard called HTML 5, and we can hope that it completely destroys all this XHTML nonsense and gives us back our document.write() command :-)

---

### Post by bhaskar_goel on 2009-02-26
Thanks,
I tried again and it worked.

---

