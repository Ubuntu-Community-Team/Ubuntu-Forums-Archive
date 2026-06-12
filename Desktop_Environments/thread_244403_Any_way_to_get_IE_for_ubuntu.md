---
title: "Any way to get IE for ubuntu?"
date: 2006-08-26
forum: Desktop Environments
---

### Post by randell6564 on 2006-08-26
Hi Folks!

The only reason that I would like to get Internet Explorer for my Ubuntu is because I am a paying member of cinemanow.com and would like to be able to view their movies.  They are an IE only web site.

I did try and install ies4linux from here [http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)  but to no avail!  Keep getting .Cab errors.  I have installed wine and cabextract.

Does anyone know of another way? Thanks!

---

### Post by v1ct0r on 2006-08-26
There is a way...a very dangerous way! 
j/k

Here is a chapter from the Unofficial Ubuntu Bible
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Internet_Explorer_.2B_Flash_9](http://ubuntuguide.org/wiki/Dapper#How_to_install_Internet_Explorer_.2B_Flash_9)
Hope it works. 
Cheers!

ps. [And some geek humour...](http://monster-island.org/tinashumor/humor/ielinux.html)
:-({|=

---

### Post by randell6564 on 2006-08-26
> **v1ct0r said:**
> There is a way...a very dangerous way! 
j/k

Here is a chapter from the Unofficial Ubuntu Bible
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Internet_Explorer_.2B_Flash_9](http://ubuntuguide.org/wiki/Dapper#How_to_install_Internet_Explorer_.2B_Flash_9)
Hope it works. 
Cheers!

I'll give it a looksy Thanks!

---

### Post by mlind on 2006-08-26
I've got IE6 running using wine and [WineTools]("http://www.von-thadden.de/Joachim/WineTools") in the past.

---

### Post by randell6564 on 2006-08-26
> **v1ct0r said:**
> There is a way...a very dangerous way! 
j/k

Here is a chapter from the Unofficial Ubuntu Bible
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Internet_Explorer_.2B_Flash_9](http://ubuntuguide.org/wiki/Dapper#How_to_install_Internet_Explorer_.2B_Flash_9)
Hope it works. 
Cheers!

ps. [And some geek humour...](http://monster-island.org/tinashumor/humor/ielinux.html)
:-({|=

Hi!  Thats the exact same application as what I used before, just a different way of getting it!

the App is called ies4linux.  I tryed to install it using the link you provided but I'm getting the same error:
[B]No valid cabinets found
An error occured when trying to cabextract some files.
[/B]

I have no idea what the problem is!

is there another way?

---

### Post by randell6564 on 2006-08-26
Here is the complete error that i am getting in case anyone has any ideas:

[B]Installing IE 6
 Initializing
 Creating Wine Prefix
 Extracting CAB files
/home/scott/.ies4linux/downloads/ie6/EN-US//ADVAUTH.CAB: no valid cabinets found
/home/scott/.ies4linux/downloads/ie6/EN-US//CRLUPD.CAB: no valid cabinets found
/home/scott/.ies4linux/downloads/ie6/EN-US//HHUPD.CAB: no valid cabinets found
/home/scott/.ies4linux/downloads/ie6/EN-US//IEDOM.CAB: no valid cabinets found
/home/scott/.ies4linux/downloads/ie6/EN-US//IE_S1.CAB: no valid cabinets found
/home/scott/.ies4linux/downloads/ie6/EN-US//IE_S2.CAB: no valid cabinets found
/home/scott/.ies4linux/downloads/ie6/EN-US//IE_S3.CAB: no valid cabinets found
/home/scott/.ies4linux/downloads/ie6/EN-US//IE_S4.CAB: no valid cabinets found
/home/scott/.ies4linux/downloads/ie6/EN-US//IE_S5.CAB: no valid cabinets found
/home/scott/.ies4linux/downloads/ie6/EN-US//IE_S6.CAB: no valid cabinets found
/home/scott/.ies4linux/downloads/ie6/EN-US//SCR56EN.CAB: no valid cabinets found
/home/scott/.ies4linux/downloads/ie6/EN-US//SETUPW95.CAB: no valid cabinets found
/home/scott/.ies4linux/downloads/ie6/EN-US//VGX.CAB: no valid cabinets found
An error occured when trying to cabextract some files.
[/B]

Thanks!

---

### Post by v1ct0r on 2006-08-26
Maybe this ? 
[http://www.tatanka.com.br/ies4linux/forum/viewtopic.php?p=843](http://www.tatanka.com.br/ies4linux/forum/viewtopic.php?p=843)
Try and ask on the official forums. 
Or...get an older version. :-({|=

---

### Post by mostwanted on 2006-08-26
ies4linux has always worked for me. It's completely automated so it's probably the easiest way as well.

It installs a localised copy of IE 5, 5.5. and/or 6.0 along with the Flash plugin.

---

### Post by randell6564 on 2006-08-26
> **v1ct0r said:**
> Maybe this ? 
[http://www.tatanka.com.br/ies4linux/forum/viewtopic.php?p=843](http://www.tatanka.com.br/ies4linux/forum/viewtopic.php?p=843)
Try and ask on the official forums. 
Or...get an older version. :-({|=

Hey Thanks, but I was actually asking if there was another way entirely of getting IE.  (Read the OP)

---

### Post by randell6564 on 2006-08-26
> **mostwanted said:**
> ies4linux has always worked for me. It's completely automated so it's probably the easiest way as well.

It installs a localised copy of IE 5, 5.5. and/or 6.0 along with the Flash plugin.

Hey mostwanted!

I finally got it installed, but I could only install it by logging in as root.  Also, for some reason, I cant view the movies at [www.cinemanow.com](www.cinemanow.com).
The free player pops up, but no movie ever loads.

Any ideas?

---

### Post by v1ct0r on 2006-08-26
Tricky ...
Maybe this ? 
[http://rewrite.rickbradley.com/articles/2006/02/18/building-ie-on-linux](http://rewrite.rickbradley.com/articles/2006/02/18/building-ie-on-linux)
:roll:

---

