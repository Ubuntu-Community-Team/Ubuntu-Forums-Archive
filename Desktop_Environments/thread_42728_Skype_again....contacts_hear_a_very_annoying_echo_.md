---
title: "Skype again....contacts hear a very annoying echo of their own voice"
date: 2005-06-19
forum: Desktop Environments
---

### Post by greatshape on 2005-06-19
Hi, 

I installed Skype as described here [http://ubuntuguide.org/temp/#skype](http://ubuntuguide.org/temp/#skype)
It works, and also the echo123 test is ok. 
But, when i go in conversation with someone, the other person hears an incredible echo of their own voice. I tried it myself with my laptop, and it's really annoying, almost impossible to have conversation like this. Nobody wants to skype with me anymore now  :grin:   [-X 
Before i was running suse and using the rpm provided, everything worked as a charm.
Anyone who has a solution for this?
Many thanks,

Regards, steve :wink:

---

### Post by desdinova on 2005-06-19
[QUOTE=greatshape]Hi, 

I installed Skype as described here [http://ubuntuguide.org/temp/#skype]("http://ubuntuguide.org/temp/#skype")
It works, and also the echo123 test is ok. 
But, when i go in conversation with someone, the other person hears an incredible echo of their own voice. I tried it myself with my laptop, and it's really annoying, almost impossible to have conversation like this. Nobody wants to skype with me anymore now :grin:   [-X 
Before i was running suse and using the rpm provided, everything worked as a charm.
Anyone who has a solution for this?
Many thanks,

Regards, steve :wink:[/QUOTE]

Is your microphone sensitivity up too high, so its picking up your speakers?

---

### Post by greatshape on 2005-06-19
[QUOTE=desdinova]Is your microphone sensitivity up too high, so its picking up your speakers?[/QUOTE]

No, i'm using a headset, that is certainly not the problem.
When i'm using skype under windows (on the same machine) everything works fine.

---

### Post by greatshape on 2005-06-21
*BUMP* anyone?

---

### Post by greatshape on 2005-09-13
I'll bump this again, hoping that somebody is able to help.
This problem still ain't solved !! 
Am i really the only one experiencing this problem? :? 

Regards, Steve

---

### Post by paulmilliken on 2006-01-12
[QUOTE=greatshape]I'll bump this again, hoping that somebody is able to help.
This problem still ain't solved !! 
Am i really the only one experiencing this problem? :? 

Regards, Steve[/QUOTE]
You have to run alsamixer and turn capture off (using the space key).

Paul

---

### Post by cbandeira on 2006-06-25
I'm not sure if the above post worked for you, but anyway:

1 - Open the terminal and start alsamixer;
2 - Press F4 (so you select "capture")
3 - Go to PCM by pressing left and set it to zero.

That solved the problems here :cool: 
See ya

Carlos

---

### Post by cbandeira on 2006-06-27
[QUOTE=cbandeira]I'm not sure if the above post worked for you, but anyway:

1 - Open the terminal and start alsamixer;
2 - Press F4 (so you select "capture")
3 - Go to PCM by pressing left and set it to zero.

That solved the problems here :cool: 
See ya

Carlos[/QUOTE]

Forgot to say how to store the mixer settings:

[INDENT]sudo alsactl store[/INDENT]

There you go!

---

### Post by annazack on 2006-07-11
How do I set it to zero?

Do i press escape then to leave alsamixer and then save the settings with the command?

//Anna

---

### Post by joehill on 2006-07-14
I'm having the same problem.  Everyone I try to talk to reports a very loud echo and insists on using a land line.  I tried following the steps above to no avail.  My interlocutor tells me that when I turn PCM way down the echo decreases a little (but it's always still there), but then, of course, they become nearly inaudible to me.  I've muted the capture (I'm surprised it needs a sudo command to make it stick--otherwise it turns itself back on).  I'm not sure changing the capture settings actually does anything.  Changing the microphone volume or muting it doesn't seem to make any difference either.

---

### Post by WhoDaBear on 2006-08-04
Worked for me.  Thanks!

---

