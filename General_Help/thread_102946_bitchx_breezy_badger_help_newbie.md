---
title: "bitchx breezy badger help newbie"
date: 2005-12-13
forum: General Help
---

### Post by solarstone on 2005-12-13
When i do a whois on myself running bitchx i get the following

 DTy (n=[COLOR="Red"]<realnamehere>[/COLOR]@hostname) (Commercial)
: ircname  : [COLOR="Red"]<realname here>[/COLOR]
| server   : calvino.freenode.net (Milan, IT)
: idle     : 0 hours 0 mins 5 secs (signon: Tue Dec 13 11:17:44 2005)

I have tried "/set ircname name" to try and change the ircname but bitchx says
no variable named that.

how do i change this IRCNAME ???

also i have no idea how to change my real name before the @ sign
I have spent hours looking through bitchx docs put got no answers.

pleeaase help ! :confused: 

many thanks.

---

### Post by kaamos on 2005-12-13
try just "/set name" and look at the variables..

Hope this helps.

---

### Post by solarstone on 2005-12-13
Thanks but it doesnt change.

any more ideas anyone :confused: :confused:

---

### Post by kaamos on 2005-12-13
/set real_name solarstone

This is how it would go in irssi at least..

---

### Post by solarstone on 2005-12-13
yes i have also done that in irssi and it works ok.

I have also done this in bitchx but it doesnt get rid of my real name in the places ive specified above.

Im thinking that bitchx *may* be reading an environment variable :confused: :confused: 

I dunno, and even if it is does that mean i have to change my log in name to something different:confused: :confused: 

just confused and getting no where fast...... :rolleyes:

---

### Post by M3ta7h3ad on 2005-12-13
do /set and hit enter. Read through the loaddddd of variables that will appear.

Wherever you find your name then do /set variable_name thenameyouwantinitsplace and it should change. :)

---

### Post by solarstone on 2005-12-13
Thanks but again I have already tried this..............

Update !!

I have now been able to change:

: ircname : <realname here>

Did this from bash with the command "export IRCNAME <namewantedhere>

so thats that sorted. But now I want to know how i change the
realnamehere part in the following
 (n=<realnamehere>@hostname) (Commercial)
:confused: :confused:

---

### Post by tedddee on 2005-12-13
just /IRCNAME by itself will generate a random one for you

or /IRCNAME yournamehere will change it

the other command you are looking for is /IRCUSER i believe, or /IRCHOST

havent been able to figure out how to get it to save the change though so it will remember it over a restart

also, anyone know how to disable these server messages?

Local OperKill: killed <ip> bla bla

---

### Post by M3ta7h3ad on 2005-12-13
[QUOTE=tedddee]just /IRCNAME by itself will generate a random one for you

or /IRCNAME yournamehere will change it

the other command you are looking for is /IRCUSER i believe, or /IRCHOST

havent been able to figure out how to get it to save the change though so it will remember it over a restart
[/QUOTE]
/save

---

### Post by loon on 2005-12-22
easy way would be to go into your Users and Groups

System -> Administration -> Users and Groups

And change your Real name information.  :)

---

### Post by kserg on 2007-03-09
Slightly off-topic but does anyone know how to remove pratchett.freenode.net from the list of servers? I can't find it listed in any files:/

EDIT: Never mind, i found it... .ircservers file...

---

### Post by Invius on 2007-04-20
gedit ~/.bitchxrc

type the following in this new file:

^set realname whatever name you want.

Save the file.

---

