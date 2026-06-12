---
title: "Sound in Legends?"
date: 2006-07-07
forum: Gaming &amp; Leisure
---

### Post by jISh on 2006-07-07
The game uses OpenAL sound..apparently. Never even heard of that before. 
Since the game doesn't support ALSA, how can I make sound work?

---

### Post by Iarwain ben-adar on 2006-07-07
Hi,
could you give me the complete name of the game please? Or is Legends the complete name?

And do you not have a config for the game? (either GUI wise, or CLI wise?)


Iarwain

---

### Post by DoktorSeven on 2006-07-07
OpenAL is just an API for programs to access your sound, not a replacement for ALSA.

Make sure you have **libopenal0a** installed.  (**sudo apt-get install libopenal0a**)

---

### Post by jISh on 2006-07-07
I have the latest version of libopenal0a
And the game is [http://legendsthegame.net.nyud.net:8080/](http://legendsthegame.net.nyud.net:8080/)

---

### Post by DoktorSeven on 2006-07-07
Is it complaining that it can't use OpenAL, or is the sound just not working?

If the latter, then there's all sorts of things that could be the problem; search the forums for other no sound issues.  Not sure about the former since Legends works fine here with the above library...

---

### Post by jISh on 2006-07-07
If I run it in terminal..

fdhgfdh@dgdsg:~/legends$ bash runlegends
sdgdsg@sdgsdg:~/legends$ open /dev/[sound/]dsp: Device or resource busy


My sound works in other games just fine, even things like Enemy Territory, so I don't see why this would give me a problem.

I tried making sure I had no web browser or music software running in the background, same problem.

---

### Post by DoktorSeven on 2006-07-08
Yeah, that's a sound blocking issue.  Shut down esd (if you're running Gnome) or artsd (for KDE) and see if that helps matters.  If not, search around the forums; others may have had similar issues.

---

### Post by jISh on 2006-07-08
Oh yeah, the killall esd command
Forgot about that one =/
Will give it a try...

Edit: It worked.

---

### Post by fakie_flip on 2007-06-09
Has anyone been able to get Legends to work with Teamspeak? When I run Legends with Teamspeak, it has no sound and crashes. The same thing happens when I use Skype..

---

