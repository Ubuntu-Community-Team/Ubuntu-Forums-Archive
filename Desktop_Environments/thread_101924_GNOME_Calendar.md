---
title: "GNOME Calendar"
date: 2005-12-10
forum: Desktop Environments
---

### Post by BorgHunter on 2005-12-10
I have what seems to be a very simple problem, but for some reason, I have not seen any simple ways to fix it. In 4.10 and 5.04, the week always started on Sunday in the Calendar. However, in 5.10, I find that the week starts on a Monday. I want to fix this. I tried messing with the week settings in Evolution, but apparently that doesn't transfer over to GNOME Clock.

---

### Post by matthew on 2005-12-10
I don't know how to change it, but I can give a rationale for why it is like it is. Lots of places (maybe most?) outside of North America print their calendars with Monday as the first day of the week.

It would be nice to have the option to do it either way...maybe that's in the works for the next Gnome version...I haven't seen any way to change it right now.

---

### Post by BorgHunter on 2005-12-11
Yeah, I understand why, just not why it's not easily fixable. Ideally, it should set itself based on what country you chose in the initial setup of Ubuntu.

---

### Post by aysiu on 2005-12-11
KDE's flexible in this way... right-click on the clock, select "date and time format."

---

### Post by jegerjensen on 2005-12-14
This is weird...  I am sitting in Norway trying to find a way to make monday the first weekday.   Maybe we should just swap computers?

---

### Post by taurus on 2005-12-14
If you can't change it, then maybe you should look into gdeskcal, [http://www.pycage.de/software_gdeskcal.html](http://www.pycage.de/software_gdeskcal.html).  After you install it with apt-get or synaptic, run it from a terminal for the first time as

gdeskcal first-day=7 
(for Sunday...)

From then on, the first column will be Sunday each time you start gdeskcal!

---

### Post by Hairy_Palms on 2005-12-14
ive always wished you could make monday the first day of the week in the calender too, but ive never figured out how no matter how much googling i do.

---

### Post by dcstar on 2005-12-14
[QUOTE=Hairy_Palms]ive always wished you could make monday the first day of the week in the calender too, but ive never figured out how no matter how much googling i do.[/QUOTE]
I believe this is set in the LOCALE for your system, and the calendar should take that setting.

Now, how you go about modifying the locale is another issue.........

---

### Post by bionnaki on 2005-12-15
monday is set as the first day for me...

---

### Post by dcstar on 2005-12-15
[QUOTE=bionnaki]monday is set as the first day for me...[/QUOTE]
And your LOCALE is?

---

### Post by anil_robo on 2005-12-16
Can someone please write a detailed how-to for using locale through commandline for the newbies? Thanks! :)

---

### Post by harfooz on 2006-01-03
I'm having the same problem as described, and haven't found a solution. I want the Gnome calendar to start each week with Sunday, rather than Monday. There is no such configuration available in the Preferences. I'm in the US and using a default Breezy installation.

Hoping someone has a solution!
harfooz

---

### Post by mrmcctt on 2006-01-03
[QUOTE=taurus]If you can't change it, then maybe you should look into gdeskcal, [http://www.pycage.de/software_gdeskcal.html](http://www.pycage.de/software_gdeskcal.html).  After you install it with apt-get or synaptic, run it from a terminal for the first time as

gdeskcal first-day=7 
(for Sunday...)

From then on, the first column will be Sunday each time you start gdeskcal![/QUOTE]

Use ```
gdeskcal --first-day=7
```

Works for me.  Now starts on Sunday

---

### Post by dpm on 2006-01-15
As a GNOME user, I also found that I could not change the day the week starts through the GUI, so after doing a bit of research I solved this problem on my system. Here's how I did it. I take no credit for this solution, since it is all based on information I found from other posts or on google. 

The problem was, I think, that the first day of the week, which should be defined in your locale configuration file, is not correct for all locales. For example, in Breezy, for en_US, the first day of the week is Monday, whereas for en_GB it is Sunday.

Anyway, this worked for me:

**1.-** Determine your locale: 

either a) in /etc/environment or b) by running

  ```
locale
``` 
in a terminal

the locale should look like:

 <language>_<location>.<encoding> (I don't know if these are the correct terms, though)

So, for example, for UK English, the locale should look like:

  en_GB.UTF8

** 2.-** Once you know exactly your locale, find its corresponding configuration file in /usr/share/i8n/locales:

(/usr/share/i8n/locales/en_GB following the previous example)

# And edit it as follows:

```
sudo gedit /usr/share/i8n/locales/<yourlocaleconfiguration>
``` 
add 

```
first_weekday 2
first_workday 2
``` 

between **LC_TIME** and **abday** in the LC_TIME section. The number 2 represents the day of the week, so in case another day is to be used as a start, another number can be chosen here.

**3.-** Run the following command in a terminal

```
sudo locale-gen
``` 

**4.-** **Reboot** your computer and you're done. Your week should start on Monday now.

You may find the information on these links also useful:

[https://wiki.ubuntu.com/LocaleConf]("https://wiki.ubuntu.com/LocaleConf")

[http://www.ubuntuforums.org/showthread.php?t=84369&page=2]("http://www.ubuntuforums.org/showthread.php?t=84369&page=2&highlight=day+week+monday+locale")

[http://bugzilla.ubuntu.com/show_bug.cgi?id=16168]("http://bugzilla.ubuntu.com/show_bug.cgi?id=16168")

---

