---
title: "Making Haploview work (The answer, not the question)"
date: 2007-09-21
forum: Education &amp; Science
---

### Post by mycotropic on 2007-09-21
For those of you who do genetic analysis using Haploview;

Here's the UNIX .jar;
[http://www.broad.mit.edu/mpg/haploview/download.php](http://www.broad.mit.edu/mpg/haploview/download.php)

The problem is that running;

java -jar Haploview.jar 

produces an error.

The answer is that Haploview will only run under Sun Java, available in synaptic, and not under the native Ubuntu Java . While this may be idiotically simple to some, I could have had an additional ~2 hours to work on my analysis last night had I known this. Oh and when I searched these forums for haploview I got no hits.

If anyone IS using Haploview and is pissed that it won't output individual level haplotype data with probabilities of assignment, please feel free to post here about how YOU get around this annoyance. I mean, who the hell does univariate genetic studies anymore?

---

### Post by hypotheses on 2008-11-23
As of today on x86_64 machine, the Sun Java is going to give you a headache instead. Haploview will start with an error message, nothing seems to work; whereas, openjdk works really well. The Sun Java will give you a slightly better looking GUI than openjdk, but this gives no advantage if Haploview doesn't work. 

So, to save other additional time, don't waste time with Sun Java if you are running linux on x86_64

---

### Post by mbmiller on 2010-02-11
I'm using Karmic (9.10) and I have both Sun and Open versions installed (according to Synaptic).  When I run this...

java -jar Haploview.jar

...I get an error telling me that a library is not found.  It turns out that "java" in the path is the Open version.  So I tried the Sun version like this...

/usr/lib/jvm/java-6-sun-1.6.0.16/jre/bin/java -jar Haploview.jar

...and it worked great.  That's all I know.  Maybe this is changing with versions of Haploview or with versions of Ubuntu.

---

### Post by mbmiller on 2010-02-11
I was using Ubuntu 64 when the Open java failed but the Sun java worked.  When I went to a 32-bit Ubuntu Netbook Remix, this was no longer true -- the Open version worked with Netbook Remix while the Sun version did not.  So it might be a 32-bit v. 64-bit difference.  I was using Haploview 4.2 in every attempt.

---

### Post by hypotheses on 2010-11-17
I re-install new Ubuntu 10.10 on a 86x64 machine with open JDK, and haploview 4.2 works fine. So, this seems to confirm the speculation that the problem with Sun Java seems to be with the system architecture.

---

### Post by Letrell on 2011-12-28
I have a file in SPSS format with info on 4 SNPs of the NCOA3 gene; i would like to analyze this file in haploview. Does anyone know of any free software i can use to convert this file to one haploview accepts?

Also, i tried to load the info automatically into haploview by using the HapMap download tab on haploview, and it downloaded the many SNPs of NCOA3 gene, but the 4 SNPs i am interested in were missing from the output info HapMap Download downloaded for me. I had inputted all required parameters. Does anyone know why? Thanks

---

