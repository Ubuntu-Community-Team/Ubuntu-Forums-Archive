---
title: "Problem with bullets when saving OpenOffice to RTF"
date: 2009-06-16
forum: General Help
---

### Post by SteveDee on 2009-06-16
I have a problem when saving documents created in ooWriter to RTF.

If the document contains a list of bullet points, some of the bullets are removed.

I can reproduce this on 3 computers (all run OpenOffice 3.0.1 on 9.04) as follows:-

1. create a simple bullet list in ooWriter.
2. save file in RTF
3. close document
4. re-open document

See attached.

I don't get this problem running OpenOffice 2.4 Portable on a memory stick on a Windows pc.

Any ideas?

---

### Post by coffeecat on 2009-06-16
I can confirm I get something similar in Open Office 3.01 in MacOS. Picture 1 is the odt file made with OOo. Picture 2 the rtf file reopened in OOo. It gets worse with other word-processors. Picture 3 is the rtf created by OOo and opened in Text Edit (Mac version of Gedit) and Picture 4 is in Pages (WP part of iWork).

I would guess this is an issue in OOo version 3. If I get time I'll try out OOo3 in Windows later and post back.

---

### Post by coffeecat on 2009-06-16
I'm posting from Vista ( :oops: ) atm. I've made an rtf file with Open Office Writer 3.01 exactly the same way I did in MacOS and got exactly the same result, so I won't waste forum space by posting more screenshots. This is not the vanilla OO, by the way, but the Go-OO build by Novell. So it does seem like an OO version 3 problem.

However, curiouser and curiouser...

First time round I absently-mindedly double-clicked on the .rtf file which made it open in MS WordPad, and in WordPad the formatting appears correct with all the bullets in place.

Hmmm. :-k

---

### Post by SteveDee on 2009-06-16
> **coffeecat said:**
> ...I would guess this is an issue in OOo version 3. If I get time I'll try out OOo3 in Windows later and post back.

Yep, you are right. I just installed OpenOffice on WinXP and it has the same problem.

AbiWord looks OK with rft so I guess I'll use that for now.

---

### Post by SteveDee on 2009-06-16
> **coffeecat said:**
> ... I absently-mindedly double-clicked on the .rtf file which made it open in MS WordPad, and in WordPad the formatting appears correct with all the bullets in place.

Hmmm. :-k

I opened my ooWriter rtf in;
 - WordPad and found it retained the indents, but lost all the bullets (could be a font problem).
 - AbiWord and found it had 1st bullet & indent, but lost the rest (same as ooW)
 - In Word 97 (sorry) and got the attached...

...maybe emailing your CV in rtf is not such a good idea.

---

### Post by coffeecat on 2009-06-16
> **SteveDee said:**
>  ...maybe emailing your CV in rtf is not such a good idea.

Did you try saving as .doc in Open Office? I tried that and iirc correctly the bullets were retained OK. I would have thought that a recipient would have been happy with .doc - it tends to be used as a "standard". :( The only thing to watch is that page breaks can occur in different places using different word-processors. I even had page breaks appear in different places in the same .doc document using the same version number of OO in different Linux distros on the same computer using the same printer. ](*,)

Or could you use .pdf files? OO can export to pdf. I'm a bit out of touch with these things so I don't know whether prospective employers will accept PDFs, but you'd think they would. They only have to double-click on them, whatever OS they use.

---

### Post by SteveDee on 2009-06-16
> **coffeecat said:**
> ...Or could you use .pdf files? OO can export to pdf. I'm a bit out of touch with these things so I don't know whether prospective employers will accept PDFs, but you'd think they would. They only have to double-click on them, whatever OS they use.

I did actually send a pdf to preserve my glorious formating. But job agencies want .doc or .rtf so they can strip out your contact details and replace with their logo.

Yes, ooW normally works well when saving to .doc, but unless you test it every time, its a bit risky.

Anyway many thanks for your input.

---

