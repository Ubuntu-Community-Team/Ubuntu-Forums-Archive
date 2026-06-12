---
title: "Thunderbird Settings from Windows?"
date: 2009-05-19
forum: General Help
---

### Post by markwilliams666 on 2009-05-19
Hi all,

Been using Ubuntu for a few weeks now. A wee question that I wonder if anyone can help with..

I've used Mozilla Thunderbird on a windows PC for my email & diary for ages. Is there a way to easily transfer all the settings across to Thunderbird in Linux?

I know I can export the calender as as an ICS file & import it. I can set up the individual email accounts but I want to bring my sent items, inbox over too.

There a program called Moz backup that does the job on windows.

Anything like it available for Ubuntu?

Ta

---

### Post by Concrete on 2009-05-19
Yes its possible ;)

In Windows, type in Run, %APPDATA% then find Mozilla, then Thunderbird, open profile, copy profile.

In linux (when u installed TB right..) go to /home/yourusername/.mozilla-thunderbird and there past ur profile from windows and evrything should works 1/1.

It works for me just fine...

---

### Post by paradigm2 on 2009-05-19
> **markwilliams666 said:**
> Hi all,

Been using Ubuntu for a few weeks now. A wee question that I wonder if anyone can help with..

I've used Mozilla Thunderbird on a windows PC for my email & diary for ages. Is there a way to easily transfer all the settings across to Thunderbird in Linux?

I know I can export the calender as as an ICS file & import it. I can set up the individual email accounts but I want to bring my sent items, inbox over too.

There a program called Moz backup that does the job on windows.

Anything like it available for Ubuntu?

Ta

I'm unsure if it will work the same from windows -> Linux, but for Linux -> Linux, I just copied my profile (found in ~/.mozilla-thunderbird) over to the other computer.  Then I edited the file profiles.ini (I believe, perhaps it was profiles.conf) and pointed it towards that new profile.  Everything then worked great!  You might try it.

---

### Post by SentientFluid on 2009-05-19
You can [share profiles]("http://ubuntuforums.org/showthread.php?t=1138477") between Windows and Ubuntu.

Remember when sharing or moving your profile, some add-ons may not be compatible with both operating systems. These typically get disabled automatically.

---

### Post by CatKiller on 2009-05-19
You can just copy the profile across. The Mozilla products all have their own structure, so as long as the files are all there it will work.

---

### Post by markwilliams666 on 2009-05-20
Thanks all,

I'll give it a whirl & report how I get on

---

### Post by Meuro on 2009-07-21
This solution works a treat.  Thanks very much

---

