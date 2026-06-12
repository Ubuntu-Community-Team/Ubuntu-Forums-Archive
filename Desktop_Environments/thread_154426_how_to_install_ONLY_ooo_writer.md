---
title: "how to install ONLY ooo writer?"
date: 2006-04-03
forum: Desktop Environments
---

### Post by arazaxirelcinellersadolur on 2006-04-03
hi,
i am using only ooo's writer on my ubuntu hoary system and i want to uninstall the other ooo's components such as calc, draw, math, spreadsheet etc..

but how to do? ](*,) 

OR,

i want to install only and only the ooo's writer, witout calc, draw , math etc.

but how can i do that, after full uninstalling? ](*,) 
best regards

---

### Post by adrenaline on 2006-04-03
Hmmm...not quite sure but have you tried abiword?  If you like it you could ditch openoffice altogether.

Sorry for not explaining what it is, abiword is a word processor similar to writer but tends to open faster and ships standard with a lot of distributions that are aimed at older computers.

---

### Post by Zeroangel on 2006-04-03
You *should* be able to uninstall those components individually, or at least uninstall everything and then install openoffice-core (and other necessary files) as well as the writer. Unless, that only works in Dapper.

The other openoffice components do not take up as much room, so I don't really see harm on keeping them unless of course you want an uncluttered menu.

---

### Post by arazaxirelcinellersadolur on 2006-04-03
[QUOTE=Zeroangel]You *should* be able to uninstall those components individually, or at least uninstall everything and then install openoffice-core (and other necessary files) as well as the writer. Unless, that only works in Dapper.

The other openoffice components do not take up as much room, so I don't really see harm on keeping them unless of course you want an uncluttered menu.[/QUOTE]

ok, if i understand correctly, i can not uninstall the ooo components at my hoary, wich uses the 1.1.3 v. of ooo .

thanks for reply

---

### Post by arazaxirelcinellersadolur on 2006-04-03
[QUOTE=adrenaline]Hmmm...not quite sure but have you tried abiword?  If you like it you could ditch openoffice altogether.

Sorry for not explaining what it is, abiword is a word processor similar to writer but tends to open faster and ships standard with a lot of distributions that are aimed at older computers.[/QUOTE]
hi,
thank u for reply. 
i tried abiword, but i found it less comfortible, especially i hate its crashing.
and, it did not answer my requests about writing in arabic and turkish...
but i agree with you about its small size and speedity...

---

### Post by megabyte405 on 2006-04-19
Please report any problems, bugs, or documents that don't work to the AbiWord bug tracker, where we can take a look at them, help you fix them if they're a configuration issue, or fix the problem in the program if you've found a bug.  It can be found at [http://bugzilla.abisource.com ]("http://bugzilla.abisource.com")  You might also care to visit the home page at [http://www.abisource.com]("http://www.abisource.com") and perhaps join the user mailing list if you have questions.

Thanks for trying AbiWord, and we hope you'll give it another shot!  (Perhaps with a more recent version: try the AutoPackage on our web site for the latest version that should work on most linux distributions)

-- Ryan, AbiWord dev and win32 maintainer

---

### Post by arazaxirelcinellersadolur on 2006-04-20
[QUOTE=megabyte405]Please report any problems, bugs, or documents that don't work to the AbiWord bug tracker, where we can take a look at them, help you fix them if they're a configuration issue, or fix the problem in the program if you've found a bug.  It can be found at [http://bugzilla.abisource.com ]("http://bugzilla.abisource.com")  You might also care to visit the home page at [http://www.abisource.com]("http://www.abisource.com") and perhaps join the user mailing list if you have questions.

Thanks for trying AbiWord, and we hope you'll give it another shot!  (Perhaps with a more recent version: try the AutoPackage on our web site for the latest version that should work on most linux distributions)

-- Ryan, AbiWord dev and win32 maintainer[/QUOTE]

thank you.
my hoary's latest version is : 2.2.2-1ubuntu2.2 . i installed it -wich do not wrote the arabic correctly- and was wait for a new version to be appear at the update manager icon about 5 days. but when it did not appear, i uninstalled it away.
and due to i want to keep my system «clean», i.e. that i do not want to keep at my system softwares that i am not using, i did not try the autopackage..
anyway, i thank u for your attention

---

### Post by megabyte405 on 2006-04-30
[QUOTE=arazaxirelcinellersadolur]thank you.
my hoary's latest version is : 2.2.2-1ubuntu2.2 . i installed it -wich do not wrote the arabic correctly- and was wait for a new version to be appear at the update manager icon about 5 days. but when it did not appear, i uninstalled it away.
and due to i want to keep my system «clean», i.e. that i do not want to keep at my system softwares that i am not using, i did not try the autopackage..
anyway, i thank u for your attention[/QUOTE]


Arabic support is a work in progress, and we'd love your help.  Due to the Ubuntu team's decisions, new versions are not added to released versions of the operating system, so if you want anything newer than 2.2.2 (which is ancient, IMHO), you'll have to either use Backports (which might get you 2.4.1), or use the autopackage, which is recommended.  If you do decide to give it a shot, make sure you remove your Ubuntu version of AbiWord first.  Then, if you find any bugs, please report them to [http://bugzilla.abisource.com/](http://bugzilla.abisource.com/)

Thanks for your reply!

--Ryan, AbiWord Dev and Win32 Maintainer

---

### Post by louis_nichols on 2006-05-01
This is probably not the best advice and certainly not very elegant, but if you were to upgrade to breezy, you would be able to simply choose the debs to install for the various ooo components. Look:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=openoffice&searchon=names&subword=1&version=breezy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=openoffice&searchon=names&subword=1&version=breezy&release=all")

---

