---
title: "HOw to install aegis Antivirus scanner"
date: 2006-01-14
forum: General Help
---

### Post by KhanArash on 2006-01-14
I want to install the Antivirus in my UBuntu 5.10 but I get this message :
Cannot install 'aegis-virus-scanner'

Installing this application would mean that something else needs to be removed. Please use the "Advanced" mode to install 'aegis-virus-scanner'.

CAn SOmeone please help?

---

### Post by KhanArash on 2006-01-14
CAnt anyone help me please?!:confused:

---

### Post by BathroomNinja on 2006-01-14
A member is [This thread]("http://www.ubuntuforums.org/showthread.php?t=117099") had a very simular problem (only with VLC instead of aegis).  Instead of me re-typing everything here, go read that thread and see if any of it helps you.

---

### Post by KhanArash on 2006-01-14
[QUOTE=BathroomNinja]A member is [This thread]("http://www.ubuntuforums.org/showthread.php?t=117099") had a very simular problem (only with VLC instead of aegis).  Instead of me re-typing everything here, go read that thread and see if any of it helps you.[/QUOTE]

YEa I know I did post the otherone too...BUt that didnt solve my problem, none of those programs are running, there I ask for help again!

---

### Post by KhanArash on 2006-01-14
Everytime I will install something from synaptic, it tells it need "another file" and the other file needs another! so I cant get anything installed from the synaptic!

ANyone can help?!

---

### Post by BathroomNinja on 2006-01-14
it's normal for the file to need other files (called dependencies) in order to install.  Synaptic should tell you that it will be installing these files, then you click 'apply' and Synaptic does it's thing.

It's not normal for this process to fail like it is for you.
When did this first start happening for you?

---

### Post by KhanArash on 2006-01-14
[QUOTE=BathroomNinja]it's normal for the file to need other files (called dependencies) in order to install.  Synaptic should tell you that it will be installing these files, then you click 'apply' and Synaptic does it's thing.

It's not normal for this process to fail like it is for you.
When did this first start happening for you?[/QUOTE]


I did start to use linux for 2 days ago, and it started today!
I know it comes up and tells what will be installed, but when I click on applay it says the files were not found!

do you know how to fix it?

---

### Post by BathroomNinja on 2006-01-14
OK.  Just a wild guess here, are you connected to the internet on your Ubuntu computer?

If so, have you recently installed anything prior to this issue?  Try clicking 'Refresh' in Synaptic.  What happens?

---

### Post by KhanArash on 2006-01-14
[QUOTE=BathroomNinja]OK.  Just a wild guess here, are you connected to the internet on your Ubuntu computer?

If so, have you recently installed anything prior to this issue?  Try clicking 'Refresh' in Synaptic.  What happens?[/QUOTE]


YEa I am using ubuntu now and I am connected to the INternett... if you mean "Reaload" when I cliked on that now it sayd it was downloading 8 packs!
But can u please tell me how to fix it?!

---

### Post by KhanArash on 2006-01-14
None has any idea for how it can be fixed?:confused:

---

### Post by soulestream on 2006-01-14
maybe you could copy/paste the output from synaptic

cause guessing based on "another file" would be "pointless"

could be something like synaptic is trying to install files from your CD

soule

---

### Post by johnnymo87 on 2006-01-14
[QUOTE=KhanArash]I want to install the Antivirus in my UBuntu 5.10 but I get this message :
Cannot install 'aegis-virus-scanner'

Installing this application would mean that something else needs to be removed. **Please use the "Advanced" mode to install 'aegis-virus-scanner'.**

CAn SOmeone please help?[/QUOTE]

The "advanced mode" is Synpatic Package Manager.

To give us more info to analyze, go to System ---> Administration ---> Synaptic Package Manager

Press the "search" button. Type in "aegis". Mark the "aegis-virus-scanner" for installation. Press the "apply" button. When the "mark addition changes window?" comes up, press the "mark" button. [This is as far as I went, the rest I'll tell you from memory--it won't be as precise] The packages should begin to install. In that window, there is a triangular button that will show the details in the terminal if you press it. Press it. When the error comes up, post it here.

---

### Post by KhanArash on 2006-01-14
aegis-virus-scanner:
 Avhenger av: libarchive-zip-perl  but it is not installable
 Avhenger av: libarchive-tar-perl men kommer ikke til å bli installert

