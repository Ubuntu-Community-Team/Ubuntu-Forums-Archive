---
title: "Lid closing problem (not resolved by fix)"
date: 2007-07-14
forum: Dell  Ubuntu Support
---

### Post by ndinadis on 2007-07-14
I have a Dell i6400/E1505 
Since installing Fiesty I have had a problem with suspending, I have changes the settings under the battery menu to suspend, when I do close the lid or say suspend under the shut down menu it suspends normally. 
Its when I try to wake the computer the problem happens, it doesnt wake.
the computer seems to wake but the screen stays black no matter how long I leave it. 
I have seen and tried a fix with editing the warm boot setting from true to false, this has made no difference.
Anyone who what's causing this or more importantly how to fix it?
Thanks

---

### Post by angryfirelord on 2007-07-15
Suspend/Hibernate is still an issue with the kernel that has to be worked out. There's no good solution at the moment.

However, Ubuntu starts up fast enough to where I don't really think it's necessary.

---

### Post by strabes on 2007-07-15
Check the "Suspend & Hibernate for ATI" link in my signature. It's a video card issue.

---

### Post by ndinadis on 2007-07-15
I am trying the instructions in your sig I will post if it works,
I think it is an issue considering I have had it work with every other install I  have ever done.
thanks for the help.

---

### Post by technikalKP on 2007-07-15
Are you using Compiz Fusion for the desktop effects?  I found that when I had that installed, my machine would not consistently resume from suspend.  I reverted back to Beryl and everything works correctly with that.

---

### Post by ndinadis on 2007-07-15
Funny I was just thinking of setting up compiz fusion on another machine 
I am running beryl with xgl, but am pretty sure the problem still exists in gnome. 
I have applied the changes that were in the tut but havent tried it yet, it did not work with only step 3 so I did all of them but will wait till I shut down my computer tonight to try and see if it worked (dont want to loose things that are open right now (torrents)).
Thanks for the help again guys, will post if this works!

---

### Post by strabes on 2007-07-17
Yes, I think once you get rid of "true" in that file you'll have to restart your computer in order to see it work. I'm not really sure though.

---

### Post by ndinadis on 2007-07-17
I am pretty sure I have tried restarting it and checking again but so far it has not worked, I am going to leave it as is for a while I guess (at least until I fix the vista install that got messed up at the time of the ubuntu install) I will then check other versions and see if they work, (ubuntu studio, Gutsy etc)

---

### Post by thejackal0101 on 2007-07-18
Im facing the same problem on a Dell D620, i jus have gnome installed 

Cheers,

---

### Post by thejackal0101 on 2007-07-18
this worked for me 

Edit the etc/default/acpi-support and change POST_VIDEO=true to POST_VIDEO=.

Cheers,

---

### Post by thejackal0101 on 2007-07-18
sorry but i guess i jumped the gun here , i rebooted and its gone back to normal 

Any ideas

Cheers,

---

### Post by ndinadis on 2007-07-18
is that a period (.) or blank ( )?
I have tried blank and it did not work for me, I also found this tut which whitelists fglrx and it did not work for me last night when I tried it, (it suckkkkks) 
 [http://debian.helicroc.com/inspiron.html](http://debian.helicroc.com/inspiron.html)

---

### Post by RangerDanger on 2007-07-18
> **ndinadis said:**
> is that a period (.) or blank ( )?
I have tried blank and it did not work for me, I also found this tut which whitelists fglrx and it did not work for me last night when I tried it, (it suckkkkks) 
 [http://debian.helicroc.com/inspiron.html](http://debian.helicroc.com/inspiron.html)


Use the period not a blank.

---

### Post by ndinadis on 2007-07-18
ah alright thank you so much i will have to try that, i always assumed it was blank

---

### Post by RangerDanger on 2007-07-19
> **ndinadis said:**
> ah alright thank you so much i will have to try that, i always assumed it was blank

I started with the period and have never looked back, zero problems for me after deleting True.  I did absolutely nothing else.

---

### Post by ndinadis on 2007-07-19
I have tried it with my modified one (things whitelisted etc) 
I have saved and backed up the file does anyone know how to revert back to the backed up copies so I can re-try with the period alone. Because as it is..... it doesn't work :(

---

