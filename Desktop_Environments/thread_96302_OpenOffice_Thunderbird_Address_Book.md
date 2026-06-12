---
title: "OpenOffice Thunderbird Address Book"
date: 2005-11-28
forum: Desktop Environments
---

### Post by brianglass on 2005-11-28
I have seen numerous tutorials and documentation that say that OpenOffice 2 is supposed to be able to use a Thunderbird address book as an address data souce. However, when I go to add it, the Thunderbird address book type is not listed where it is supposed to be (Evolution IS listed).

Is there something odd about the Ubuntu build of OOo, or am i doing something wrong?

---

### Post by Egghard on 2005-12-23
Same problem here,
Can´t find the database for Thunderbird in Openoffice 2
Please is there someone who van help us out?

---

### Post by dvhart on 2006-03-15
I have seen in mentioned on several places on the web that you can can use a Thunderbird addressbook in OO. I haven't been able to get that to work. In OpenOffice2 (1.9.129 - Ubuntu Breezy):

File->Wizards->Address Data Source

There is no option for a mozilla/netscape/thunderbird addressbook.

File->New->Database

Under connect to an existing databse there is no mozilla/netscape/thunderbird type.

Under OpenOffice 1.1 (1.1.5 - Ubuntu Breezy)
File->Template->Address Book Souce - just real database and textfile types
Tools->Datasources - Same as above

Tools->Mail Merge
From this document
OK
Address Data Source AutoPilot

There is actually a Mozilla/Netscape option here! I select it, click next and get this error:

The connection could not be established, Please check the settings made for the data source.

Clicking more has several fields:

Information - The connection could not be established.
Details - Please check the settings made for the data source.
Error - The connection to the external data source could not be established. No SDBC driver was found for the given URL.
SQL Status - "
Information -
Details - sdbc:address:mozilla

Is there an external sdbc driver I need to find and install or something? I haven' seen it mentioned in these tutorials anywhere.

There apparently are addressbook drivers, ie from the openoffice.org2-evolution package:
/usr/lib/openoffice2/program/libevoab2.so

I have also seen reference to libmozab2.so on the web, but haven't been able to find it it Ubuntu.  Anyone know if this has been intentionally disabled in Ubuntu?

---

### Post by wjp.reg on 2006-03-15
No Help Here, sorry :(

I was just doing a search for "openoffice address" when I stumbled on this post.  I recall there being support for Evolution in the past, but notice it's not listed when using the wizard to setup an address book.  Thunderbird is listed but I get the same error you described: > No SDBC Driver

I've got openofffice.org 2.0.2-1ubuntu2 from Sun Mar 12 01:42:09 UTC 2006

Sure would like to get ANY email address book linked to openoffice. 

Cheers

---

