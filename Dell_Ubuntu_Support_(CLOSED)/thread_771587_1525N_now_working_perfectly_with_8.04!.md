---
title: "1525N now working perfectly with 8.04!"
date: 2008-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by WBL on 2008-04-27
I have a Dell Inspiron 1525N.  Like many people, I had problems after upgrading to 8.04.  Everything's fixed now and working wonderfully.  I thought it might be useful to document exactly what I did (it might help somebody else).  Here is what I did, step-by-step:

-----

1.  Download the .iso for 8.04 and burn the image using Brasero (or whatever you like to burn  with).

2.  Backup data and do a clean install of 8.04.

3.  Enable all repositories.

4.  Type the following into the command prompt:```
sudo apt-get install ubuntu-restricted-extras

```

5.  Follow all the directions on this webpage:  [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

6.  If your sound is too low (mine was), open up a terminal and type ```
alsamixer
```Turn everything up all the way.  Press "Esc" to save settings and exit.

-----

Doing this made everything work.  The only annoyance is that, for some reason, everytime I install something it says "NOT AUTHENTICATED" or something and makes me click "Yes" to install.

Hope this helps somebody.  :)

-WBL

---

### Post by LeoSolaris on 2008-04-28
Thank ya!  I have an Inspiron 1520 and it is similar enough to the 1525 for most of the 25's fixes to work. Thanks for the pointer towards that sticky,it made life easier too.

I did a distro upgrade rather than a fresh install... the webcam stopped working. Can you let me know what you're webcam is doing so I can compare notes? I made a post about it [-->here<--]("http://ubuntuforums.org/showthread.php?p=4818762#post4818762")

I bet it has something to do with what I had to do to get the cam working under Gutsy, either that or with Skype.

Leo

---

### Post by WBL on 2008-04-28
> **LeoSolaris said:**
> 
I did a distro upgrade rather than a fresh install... the webcam stopped working. Can you let me know what you're webcam is doing so I can compare notes? I made a post about it [-->here<--]("http://ubuntuforums.org/showthread.php?p=4818762#post4818762")
Leo

Sorry, I don't have a webcam.  :(

-WBL

---

### Post by ubuntu-freak on 2008-05-08
Just to let you know, there's no need to install the restricted-extras package if you're gonna follow my sticky, as part 1 will install those packages and more. The restricted-extras package also installs OpenJDK instead of Sun Java, most of you will want the latter for compatibility reasons.
 
Nathan

---

