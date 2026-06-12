---
title: "Matlab 7.5.0 XML Parser"
date: 2008-08-19
forum: Education &amp; Science
---

### Post by Claire_CH on 2008-08-19
Hi, I hope I am in the good place to post...

I am having problems using The XML parser Toolbox on Ubuntu, and I am a little lost. Has anyone tried to use it on Ubuntu?
Is there a probleme with Mex files on ubuntu?

Thanks for your time


PS: Here is the error printed by Matlab: 

??? Invalid MEX-file '/home/tswg/Claire/xmltree/@xmltree/private/xml_findstr.mexglx':
/home/tswg/Claire/xmltree/@xmltree/private/xml_findstr.mexglx: symbol mxCreateDoubleMatrix, version
libmx.INTERNAL not defined in file libmx.so with link time reference.

Error in ==> xml_parser>prolog at 363
    start = xml_findstr(str,'<',1,1);

Error in ==> xml_parser at 128
xmlstring = normalize(prolog(xmlstring));

Error in ==> xmltree.xmltree at 34
            tree.tree = xml_parser(varargin{1});

---

### Post by HumanShield42 on 2009-03-05
I had the same problem described here and I just solved it by recompiling the mex-file.  


mex -O xml_findstr.c


I know this is an old thread, but I hope this helps someone.

---

### Post by mel_lancs on 2011-09-01
It helped me ! Thanks !

It's never too late ;)

---

