---
title: "Pulseaudio broke after update"
date: 2009-04-11
forum: General Help
---

### Post by rmausser on 2009-04-11
Hi there. 

I am running Ubuntu Studio with an HDA Nvidia sound card, and today i decided that since i had some free time i'd run some updates. 

Well, now my pulseaudio seems to be broken. 

I get sound at login screen (the ubuntu bongos) but they are delayed by 5 seconds. 

Then once I enter gnome via my login, there are no sounds. 

so I killed pulseaudio, and voila, sounds work, BUT they are very laggy and choppy...i think its using the old esound driver or something. 

So i went to reenable Pulseaudio in terminal with

pulseaudio -D

and i get: 

"W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed."

someone please get my sound back... i needs it! 

Thank you.

PS. I want to maybe upgrade to Jaunty, hoping this will fix the problem (I noticed there are new pulse updates in the update manager, but they are greyed out due to conflicting packages. 

Do you think this is wise, or will upgrading to jaunty just mess things up more? I have tweaked the settings of this computer quite extensively. (mythbuntu packages enabled, syncing over bluetooth with Windows mobile 5 device, getdebs etc)

thanks

Rob

---

### Post by schmidtbag on 2009-04-11
It wouldn't surprise me that Jaunty will fix your problem.

I feel so bad for you, I have the same audio and had a TERRIBLE experience with it, it got even worse when I used pulseaudio and I uninstalled that altogether.  if you are going to uninstall it BE SURE TO REMOVE IT FROM THE SESSIONS PROGRAM.  if you don't ubuntu will refuse to boot up.  you can ignore the fact that it wants to remove "ubuntu-desktop".

Honstly you're better off getting a different sound card to fix your problems.  really, anything will do better.  i have a soundblaster live! EM10K, which is over 10 years old and that thing works great and does more than the HDA sound does

---

### Post by rmausser on 2009-04-12
I am on a laptop and thus cannot

Guess what.... Jaunty did not fix my problem...now there is no sound at all! not even at login.

someone help!

what information should I post?

---

### Post by schmidtbag on 2009-04-12
well is there a driver at all in the Sound settings in the preferences menu?  you don't want autodetect, try alsa.  if not, do "lsmod" and try finding anything related to sound and post it here.  it might be labeled as "snd" or pcm

---

### Post by rmausser on 2009-04-12
I just wanted to mention, that only some sounds work, and some do not

The login bongo sounds work, the 'notification' sounds in Pidgin do, and occasional system sounds

but music, video, flash videos (youtube) or anything else has no sound.

Even the "alsa" setting in the Sounds manager will "test" correctly, but system sounds still wont play?

---

### Post by schmidtbag on 2009-04-12
i know someone who had the exact same problem.  what is your media player?  maybe you just picked the wrong device.

you should open up the volume control settings too, and make sure "wave" "master" and most important of all, "pcm" are set mostly up, if any one of those are down then it'd make perfect sense why you can't play all sounds.  if any of those features arne't there, click on the preferences button.  when you open the program, the default device should show up.  if its not alsa, its probably not working right.



if all else fails, do OSS

---