men kommer ikke til å bli installert= but could not be installed

---

### Post by BathroomNinja on 2006-01-14
[QUOTE=KhanArash]aegis-virus-scanner:
 Avhenger av: libarchive-zip-perl  but it is not installable
 Avhenger av: libarchive-tar-perl men kommer ikke til å bli installert

men kommer ikke til å bli installert= but could not be installed[/QUOTE]


can you translate that into english of me?

---

### Post by KhanArash on 2006-01-14
[QUOTE=BathroomNinja]can you translate that into english of me?[/QUOTE]

aegis-virus-scanner:
It needs: libarchive-zip-perl but it is not installable
It needs: libarchive-tar-perl but could not be installed

ok:D?

---

### Post by BathroomNinja on 2006-01-14
[QUOTE=KhanArash]aegis-virus-scanner:
It needs: libarchive-zip-perl but it is not installable
It needs: libarchive-tar-perl but could not be installed

ok:D?[/QUOTE]

yes! thank you!

ok.  Click on APPLICATIONS > ACCESSORIES > TERMINAL

in the terminal, type the following:
```
sudo gedit /etc/apt/sources.list 
```
press Enter

It will ask you for your password, type it in, press Enter.

A gedit window will pop up with a list of your sources.  Copy ALL of it and paste it into a reply here.  Please make sure to use the code tags.  You can get them by clicking on the # symbol next to the <> and php symbols when you are typing a message here.

---

### Post by KhanArash on 2006-01-14
[QUOTE=BathroomNinja]yes! thank you!

ok.  Click on APPLICATIONS > ACCESSORIES > TERMINAL

in the terminal, type the following:
```
sudo gedit /etc/apt/sources.list 
```
press Enter

It will ask you for your password, type it in, press Enter.

A gedit window will pop up with a list of your sources.  Copy ALL of it and paste it into a reply here.  Please make sure to use the code tags.  You can get them by clicking on the # symbol next to the <> and php symbols when you are typing a message here.[/QUOTE]
sry ididnt understand what u meand by "You can get them by clicking on the # symbol next to the <> and php symbols when you are typing a message here"

but here is the text!


deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

---

### Post by BathroomNinja on 2006-01-14
OK.  Edit the lines, removing the # in front of all of the lines starting with '# deb'
so that it looks like the following
```
## Uncomment the following two lines to fetch updated software from the network
deb http://no.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://no.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb-src http://no.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://no.archive.ubuntu.com/ubuntu breezy universe
deb-src http://no.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy multiverse

deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ breezy universe
```


After you do this, click on save, or just close and save gedit.  Close Synaptic, open it back up again, click on RELOAD.  Then try installing the virus scanner again.

Also, here is what I was talking about:

---

### Post by BathroomNinja on 2006-01-14
er.. I mean here:

---

### Post by KhanArash on 2006-01-14
```

## Uncomment the following two lines to fetch updated software from the network
deb http://no.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://no.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb-src http://no.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://no.archive.ubuntu.com/ubuntu breezy universe
deb-src http://no.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy multiverse

deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ breezy universe
```

---

### Post by BathroomNinja on 2006-01-14
How did that work out for you?

---

### Post by KhanArash on 2006-01-14
[QUOTE=BathroomNinja]How did that work out for you?[/QUOTE]

Thank you ..it works very well..everything work:D

---

### Post by sapatos on 2008-02-21
Please help, how can i install download applications?

---

### Post by toolisima on 2008-06-12
Hello, I am posting this because the thread title is exactly what I was gonna write, although the problem seems to be different from what I read above.

So the deal is that first of all I wonder if an Antivirus is necessary in Ubuntu?
Then I have already in my desktop the archive with the aegis files downloaded with Synaptic. I try to find out instructions to install it, but there are none. I try to open the package with GDebi Package Installer but I get an error message: "Could not open 'avg75fld-r51-a1243.i386.deb' The package might be corrupted or you are not allowed to open the file. Check the permissions of the file". 
I check the permissions by rightclicking and looking at Properties, changed all to Read and Write, but the same error message.
:confused:

Ideas anyone? Ohhh but first tell me how necessary it is to have a virus scanner in Ubuntu.
Thanks!

---

