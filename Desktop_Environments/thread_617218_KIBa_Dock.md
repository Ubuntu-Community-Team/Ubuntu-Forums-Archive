---
title: "KIBa Dock"
date: 2007-11-19
forum: Desktop Environments
---

### Post by sweetfishremix on 2007-11-19
Ok so I just finished installing Kiba dock, but it looks like this....
[IMG]http://img.photobucket.com/albums/v622/kyochan/help.jpg[/IMG]

I tryed going to gset-kiba to change that blue background. But it dosent save it. Someone told me to run it as root, but I'm fairly new at using Ubuntu, so I dont know how to do that. Can soemone please help me.

---

### Post by daengbo on 2007-11-19
To run it as root, type ALT-F2 and type the following in the dialog:
gksudo gset-kiba

If you want to use a terminal, you can type 
sudo gset-kiba

---

### Post by sweetfishremix on 2007-11-19
Ok I ran it as root....And I still got the same thing...Nothing is differnt.... Any suggestions?

---

### Post by seventhc on 2007-11-19
I installed kiba-dock just a few days ago, yours looks different than my default settings, but the way I changed my settings was by right clicking in the dock area and chose kiba settings. From there I can make it look how I want. If this is your default settings I'm not sure if we have the same version though but I hope this helps. :)

kiba settings also shows up under system> preferences>kiba settings.

---

### Post by sweetfishremix on 2007-11-19
There are differnt verson? Mine was a package thing...Because installing it manually was too hard T-T I'm very new at linux so I have no idea what is what T_T
And No it did not work for me...Everytime I change what it looks like nothing happens. It just looks like this. Everythign works fine thou, including the gravity engin, akam watever...

---

### Post by seventhc on 2007-11-19
Did you install the plugins also??
when I installed mine I went through several steps, I'll try to find the link for you.

O.K I found it, just read through it and see if it's like you did and also b/c they have a way for 32 bit users as well as 64 bit users, the first part is for both then just follow it through for either 32 or 64 bit depending on what you have.

just copy and paste everything into the terminal...applications>accessories>terminal

I tried other ways but this is the only one that worked for me...hope it helps you too. :)

[http://ubuntuforums.org/showthread.php?t=554127]("http://ubuntuforums.org/showthread.php?t=554127")

---

### Post by sweetfishremix on 2007-11-20
So at the moment what step am I on? Or should I start over? I apologize for sucking at this so much T____T

---

### Post by seventhc on 2007-11-20
don't worry, it took me a few tries to get it working, imo I would prob just start over using that link. 
If you have any probs let me know but I might not be back on until tomorrow, but theres lots of people still awake :)

when i did the install at 1 point i was missing a file...I did

 sudo aptitude install <filename> the name of the missing file without the brackets ;)
then continued from the last command before the error and all was fine. :)
Let me know how you make out.

---

### Post by sweetfishremix on 2007-11-20
Error validating server certificate for 'https://kibadock.svn.sourceforge.net:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
Certificate information:
 - Hostname: *.svn.sourceforge.net
 - Valid: from Tue, 09 Oct 2007 14:15:07 GMT until Mon, 08 Dec 2008 15:15:07 GMT
 - Issuer: Equifax Secure Certificate Authority, Equifax, US
 - Fingerprint: fb:75:6c:40:58:ae:21:8c:63:dd:1b:7b:6a:7d:bb:8c:74:36:e7:8a
(R)eject, accept (t)emporarily or accept (p)ermanently? svn: PROPFIND request failed on '/svnroot/kibadock/trunk/akamaru'
svn: PROPFIND of '/svnroot/kibadock/trunk/akamaru': Server certificate verification failed: issuer is not trusted ([https://kibadock.svn.sourceforge.net](https://kibadock.svn.sourceforge.net))

I got this during the directory phase........Please help T_T

---

### Post by seventhc on 2007-11-20
It looks like you get choices there ( (R)eject, accept (t)emporarily or  [COLOR=Red]accept (p)ermanently?)[/COLOR] so if you type in [COLOR=Red]p[/COLOR] it will accept the certificate permanently.

[I]so type p and then hit enter to accept  the certificate.

here is a link to someone with the same problem...towards the  bottom of the page.

[/I][http://ubuntu-utah.ubuntuforums.org/showthread.php?t=554127&page=12](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=554127&page=12)

---

