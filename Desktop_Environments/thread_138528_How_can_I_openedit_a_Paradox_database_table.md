---
title: "How can I open/edit a Paradox database table?"
date: 2006-03-02
forum: Desktop Environments
---

### Post by PaulR2006 on 2006-03-02
Hi

Can anyone suggest how I can open/edit/query Pardox database tables (created on Windows)? I believe they are ODBC compliant but if I try to open one with OpenOffice Base I get an error message (after selecting ODBC as the type and clicking 'Browse') as follows...

"Could not load the program library libodbc.so.1 or it is corrupted..."

I took this to mean that some necessary driver wasn't installed but I can't find any such file listed in the package manager (there is a libodbcinstq1c2 not currently installed and odbcinst1debian1 which was installed by default).

This is a brand new install of 5.10 with updates and nothing else added or taken away.

This is a critical issue for me while assessing Ubuntu for our business, resolving it will lead to a whole office full of new Ubuntu users!

PS I have noticed programs such as FabForce's DBDesigner which might do the job but I didn't want to install anything that isn't necessary if the tools are already included to achieve the objective. We require only simple 'desktop' database functionality (view/edit/simple query) - we currently use Borland's Database Desktop on Windows machines and it works very well.

TIA

Paul

---

### Post by cronholio on 2006-03-02
Install gnumeric and gnumeric-plugins-extra. This will also install pxlib1 (for reading/writing Paradox files). Gnumeric should now be able to handle these.

---

### Post by kaamos on 2006-03-02
You can use packages.ubuntu.com to track down missing libraries. According to [that](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libodbc.so.1&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386) /usr/lib/libodbc.so.1 is in the package "unixodbc". That will most likely get installed with cronholios solution.

---

### Post by PaulR2006 on 2006-03-02
Thanks for trying but that doesn't work - I installed gnumeric and the plug ins but get an 'error opening paradox file' when trying to open a table. I checked and unixodbc wasn't installed so I installed that too and tried again but gnumeric gives the same error (pxlib1 is installed too, I checked).

However, if I now try to connect to an existing odbc in OpenOffice I don't get the original error, instead when I click 'browse' I get a dialog with an empty list asking me to choose a data source.

Ideally I'd like to use OpenOffice since it's familiar (on Windows) to other users.

---

### Post by cronholio on 2006-03-02
Mhh... Do you have the /usr/lib/gnumeric/1.6.1/plugins/paradox dir?

---

### Post by PaulR2006 on 2006-03-02
Er, sort of... I have version 1.5.90 for some reason... the paradox folder contains three files.

---

### Post by PaulR2006 on 2006-03-06
Bump: Anyone got any other suggestions?

TIA

Paul.

---

### Post by Zimmer on 2006-03-06
[QUOTE=PaulR2006]Thanks for trying but that doesn't work - I installed gnumeric and the plug ins but get an 'error opening paradox file' when trying to open a table. I checked and unixodbc wasn't installed so I installed that too and tried again but gnumeric gives the same error (pxlib1 is installed too, I checked).

However, if I now try to connect to an existing odbc in OpenOffice I don't get the original error, instead when I click 'browse' I get a dialog with an empty list asking me to choose a data source.

Ideally I'd like to use OpenOffice since it's familiar (on Windows) to other users.[/QUOTE]
SOunds like you haven't 'created' the Data Source for use with ODBC:you need to create a name for the source and link that to the location and specify the driver to be used. I have never done that with OO.
I remember similar experience linking SAS as an ODBC source in Windows.
HAve a look at this link for some info , it may give you a clue.
[http://dev.mysql.com/doc/maxdb/en/40/b3ee407552742ae10000000a155106/content.htm](http://dev.mysql.com/doc/maxdb/en/40/b3ee407552742ae10000000a155106/content.htm)

EDIT: also, have you 'registered' the Database/Source you wish to connect to, BTW ?
Tools>Options>Database    and NEW.
(Sorry about the Edits, but the forum keeps dropping my sign in !!)
Another good source of info..
[http://api.openoffice.org/docs/DevelopersGuide/Database/Database.xhtml](http://api.openoffice.org/docs/DevelopersGuide/Database/Database.xhtml)

---

### Post by PaulR2006 on 2006-03-06
Thanks Zimmer... I know how to connect to these Paradox tables via OpenOffice on Windows (described in that link) but can't get it to work in Ubuntu.

Thinking....

---

