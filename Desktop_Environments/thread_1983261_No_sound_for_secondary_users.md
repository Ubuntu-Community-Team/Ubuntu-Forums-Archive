---
title: "No sound for secondary users"
date: 2012-05-20
forum: Desktop Environments
---

### Post by sparek-3 on 2012-05-20
This is a weird problem.  I'm not sure what to check or what the problem could be.

The secondary users on my Ubuntu system are unable to play sound.  I'm not sure when this started.  It was working just fine, but tonight I went to play an mp3 file on a secondary account and it's no go.

Sounds still works fine for the main user.

I'm not sure what information is needed to help diagnose this problem.  This is on a Ubuntu 10.04.4 LTS system with the 2.6.32-37-generic kernel.

---

### Post by papibe on 2012-05-20
Hi sparek-3.

My guess is the secondary user need permission to write to the necessary devices. In particular, audio devices are set in a way that only users belonging to the group 'audio' can access them:
```
ls -l /dev/audio /dev/mixer 
crw-rw----+ 1 root audio 14, 4 2012-05-19 11:14 /dev/audio
crw-rw----+ 1 root audio 14, 0 2012-05-19 11:14 /dev/mixer

```
You can solve it by adding the user to the audio group:
```
sudo usermod -a -G audio secondary_user
```
Hope that helps, and tell us how it goes.
Regards.

---

### Post by sparek-3 on 2012-05-20
Yea, this was the issue.  Thanks!

I'm not sure why this secondary user was taken out of the audio group.  I vaguely remember having this issue when I first created the secondary user, and adding it to the audio group then to make this work.

I was just kind of at wits end last night.  It had worked last week or so, but didn't last night, I couldn't think of any changes I had made.  I still can't think of any changes I made, but I'm sure I must've done something that removed it from the audio group.

At any rate, this is working now.  Thanks for the help!

---

