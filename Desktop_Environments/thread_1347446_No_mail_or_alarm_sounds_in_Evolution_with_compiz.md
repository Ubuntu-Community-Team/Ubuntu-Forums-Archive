---
title: "No mail or alarm sounds in Evolution with compiz"
date: 2009-12-06
forum: Desktop Environments
---

### Post by pataphysicianu on 2009-12-06
Using Ubuntu 9.10. Evolution is working fine without compiz, if I get a new mail I get a sound, and also choosing a custom sound works as well with wav files. Calendar sound alarm works either with default sound or custom wav file.

Then I turn on compiz, now Evolution won't make a sound, of any type. I did get the mail notification plugin to play a custom sound, but this will only work for first new email, calendar alarms will not work, no matter if default sound or custom.

---

### Post by Boondoklife on 2009-12-06
I have never been able to get evolutions audio alerts to work right, it will be interesting to see if anyone has.

---

### Post by LuisGMarine on 2009-12-06
wow I didn't even know that evolution did that kind of stuff.  Maybe that will be my next project is to try to have evolution give me sounds! :popcorn:

---

### Post by Boondoklife on 2009-12-06
Yea I seen that it did the audio alerts and thought wow, this is perfect for an alarm to tell me to get to my next class... That is until it never made a peep!!!

---

### Post by pataphysicianu on 2009-12-07
I have figured out the problem, It's because of two bugs, one a complex one that seems fixed everywhere but compiz, and one in evolution that has been in existance for over two years.

The compiz bug causes evolution's use of default system sounds not to work, This can be fixed for mail notifications with a custom sound in the mail notification plugin, this now seems to be working for me, and not just on the first email. 

The alarms for calendar won't work again because with compiz, evolution can't make the default system sound, but unfortunately there is a two year old, well documented bug, that would seem very easy to fix, in evolution using custom sounds, which causes custom sounds not to work. You can kludge a fix by choosing "running a program" for custom notification and then say use aplay or ogg123 to play a sound, This seemed like too much work (have to do these steps for each alarm) with the possibility of typing mistake screwing you over, so it doesn't meet my reliability requirement.

All in all, my re-re-re-foray into evolution has shown that it indeed sucks. So I'm using Thunderbird with lightning and several other extensions, I now get better mail notification and alarms than with evolution, even when it was working without compiz. I much prefer an email notice with who and what the email is.

---

