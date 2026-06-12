---
title: "TeamSpeak Problems"
date: 2005-07-09
forum: Gaming &amp; Leisure
---

### Post by Williams477 on 2005-07-09
I installed TeamSpeak with no problem at all. But when I try to run it from the directory instead of the terminal nothing happens. So I tried to run it from the terminal and it told me I needed to delete a tmp file:

> tony@ubuntu:~$ /home/tony/TeamSpeak2RC2/TeamSpeak
teamspeak is already running, redirecting startupinfo
If teamspeak is not running, delete the file "/tmp/.lock_teamspeakclient"


I deleted the file and tried again but still nothing. Come to find out, the file keeps coming back. Somebody on the teamspeak.org forums said I needed to kill esd if it was running. It was running so I killed it and I lost all sound but TeamSpeak did come up. I logged in and my speech/hearing was muted and couldn't turn it off. I figure that has something to do with me killing esd but that is the only way to get TeamSpeak to load.

Any ideas?

Is there a way I can change esd to oss?

---

### Post by adwait on 2005-07-09
Hi,

Try System>Preferences>Sound. Chane the default to ALSA or OSS and try :)

I am not sure about the game, but I guess if you could set it up to use ALSA, there would be no problem.

---

### Post by Williams477 on 2005-07-10
There isn't a default option.

It just says enable sound server startup and sounds for events

I'm trying to edit it in the Multimedia System Selector, but ESD is the only one that works. I get 'failed to construct pipeline' errors on the others.

---

### Post by adwait on 2005-07-10
Uhh sorry, I meant System>preferences>Multimedia Selector. Try changing the defaul sink not the source.

---

### Post by Williams477 on 2005-07-10
That's what I changed and it still doesn't work. I can go into my system monitor and kill the ESD manually then TS comes up, but then I lose my sound all together.

---

### Post by adwait on 2005-07-10
[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

Try that. Not exactly related, but when u do that the sounds work in various applications even after turing off the ESD. Worth a try I guess.

---

### Post by Williams477 on 2005-07-10
Now I'm completely confused. I went ahead and killed ESD and my CD that I had going is still playing so I didn't lose my sound, but I still can't get Teamspeak to load and the .lock teamspeak file is still there.

edit: I turned off the CD and it loaded but now my sound is going completely again and I am being muted by the teamspeak and I can't turn it off.

---

### Post by adwait on 2005-07-10
The CD player might have been using ALSA or OSS, so its sound didnt stop.....

---

### Post by Williams477 on 2005-07-10
Thanks for your help.

I got it finally. Teamspeak was set to use ESD, when I was allowed to log in I changed it to OSS so now I have sound again. Thanks again

---

### Post by Jet2k5 on 2005-07-10
So does this mean that you have both sound and Teamspeak working perfectly together?  If so great also write a [solved] on the title so that others can see that it has been solved and still not an open issue.  It just helps keep tracks of posts for me.    And maybe others  :smile: 

Hope this is going to work on 64-bit ....

---

### Post by Williams477 on 2005-07-10
I don't know if it's completely fixed yet. I killed the ESD and lost sound to Gaim and things like that but that's when Teamspeak came up and I changed it's feed to OSS. So, in theory, now that it is on a different feed, I should have sound and TS working together.

---

### Post by adwait on 2005-07-10
For multiple sounds to work use the link that I gave you....
And no, multiple sounds cannot work with OSS because it takes control of the sound card. You will need the sound server for other sounds.

---

### Post by Williams477 on 2005-07-10
I tried to install that earlier but I got this message:

> Reading package lists... Done
Building dependency tree... Done
Package libesd-alsa0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libesd-alsa0 has no installation candidate

---

### Post by Williams477 on 2005-07-10
I tried that, finally got the install file to work, I needed to update somethings. Anyways, it still doesn't work. Something I think is messed up with the ALSA because I can't get the test to play. I can't get any of the tests to play.

---

