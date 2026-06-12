---
title: "VMD, MultiSeq, STAMP"
date: 2009-08-26
forum: Education &amp; Science
---

### Post by loska on 2009-08-26
Hi,
I'm learning how to use VMD, by following this toturial: [http://www.ks.uiuc.edu/Training/Tutorials/vmd/tutorial-html/node6.html](http://www.ks.uiuc.edu/Training/Tutorials/vmd/tutorial-html/node6.html)

When I try to execute point 6, the error message appears:

The STAMP alignment failed with the following
error message:
couldn't open
"/usr/tmp/multiseq-7923878160269874.start.domain
":no such file or directory"


> 
Unable to open file /usr/tmp/multiseq-7923878160269874.0.pdb for writing
ERROR) Unable to open file /usr/tmp/multiseq-7923878160269874.0.pdb of type pdb for writing frames.
Unable to open file /usr/tmp/multiseq-7923878160269874.1.pdb for writing
ERROR) Unable to open file /usr/tmp/multiseq-7923878160269874.1.pdb of type pdb for writing frames.
MultiSeq Error) 
couldn't open "/usr/tmp/multiseq-7923878160269874.start.domain": no such file or directory
    while executing
"open "$tempDir/$filePrefix.start.domain" w"
    (procedure "::STAMP::alignStructures" line 58)
    invoked from within
"::STAMP::alignStructures $regionSequenceIDs $scan $scanslide $scanscore $slowscan $npass"



How can I solve this problem?

(VMD-1.8.7beta5, Ubuntu 9.04)

---

