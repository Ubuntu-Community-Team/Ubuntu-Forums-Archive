---
title: "Sybase?"
date: 2005-12-08
forum: General Help
---

### Post by squibbon on 2005-12-08
Who has a sybase database running on their Ubuntu system or connecting into?

Can somebody from ubuntu team help me connect to our Sybase ASE database (windows server)? we got an existing system build in powerbuilder and i managed to run it on ubuntu but can't connect to the database. been trying to use open-client but still no luck for it. please, please, please.

---

### Post by squibbon on 2005-12-09
Ok, i managed to connect to database server using open-client. can execute query and all of that but still i can't use our front end to connect to our server. this is what i got when i do this:

$ wine oursystem.exe

The context allocation routine failed when it tried to load localization files!!One or more following problems may caused the failure

Your sybase home directory is /opt/sybase-11.9.2. Check the environment variable SYBASE if it is not the one you want!
Using locale name "en_PH.UTF-8" defined in environment variable LANG
Locale name "en_PH.UTF-8" doesn't exist in your /opt/sybase-11.9.2\locales\locales.dat file

and this is the error i receive when our application has been executed:

"Unable to initialize Client Library Context"

What should i do?

---

### Post by Grey Dog on 2007-01-16
I'm simply using the ODBC utilities included in Ubuntu. Works great!


(CAPS = variable)

dbdsn -w ODBCNAME -c "eng=SYBASESERVERNAME;dbn=SYBASEDATABASENAME;links=tcpip{udp=no;dobroadcast=no;host=REMOTEHOSTNAME}"


After running the above on a command line, it inserts it into your ".odbc" file in your home dir as a permanent ODBC entry.

---

### Post by Grey Dog on 2007-01-16
Sorry....Forgot Step #2

Create a Sybase profile that uses said ODBC connection....

---

