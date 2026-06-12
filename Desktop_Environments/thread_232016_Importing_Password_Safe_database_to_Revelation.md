---
title: "Importing Password Safe database to Revelation"
date: 2006-08-08
forum: Desktop Environments
---

### Post by finite9 on 2006-08-08
I have used Keepass Password Safe in Windows for quite some time, and now I switched to Ubuntu, but I want to use the Revelation password manager instead as it integrates better with gnome.  How do I import a keepass database file into Revelation?  It does not seem to be able to import the keepass KDB file (not recognised) so I exported the database in Keepass as XML but revelation doesnt recognise the XML structure.

Are there any tools that can convert the XML structure of keepass to reveltaions format?

UPDATE: Well I manually converted the Keepass Password Safe XML exported file to Revelations XML format (which is a bugger as Revelation has very strict rules for permissible values) and it works ok to import that file, but I found out during conversion that it doesn't support swedish characters and that passwords are visible in memory when database is open, so im sacking Revelation completely...I will use Keepass instead, despite not being a Gnome app and having to install Qt libs.  Importing an XML file will not be a manual affair and it is loads more secure than revelation.

--finite9

---

### Post by julius malchovitch on 2007-05-04
I'd really like to convert all my keepass passwords  to revelation as well.

If I had the xsd schema of the Keepass xml output format and the schema of the revelation xml input format I could write an xsl stylesheet to convert from one to the other.
I searched for them on the respective projects websited but I've found nothing.

Best,
Luca

---

