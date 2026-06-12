---
title: "[SOLVED]No sound for games Ubuntu 8.10"
date: 2009-01-10
forum: Desktop Environments
---

### Post by sullenx on 2009-01-10
There are a lot of threads open for sound issues for 8.10 and already a lot of people agree that Pulseaudio was not configured correctly and gave a lot of headaches to get sound working.  I myself, had great deal of difficulty trying to fix my sound issues and looking through a lot of forums I've found that the following made it work. 

1) Remove Pulseaudio 
   A simple "sudo apt-get remove pulseaudio" will do the job, of course there are other stuff left in the system that you will have to remove. I googled it and it was easy to remove

2) Install alsa. Also, google it.  Also make sure that you can see your card using the alsamixter

3) Install aoss.  This made Americas army work for me.  Of course i had to play around with the OpenAL configuration file and also i used the asoundconfig-gtk to select my default sound card.

I spent quite of bit of time figuring this stuff out.  I personally think i is a bit excessive, but to my fortune I'm on vacation. :)

As far as Pulseaudio. I see this idea like compiz, it's nice and everything, but with so many bugs for now i'll just stick to what works.  Of course, the nice thing about using linux is the fixing part :D

---

### Post by nightfire117 on 2009-01-22
I am glad that you made this post, I don't know yet if it works for me (this is a *horrible* problem with 8.10... Pulse was just implemented poorly from what I gather), but it's asoundconf-gtk, not asoundconfig-gtk hehe. Again thanks and keep it up! And have a good (belated?) vacation. =P

~Night

---

