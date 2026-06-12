---
title: "dmg2iso error"
date: 2006-02-12
forum: Desktop Environments
---

### Post by maxdevis on 2006-02-12
when i want to change a dmg file into an iso file, followed [this](https://wiki.ubuntu.com/ManageDiscImages) howto, i got this error:
```

michiel@michiel:~$ dmg2iso.pl file.dmg file.iso
bash: /usr/local/bin/dmg2iso.pl: Toegang geweigerd

```

Toegang geweigerd is dutch for not accessable or restricted area, something like that :p

---

### Post by maxdevis on 2006-02-12
hmmm, 

i found out that there was something wrong with the rights, but now i get this error 
```

bash: /usr/local/bin/dmg2iso.pl: /usr/local/bin/perl^M: bad interpreter: Onbekend bestand of map

```

---

### Post by kaamos on 2006-02-12
What is the output of
```
ls /usr/local/bin
```
and
```
cat /usr/local/bin/dmg2iso.pl | head -n 4
```

---

### Post by maxdevis on 2006-02-12
1
dmg2iso.pl               nautilus-actions-convert
nautilus-actions-config  nautilus-actions-new-config


2
#!/usr/local/bin/perl
#
# dmg2iso - dmg to iso convert tool
# Copyright (C) 2004 vu1tur <v@vu1tur.eu.org>

---

### Post by kaamos on 2006-02-12
Okay, check that you have perl
```
which perl
```
If it returns "/usr/bin/perl" (if not, install perl-base) then
```
sudo ln -s /usr/bin/perl /usr/local/bin/perl
```
Then try again to use dmg2iso

---

### Post by maxdevis on 2006-02-12
```

michiel@michiel:~$ which perl
/usr/bin/perl
michiel@michiel:~$ sudo ln -s /usr/bin/perl /usr/local/bin/perl
Password:
michiel@michiel:~$ dmg2iso.pl file.dmg file.iso
bash: /usr/local/bin/dmg2iso.pl: /usr/local/bin/perl^M: bad interpreter: Onbekend bestand of map
michiel@michiel:~$


```

hmmm
reinstall perl?

edit: "Onbekend bestand of map" = unknown file or map

---

### Post by kaamos on 2006-02-12
I think your output (of which perl) is exactly what it is supposed to be. The problem seems to be the dmg2iso script. It is looking for the perl executable in /usr/local/bin when it is in /usr/bin. So you must edit the script or link perl to the local folder with
```
sudo ln -s /usr/bin/perl /usr/local/bin/perl
```

EDIT: ah, you edited the post. What does "perl --version" give?

---

### Post by maxdevis on 2006-02-12
[QUOTE=perl --version] 

This is perl, v5.8.7 built for i486-linux-gnu-thread-multi
(with 1 registered patch, see perl -V for more detail)

Copyright 1987-2005, Larry Wall

Perl may be copied only under the terms of either the Artistic License or the
GNU General Public License, which may be found in the Perl 5 source kit.

Complete documentation for Perl, including FAQ lists, should be found on
this system using `man perl' or `perldoc perl'.  If you have access to the
Internet, point your browser at [http://www.perl.org/](http://www.perl.org/), the Perl Home Page.
[/QUOTE]

and thanks for you help, i really appriciate it!

---

### Post by kaamos on 2006-02-12
Your perl seems to be ok..

What is really weird is the ^M in the error
> bash: /usr/local/bin/dmg2iso.pl: /usr/local/bin/perl**^M**: bad interpreter: Onbekend bestand of map

You could try the edit the file with
```
sudo gedit /usr/local/bin/dmg2iso.pl
```
and delete(!) the first line and replace it with
> #!/usr/bin/perl

---

### Post by maxdevis on 2006-02-12
```

michiel@michiel:~$ sudo gedit /usr/local/bin/dmg2iso.pl
Password:
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
michiel@michiel:~$ dmg2iso.pl file.dmg file.iso 
bash: /usr/local/bin/dmg2iso.pl: /usr/bin/perl^M: bad interpreter: Onbekend bestand of map
michiel@michiel:~$

```

really strange

---

### Post by kaamos on 2006-02-12
I'm running out of ideas. Perhaps you could try
```
perl /usr/local/bin/dmg2iso.pl file.dmg file.iso
```

---

### Post by xmastree on 2006-04-22
Did this ever get sorted out? Istumbled across this, and i had the same problem but in english...
/usr/bin/perl^M: bad interpreter: No such file or directory
What I did was weird. That ^M thing...
I edited the file, typed out that first line **exactly as it appeared** in bluefish, then deleted the original one.
```
Can't locate Compress/Zlib.pm in @INC (@INC contains: /etc/perl /usr/local/lib/p erl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/p erl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./dmg2iso.pl line 28.
```
It still failed, but it got past that first hurdle. :-k

So there's some invisible weird sh*t in that file.

---

### Post by Snijglau on 2006-05-18
I also got this error and found just the suggestion of running the script with perl manually to work out just fine.```
perl ~/dmg2iso.pl file.dmg file.iso
```
No editing required.  There was also a java version at [http://typhontools.cjb.net/dmgx]("http://typhontools.cjb.net/dmgx") that totally failed to work for me as well, but you could try it.

---

### Post by bernardfrancois on 2006-06-21
The file you downloaded is a file where each line ends with \n\r (which is the case with ascii files in windows). It should be just \n at the end of each line.

You can correct that with a command line utility 'dos2unix'.

Here you can download it: [http://www.programmersheaven.com/zone3/cat713/3118.htm](http://www.programmersheaven.com/zone3/cat713/3118.htm)

---

### Post by bernardfrancois on 2006-06-21
[QUOTE=bernardfrancois]The file you downloaded is a file where each line ends with \n\r (which is the case with ascii files in windows). It should be just \n at the end of each line.

You can correct that with a command line utility 'dos2unix'.

---

### Post by nalle on 2006-07-10
There is also a working version of the file. So an easier way of converting is to write these in the directory of the dmg file:
[INDENT]
wget [http://blinkenlights.ch/gnupod/dmg2iso.pl](http://blinkenlights.ch/gnupod/dmg2iso.pl)

perl dmg2iso.pl dmgfile.dmg isofile.iso
[/INDENT]
hope it helps ;)

---

### Post by robjson on 2007-01-16
Hi,

Just in case it helps someone. I had the ^M error. Which as stated is the windows version of the script. After much searching found that if you 'apt-get install flip' then flip -u dmg2iso.pl it will convert all the ^M to ^J which will then work in Ubuntu. Worked for me.

Cheers

---

