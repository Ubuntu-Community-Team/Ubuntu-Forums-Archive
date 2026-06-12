---
title: "OpenOffice Has Died!"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Mickeysofine1972 on 2006-07-19
Hi 

I run Kubuntu Dapper and have recently had problems with OO - specifically 'calc'; I found that a previously ok spreadsheet stopped recalculating subtotals...

Anyway the problem lies in that I tried to dowload the latest copy of OO 2.0.3 and install it using alien to create the .debs etc

Now I cant see icons on my 'K' menu under office and the damn thing wont reinstall properly!

Does anyone know how I can reinstall/fix this mess?

HEEEEEELP!

Mike

---

### Post by Mickeysofine1972 on 2006-07-19
Its OK I fixed myself!

;-)

---

### Post by T700 on 2006-07-19
For the sake of those yet to come, how about sharing how you fixed it?

Paul

---

### Post by Mickeysofine1972 on 2006-07-20
Oh alright then ;-)

The problem lies in that i was too afraid to uninstall the old package first as it warned me that I might uninstall kubuntu-destop ... sounds bad but apparently isnt! :o  so here what I did:

Well where do I begin... It was a hot summer day in ... but seriously here goes!

All I did was download the latest copy of OO from openoffice.org (2.0.3) then unzipped it to my desktop, (you could do this in your home folder but this way helps me to remember that I have to delete the install files/folder after).

You need to have alien installed, if you dont type the following in a terminal:
```
sudo apt-get install alien
```

Then I open a terminal and type:
```
cd Desktop/<insert where the folder unzipped to>/RPMS
```

Then convert the rpms to .deb by typing:

```
sudo alien -d *.rpm
```

Now we waite for a million or so years as they convert, (some information may be slighty over emphasised ;-)).

Once thats done you should have a list of debs that where created which means you can now install them!

BUT

Before you do ... you must remove the standard OpenOffice.org packages from inside synaptic/Adept. 

> 
Make sure you search for OpenOffice.org and mark them all for removal. You should get a warning about language support and also the removal of kubuntu-desktop or if you us ubuntu you might get ubuntu-desktop but I'm not sure coz I'm a Kubunter not a Ubunter. Anyway, this sound more dangerous than it actually is so ignore it :-D 

FINALLY

Type the following command in you still open terminal:
```

sudo dpkg -i *.deb

cd package-intergration <I thing its called this but it contains the already created .deb for debian menus>

sudo dpkg -i *.deb

```

thats the files installed so all you need to do is reboot and bobs your mothers brother :-)

Mike

---

