---
title: "Can't open StarOffice files in OpenOffice"
date: 2005-12-30
forum: Desktop Environments
---

### Post by TheOtherShoe on 2005-12-30
After much cajoling, I have finally convinced my dad to give Linux a try on his office computer. So I'm now in the process of trying to set up Ubuntu so that it can do everything he needs it to. 

Unfortunately I am hitting a few snags. The biggest problem is that my dad keeps a lot of files in StarOffice 5 format (with an .sdw extension). OpenOffice should be able to import these with no problem. But, when I open one I am asked to select a filter, and then when I select StarWriter 5.0 I get the following error:
```
General Error.
General input/output error.
```
and nothing else happens

This is with a fresh install of Breezy, with all the current updates applied. The version of OpenOffice is: OpenOffice.org 1.9.129 (openoffice.org_1.1.5-0ubuntu1). The only idiosyncracy in the install is that I am running the 2.6.12-10-686 kernel instead of the stock 386 option. 

A possibly signifigant quirk with the StarOffice documents is that I transferred them from an older windows partition, which I believe was formatted with FAT32, to another windows machine, this time to an NTFS partition, and then finally onto the ext3 partition on which they currently reside.

I have tried installing Sun's java, and I also checked the document files to make sure their permissions are normal (644) and that ownerships are correct and whatnot. None of this seems to have made ant difference. I have also tried running OpenOffice Writer in the console - but it apparently does not output additional error information.

Can anyone give me any insight as to how I might fix this? If so, it is greatly appreciated.

---

### Post by madjo on 2005-12-30
do you still have that staroffice installation somewhere. Perhaps it is not so much as a OOo problem, but rather that the documents where somehow hosed because of the many transformation, and the fact that NTFS+linux don't always go well together :)

---

### Post by tagg3rx on 2005-12-30
perfect example of why you should always save in a non Open Office format (ie doc, xls, rtf, or XML)

Oo and Star office are nice but i have never trusted the portability of the file formats.

We had 1.4 installed on a ton of our work stations and are now going around and updating to 2.0  - in the process I'm finding alot of docs created in the old Open office that have major issues opening in 2.0.

This is realy more of a discussion for the open office forums - but i'm sure all here are intrested in Oo as well.

Just my 2cents

---

### Post by TheOtherShoe on 2005-12-31
I dug out that old copy of StarOffice and tested some documents after transferring them to the new linux partition and back, which worked so it seems that the files are not the problem.

Anyway, thank you for the replies. I may end up converting all of these files manually on another machine.

---

### Post by towsonu2003 on 2005-12-31
[QUOTE=TheOtherShoe]
Anyway, thank you for the replies. I may end up converting all of these files manually on another machine.[/QUOTE]
that sucks, file a bug with openoffice.

---

### Post by simber on 2006-01-06
Try this

sudo apt-get install openoffice.org2-filter-so52

that worked for me

let me know

:cool:

---

