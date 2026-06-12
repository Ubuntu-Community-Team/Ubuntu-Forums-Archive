---
title: "how to import multiple vcf files in evolution?"
date: 2005-06-28
forum: Desktop Environments
---

### Post by venkman on 2005-06-28
hello, i'd like to import a directory full of vcf files, but in evolution it's just possible to import a single file - I've got about 50 files, I don't wan't to do this procedure 50 times ;)
 
is there a possibility to import more than one vcf file at once?

---

### Post by bahadir on 2005-07-02
[QUOTE=venkman]
is there a possibility to import more than one vcf file at once?[/QUOTE]
do a
**cat *.vcf > contacts.vcf **in a shell and import the contacts.vcf as single file in evolution. and use the right pipe direction (-;

---

### Post by Levitation on 2007-03-14
"do a
cat *.vcf > contacts.vcf in a shell and import the contacts.vcf as single file in evolution. and use the right pipe direction"

Could you break it down into simple steps for a n.o.o.b.i.e? I don't know what "cat*" is. When you say "in a shell" do you mean in a text editor?

Thanks!

BTW I've always wondered about the origins of newbie or noobie, then it flashed in my mind:
New Out Of (the) Box (ie)! So maybe "Noober"?

---

### Post by Yeti can't ski on 2008-04-18
I believe you ended up with 50 vcards because you couldn't import properly a ".csv" file from Outlook, right? 

I had that problem and found a dumb non-brilliant non-geek way of solving it. 

In several forums I read the suggestion of first installing Mozilla in the Windows system to do a conversion of the “.CSV” file, but that seemed too troublesome. Indeed, Gmail will easily do the same trick.

- Export your contacts from Outlook to as a regular ".CSV" file;
- Import those contacts into Gmail (in webmail mode);
- Export from Gmail to a ".VCF" file (it will be a single file); and finally
- Import ".VCF" file to Evolution. 

The "bonus" is that Gmail will automatically cancel doubled/repeated entries. Really great. I hope someday Evolution will do all that by itself.

If instead you absolutely cannot go back to Outlook to produce a ".CSV" file and reaaally must use the 50 vcards then you could give a try on one of those vcard organizers software for (argh!) Windows. Or, it may be the case to add each card individually to Evolution. :-(

Good luck.

---

### Post by allquixotic on 2008-05-20
> **bahadir said:**
> do a
**cat *.vcf > contacts.vcf **in a shell and import the contacts.vcf as single file in evolution. and use the right pipe direction (-;

Brilliance! Lunacy! Both! I had no idea you could simply 'cat' multiple VCF files together and have it still come out as a valid VCF file! That isn't true of many other file formats. But now I've learned something that will save me lots of time ;-)

Thanks!

Sean

---

