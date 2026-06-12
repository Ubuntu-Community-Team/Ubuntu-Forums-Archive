---
title: "How to NOT embed fonts in PDF generations from OO writer?"
date: 2009-02-19
forum: General Help
---

### Post by bixejo on 2009-02-19
I'm using the option "File => Export to PDF" to generate PDF files from OpenOffice writer. Any time I do so, it embeds all fonts I'm using, which is only one and very common, so I'd like to **not** embed that font to reduce PDF file size as I should send it to a mail list which imposes serious size constraints.

Any clue on how I could do this, please?

Thank you in advance.

---

### Post by fragos on 2009-02-19
Fonts may be common but not necessarily present. Windows XP, Vista, Linux and Mac all default to different font sets. If you don't need tight control of the appearance I suggest you tansfer in a generic file format like RTF which is well supported in Windows, Mac and Linux. Local fonts would be used. Another option would be HTML.

---

### Post by bixejo on 2009-02-19
> **fragos said:**
> Fonts may be common but not necessarily present. Windows XP, Vista, Linux and Mac all default to different font sets. If you don't need tight control of the appearance I suggest you tansfer in a generic file format like RTF which is well supported in Windows, Mac and Linux. Local fonts would be used. Another option would be HTML.
Thank you for your reply, Fragos.

I'm afraid RTF and HTML are not choices, as the document has some images.

I know that different platforms default to different font sets, but as far as I know PDF viewing tools usually apply some font substitution table that tries to approach the font named in the document to the "closest" one available. So if the document refers to font "Times" it's highly likely that a very similar font would be chosen, am I wrong?

Thank you again,

---

### Post by fragos on 2009-02-19
> **bixejo said:**
> Thank you for your reply, Fragos.

I'm afraid RTF and HTML are not choices, as the document has some images.

I know that different platforms default to different font sets, but as far as I know PDF viewing tools usually apply some font substitution table that tries to approach the font named in the document to the "closest" one available. So if the document refers to font "Times" it's highly likely that a very similar font would be chosen, am I wrong?

Thank you again,

You may be right about images and RTF but not so with HTML. Don't forget the IMG markup and CSS backgrounds. With HTML you'd either be hosting and only send a link or sending a folder with all the various files to create the end result. In that sense PDF is perhaps more convienient.

---

### Post by bixejo on 2009-02-24
> **fragos said:**
> You may be right about images and RTF but not so with HTML. Don't forget the IMG markup and CSS backgrounds. With HTML you'd either be hosting and only send a link or sending a folder with all the various files to create the end result. In that sense PDF is perhaps more convienient.
Great to hear that you agree with me about PDF is the best choice :p

As for HTML, I already considered what you mention about sending a whole folder with all the necessary data to recreate the end result, but I discarded that idea as the recipients' computing skills are very limited in most cases so I cannot be sure whether they would be able to see the result.

Best regards and thank you for your help,

---

### Post by Psyphre on 2009-04-19
Sorry to hijack the thread but its sorta similar to what I want to ask.

Im having the opposite problem as you have Bixejo, i WANT to embed fonts,  but OO doesnt seem to! its incredibly frustrating. How did you embed?

---

### Post by bixejo on 2009-04-19
> **Psyphre said:**
> Sorry to hijack the thread but its sorta similar to what I want to ask.

Im having the opposite problem as you have Bixejo, i WANT to embed fonts,  but OO doesnt seem to! its incredibly frustrating. How did you embed?
I don't do anything special to embed fonts. Just use the menu "File => Export in PDF format", and OO will export the file with all used fonts embedded.

In the dialog window that will appear when you use this menu option you'll see several tabs where you may specify exporting options. Fonts are always embedded regardless the options you specify. You may however check the box "PDF/A-1" in the "General" tab. In that case it will include a lot of information in the PDF file, at the cost of substantially increase the file size.

Hope this helps. Regards,

---

### Post by Psyphre on 2009-04-19
thanks for hte response. I sent a pdf to a friend and I remember them sending me a screenshot. The pdf didn't look the same as in my openoffice.

I'll make a pdf will loads of different fonts and test it on a windows machine. I'll also try that A-1 option you mentioned. Thanks.

---

