---
title: "Audacity Broken"
date: 2006-01-25
forum: Desktop Environments
---

### Post by Animortis on 2006-01-25
I use Audacity pretty often, mostly for basic sound recording, but also for its multi-layer recording and editing features. (It's actually very close to an audio recording tool called Pro-Tools used in the radio industry.) However, under Ubuntu, it doesn't seem to work.

As my few problems with Ubuntu so far have been easily solved by forum posts, I'm going to try for this one.

Every time I launch Audacity just after I installed it, I got the following message:
"There was an error initializing the audio/io layer. You will not be able to play or record audio. / Error: Host error."

If you know how to get past this, please tell me. It very much refuses to record any audio, as well as play any audio, and if I want to edit voice clips I'm gonna kinda need it.

---

### Post by aysiu on 2006-01-25
Does [this](http://ubuntuforums.org/showthread.php?t=36823) help?

---

### Post by Animortis on 2006-01-25
It would, except I don't have a clue how to do the stuff in that post.

Where's .audacity and what do I change in it to switch to Alsa support? My superuser is in the audio group, I know that much.

---

### Post by aysiu on 2006-01-25
[QUOTE=Animortis]It would, except I don't have a clue how to do the stuff in that post.

Where's .audacity and what do I change in it to switch to Alsa support? My superuser is in the audio group, I know that much.[/QUOTE] Your *super*user is in the audio group? What about your regular user? See the attached screenshot for what it should look like.

.audacity is a hidden file in your /home directory.
Go to /home/animortis in Nautilus.
Then press Control-H to see hidden files.
.audacity should appear.

I don't know anything about ALSA...

---

### Post by Animortis on 2006-01-25
The user who's trying to use audacity does have that access available in users and groups. I've changed /dev/dsp to have executable, read and write access for all users. The .audacity file in my home folder (I did the hidden search already, but I thought it was a directory file. Oops.) seems to be nothing like the one described in the post. I tried adding the lines mentioned in the post about the Audio-IO, and that did nothing so I removed them.

No progress.

---

### Post by aysiu on 2006-01-26
The only links I could find were for Hoary, but I'm pretty confident they should work for Breezy, too. I've never had to deal with ALSA configuration before.

[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)
[http://ubuntuforums.org/showthread.php?t=25548](http://ubuntuforums.org/showthread.php?t=25548)

---

### Post by Animortis on 2006-01-26
Oi, a little above my head and I'm not sure I'm willing to shed the standard Ubuntu settings, even that far. I'll mess with it shortly and get back to you.

---

### Post by pjbgravely on 2006-01-30
See this thread. [http://ubuntuforums.org/showthread.php?t=117600](http://ubuntuforums.org/showthread.php?t=117600) for a work around to the host error.

---

