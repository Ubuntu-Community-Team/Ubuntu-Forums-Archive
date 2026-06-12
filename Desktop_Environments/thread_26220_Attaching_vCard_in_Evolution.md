---
title: "Attaching vCard in Evolution"
date: 2005-04-12
forum: Desktop Environments
---

### Post by mathjazz on 2005-04-12
How can I attach my user information (vCard) to the messages I send in Evolution, as seen [here](http://gnome.org/projects/evolution/images/screenshots/2.0/evo-mail.png)?

---

### Post by hagman on 2005-04-13
Hi,

You have to export the contact information as a vCard (Evolution -> Contacts -> Select Contact -> right mouse button -> export as VCF). Then you can attach the .vcf to your e-mail like any other documents.

Hope that helps,

Helge

---

### Post by mathjazz on 2005-04-13
Thanks, but when I send message like you suggested, the only way I can see the vCard is in "text mode". I tried sending in both, HTML and plain text format.

---

### Post by tang0 on 2007-07-03
I think I found something interesting...

I created a vCard with all data, even my photo ;)
I saved this vcard as .vcf and then attached it in a new message.
After receiving this message I have the same behavour you describe, only see text.

But... I made another test. In my contacts list selected my self. From context menu (right click) over my entry I selected "Forward contact". The result is another new message with vcard attached. Sent it and... Surprise!!!
It is showed as I want.

So... If I insert a vcf as attachment, It does not shows... but, If I "Forward Contact" from Contact list, It is showed as I want.

To solve this mistery :confused: I opened both messages and showed raw message text.
The reason was right there... 

This text is shown before vCard in the message which is not well displayed

--=-zR5fSrTyGrPSBzyI/kt8
Content-Disposition: attachment; filename="myself.vcf"
Content-Type: text/directory; name="myself.vcf"; charset=UTF-8
Content-Transfer-Encoding: quoted-printable

Here is the same part in the message with the "forwarded contact"

--=-ejTKFzLLo0mVWvHfPFym
Content-Description: VCard para myself
Content-Disposition: attachment
Content-Type: text/x-vcard; charset=UTF-8
Content-Transfer-Encoding: quoted-printable

Summary: if I insert a vcf file, the Content-Type is "text/directory" and is not well shown. If I forward myself contact in the message, the Content-Type is "text/x-vcard" and is shown as desired.

After inserting vcf file as attachment, right click over icon on attachments bar, open properties, but MIME Type field says "text/directory", is grayed and I can not edit it. ](*,)

Question:
Is there any way to say to evolution that .vcf files are "text/x-vcard" instead of "text/directory"? :confused:

thanks for your time

---

