---
title: "OpenOffice Writer Freezes on Dapper x86"
date: 2007-02-26
forum: Desktop Environments
---

### Post by snoopy1 on 2007-02-26
I have been running Dapper 6.06 since it came out, and I love it.  OpenOffice 2.0.2 is currently available with Dapper, and I use the Writer function extensively - a great software package!

Recently I have been creating some lengthy documents (~100 pages), and there are times when the document gets to a point where certain changes will cause OpenOffice to grab 95% of the CPU, and it will not let go (short of a KILL) no matter how long I wait.  If I kill the process, it does go away and does not cause Dapper any problems.

I have one document where I can reproduce this problem VERY easily and consistently.

After searching the Internet for a few hours and finding no solution that worked for me, I tried an experiment. I copied my problem document to Windows, opened it with OO 2.0.1 and 2.1 (I installed each version separately and independently), tried the steps that cause the document to lock up OO on Linux, but on Windows, OO did not lock up.

Next I uninstalled OO 2.0.2 from Dapper and installed OO 2.1 that I got from [www.openoffice.org](www.openoffice.org).  (I used alien to convert the .rpm's to .deb's.)  When I opened my problem document with OO 2.1 on Linux and tried my test, once again OO froze.

Additionally, I have tried this test on three different computers running OO 2.0.2 and Dapper, and on all three, OO locked up.  One of these computers is a Compaq Presario laptop with an AMD64 processor, and the other two are desktops with AMD 32-bit processors.  In all cases, I am running the i386 version of Dapper with Kernel version 2.6.15-28-386.  All three computers have 1 GB of memory.

Has anyone else run into this problem?  Is there s solution or a work-around?  If it would be helpful, I can provide the problem document along with the four click method that guarantees that my Linux OO will freeze.  If any other info would be helpful, please let me know.

Any help would be greatly appreciated!

---

### Post by moore.bryan on 2007-02-26
*have you tried checking out the openoffice forums?  (*[SIZE=-1]www.oooforum.org/[I])
they've proven helpful in the past for me...
[/I][/SIZE]

---

### Post by flossgeek on 2007-02-26
Could you add the document so we can test it, if it happens on a lots of machine we have an issue on our hands. We can't have OOO working on win32 better than Ubuntu that would just be wrong.

---

### Post by snoopy1 on 2007-02-26
Here's the document.  For me to create the problem, I open the document (once open, you'll find yourself in the middle of a table), then I click <Table> <Insert> <Row> <OK>.  Then BANG!  It strangles my CPU until I kill it.  It happens every time for me without exception.

---

### Post by flossgeek on 2007-02-26
The document isn't present I'm afraid.

---

### Post by snoopy1 on 2007-02-26
I see now why.  There was an error when I tried to upload the file.  It said, "Your file of 48.2 KB bytes exceeds the forum's limit of 19.5 KB for this filetype."  How else can I get the file to you?

---

### Post by flossgeek on 2007-02-26
Email it to me, if you click my blog link and click contact me you will see my email, please zip the file first though. Thank you.

---

### Post by snoopy1 on 2007-02-26
Thank you!  I just e-mailed the document to you at the address I found in your vcard.  I look forward to your response.

---

### Post by flossgeek on 2007-02-26
hmm i dont seem to have recieved it...

---

### Post by flossgeek on 2007-02-26
Its okay ignore me I have it now, I will get back soon...

---

### Post by snoopy1 on 2007-03-01
Since the last post, flossgeek and I have had many e-mail exchanges.  Flossgeek did a lot of research and was indeed able to reproduce the problem I was having.  Flossgeek also noted that the problem does not exhibit itself when running OpenOffice 2.1 on a fresh (i.e., not upgraded) install of Edgy.

One test I conducted was to remove OpenOffice 2.0.2 from Dapper and then use alien to convert the .rpm's of 2.1 from openoffice.org to .deb's.  I then installed OO 2.1 on Dapper, and I saw that I still had the freezing problem.  Consequently, between Flossgeek's observations and my own, I'm beginning to suspect that the problem is in Dapper not in OO.

Should anyone be interested in continuing to figure out this problem, I have attached a smaller document to this post that exhibits the same freezing problem.  To reproduce the problem, position the cursor at the yellow-highlighted point in the document that reads "Position the cursor here and insert a row" and then click <Table> <Insert> <Row> <OK>.  In my case, as mentioned above, OO seizes the CPU, and nothing but a kill can stop it.

I will keep an eye on this post for a while to see if anyone comes up with anything.  Also, if I discover more, I will update this post.

Many thanks to flossgeek for all the help!

---

### Post by flossgeek on 2007-03-01
No problems, **open source** matters, right. :)

Whilst even more interesting I have the opposite to you Snoopy. I run Edgy on my Desktop machine. I removed the default openoffice.org that came with edgy and then reinstalled openoffice.org 2.1 using alien to convert the rpms to debs. This openoffice.org suffers from the bug with the document attached to snoopys post of just crashing. This I can understand as perhaps the Alien conversion can produce errors causing the issue.

However on my laptop I have not installed openoffice.org 2.1 and kept the default version that came with edgy and the document Snoopy has supplied doesn't suffer from a crash. Which is good for me as its the default install but in snoopys case his default install of open office on dapper suffers the bug.

---

