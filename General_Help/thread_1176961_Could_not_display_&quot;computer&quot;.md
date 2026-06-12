---
title: "Could not display &quot;computer:///&quot;"
date: 2009-06-02
forum: General Help
---

### Post by dangmien on 2009-06-02
hi all,i have a problem when i log in ubuntu and mycomputer indicates any errors:  
can you explain and help me to fix that errors(i am newbie of ubuntu)
[IMG]http://i561.photobucket.com/albums/ss55/dangmien/Screenshot.png[/IMG]

---

### Post by LepeKaname on 2009-06-02
Its kind of weird your problem...

Check what did you install recently (look at the /var/log/aptitude if you uses aptitude, or /var/log/apt .. or in you synaptic.. or whatever you use...)

You could also try reinstalling nautilus, with:

sudo aptitude reinstall nautilus

Sorry I can't help more...

---

### Post by dangmien on 2009-06-03
thank for your help,it really is much appreciated,i have tried  reinstalling nautilus, with:

sudo aptitude reinstall nautilus,and the mistake :"could not display computer :///  "was disapeared ,but there are two mistakes which can not fix,any opinion esle ?

---

### Post by LepeKaname on 2009-06-03
One of the error said:

"Could not find /home/dangmien/Desktop/Eclipse"

According to the screenshot you posted, there is no "Eclipse" in your desktop... so I think that message is correct.

The other error:

"Could not find /media/DATA/"...

Means that you are trying to open something that was in a USB media or similar that is now unplugged. 

Check your links of whatever you are click to. That will fix the problem.

---

### Post by dangmien on 2009-06-03
thank you very much

---

