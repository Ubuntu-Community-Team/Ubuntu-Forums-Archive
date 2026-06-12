---
title: "Copy &amp; Paste problem with self created PDF"
date: 2005-12-03
forum: Desktop Environments
---

### Post by VosaxAlo on 2005-12-03
Hi to all,

I have a very strange problem with PDF documents that I create myself with my Ubuntu Breezy notebook.
Attached to this thread I send you these documents:
1) **[COLOR="DarkRed"]Simple_text.txt[/COLOR]** is the example of normal text that I use for illustrating
     my problem
2) **[COLOR="DarkRed"]Text_to_pdf.png[/COLOR]** show you how I have printed in PDF from within gedit editor
3) **[COLOR="DarkRed"]output.pdf[/COLOR]** is the result of printing in PDF from gedit

Now, when I open **[COLOR="DarkRed"]output.pdf[/COLOR]** in evince and select all the text and finally I paste the clipboard content in gedit, the result is an unreadable text like this:

[COLOR="DarkGreen"]8
*MPI LSQI RMGSPE (IWOXST 7MQTPICXI\X X\X                   4EKMRE HM
  LMW MW Q] WMQTPI XI\X [VMXXIR MR KIHMX
- [MPP TVMRX MX XS 4(* ERH EJXIV GST] MX JVSQ 4(* MR KIHMX[/COLOR]


Please: 
anyone can let me know what is wrong?
anyone has the same problem like me?
is ghostscript related? (I have gs-esp 7.07 installed)

thank you for help me
best regards

---

### Post by gonçalo on 2005-12-03
hi.


I reproduced all your steps and got the same problems, with your files and my own. Then I tested with Abiword and OO2.

Abiword has the same problems, as gedit. I tried both evince and adobe reader 7.

OO2, although it is a mamoth didn't suffer from this problem. So if you want to generate pdfs with copy and paste you should use it.

Don't know where it comes from, this bug, but I guess you are right to suspect ghostscript.

I don't know what OO2 uses to render the pdf files but it does a good job.

Also Scribus got it done perfectly too. [edit]And it use gs for the postcript interpeter.

---

