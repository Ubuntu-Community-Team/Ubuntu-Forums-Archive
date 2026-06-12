---
title: "cant play dvd"
date: 2008-02-27
forum: Dell  Ubuntu Support
---

### Post by maineman2 on 2008-02-27
Hi I downloaded all the codecs today and I still cant play any movies.I get the error message no codecs installed. So i went and downloaded Mplayer and that doseant work either  Any ideas? Thanks Dan

---

### Post by rouge568 on 2008-02-27
Could you please list the codecs you did install? You may be missing a few.

---

### Post by maineman2 on 2008-02-27
As far as I know I downloaded them all I went to the ibeentoubunu website it was a one click install. It worked for me in the past. I just did a fresh reinstall of ubuntu.
Thanks Dan

---

### Post by fragos on 2008-02-27
Go to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and follow the directions to add their repository. Then do a synaptics search for libdvdcss and install.

---

### Post by maineman2 on 2008-02-28
Well this is the output of that medibuntu  script  in the previous post   dan@medan-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
--18:28:49--  [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... failed: Name or service not known.
medan@medan-laptop:~$ 
Dan

---

### Post by fragos on 2008-02-28
I can't imagine why it didn't work.  Did you cut and paste or type the commands?  I'd try again, perhaps their system was updating when you ran the commands.  I've seen this work many times for me on a number of systems.

---

### Post by maineman2 on 2008-02-28
I copied and pasted Ill try again

---

### Post by maineman2 on 2008-02-28
Ok it worked this time I cant down load the packages here at home. The internet is to slow I will go to the local library saturday morn and do it thanks Dan

---

### Post by maineman2 on 2008-02-28
Now I went to the add remove programs it went to update sources  and it came back with an error medibuntu  no public key Dan

---

### Post by fragos on 2008-02-28
Make sure that you've run the following rather long command.

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

