---
title: "disable terminal beep?"
date: 2005-01-06
forum: General Help
---

### Post by earobinson on 2005-01-06
anyone know how i can turn off the terminal beep? dont like my box makine noise unless its music or movies.

---

### Post by nigelng on 2005-01-06
Try this 

Top panel -> Computer -> Desktop References -> Sound

This will appear Sound Preference Dialog, choose System Bell tab then **uncheck** 

Sound an audible bell


Hope u get rid of the noise,
Nigel

---

### Post by nocturn on 2005-01-07
[QUOTE=earobinson]anyone know how i can turn off the terminal beep? dont like my box makine noise unless its music or movies.[/QUOTE]

If you want to do it temporary, just do

```

setterm -bfreq 0

```

---

### Post by earobinson on 2005-01-07
[QUOTE=nigelng]Try this 

Top panel -> Computer -> Desktop References -> Sound

This will appear Sound Preference Dialog, choose System Bell tab then **uncheck** 

Sound an audible bell


Hope u get rid of the noise,
Nigel[/QUOTE]


thanks this worked

---

### Post by Mr_Radarkontakt on 2005-01-09
I have a sound that comes directly from my motherboard. It beeps everytime i erase too far in a terminal window.. The only way I can get rid of it is by starting "softbeep". I can't find any kind of speaker on my motherboard.. 
Does anyone knows how to get rid of it completely? 
If you don't, do you know how to make "softbeep" start automaticly? 



//Mr Radarkontakt

---

### Post by earobinson on 2005-01-12
[QUOTE=Mr_Radarkontakt]I have a sound that comes directly from my motherboard. It beeps everytime i erase too far in a terminal window.. The only way I can get rid of it is by starting "softbeep". I can't find any kind of speaker on my motherboard.. 
Does anyone knows how to get rid of it completely? 
If you don't, do you know how to make "softbeep" start automaticly? 



//Mr Radarkontakt[/QUOTE]
 ya that was the sound i had i got rid of it by doing what was said above. or you could unplug your system speaker but that would be a very bad idea since then you cant get boot error messages

---

### Post by nocturn on 2005-01-12
[QUOTE=Mr_Radarkontakt]I have a sound that comes directly from my motherboard. It beeps everytime i erase too far in a terminal window.. The only way I can get rid of it is by starting "softbeep". I can't find any kind of speaker on my motherboard.. 
Does anyone knows how to get rid of it completely? 
If you don't, do you know how to make "softbeep" start automaticly? 



//Mr Radarkontakt[/QUOTE]

The speaker will not be located on your motherboard.
It will probably be in your case (front).  There should be a connector running from it to your MB.

You could just put 'setterm -bfreq 0' in /etc/profile or /etc/bashrc

---

### Post by kanem on 2005-03-10
hi, 

I also have that annoying beep. None of the suggestions above work. The System Bell tab in Sound Preferences was already unchecked. Strangely, checking results in no change. The setterm -bfreq 0 does nothing either. I also hear it in Firefox if I do a 'find in this page' and there is no match. Could this be a different sound? 

The most aggravating this is that these beeps hijack my sound card for half a minute and I have to wait to start any other program that uses sound.

thanks

Edit:  Turns out it was just a setting in gnome-terminal. There's a checkbox for terminal beep under Edit/Current Profile. Sometimes things aren't as complicated as I expect. Never actually turned it on myself though.

---

### Post by kkass on 2005-08-09
Has anyone found a resolution to this?  For me the beeping is not limited to terminals.  I would be happy if I could get the beep sent to ARTS.  I frequently use headphones at work, and when the beep happens it is sent to the speakers instead of the headphones.  This has the added effect of also sending the music I am listening to to the speakers.  This is sometimes quite loud!

---

### Post by srf21c on 2006-10-23
This article should put your problem to bed:

[http://doc.gwos.org/index.php/TurnOffBeep](http://doc.gwos.org/index.php/TurnOffBeep)

Death to the PC Speaker!!!   :biggrin:

---

### Post by kkass on 2006-10-23
Hey WOW, I completly forgot about this thread (It was over a year ago since the last post.)  But thanks!

Actually you should not need the pcspkr module, I put it in my blacklist and never have a problem.  (Sound in KDE works just fine.)

```

sudo vi /etc/modprobe.d/blacklist

Add the following line:
blacklist pcspkr

```

---

