---
title: "crontab issues."
date: 2005-12-05
forum: Desktop Environments
---

### Post by nxn on 2005-12-05
I've been trying to have crontab play an mp3 file on a daily basis at a specific time (alarm clock if you will), however at most it only plays the first second of the file and then shuts off. 

Here's what I'm doing:

I have a file called alarm that is executable, inside it there's the command "mplayer <mp3 location>", doing ./alarm in the terminal starts to play the song, and it runs through it until the song is finished, so no problems there. However as soon as I try to execute it through crontab it only plays the first second and then stops. I have tried "crontab -e" then putting "00 8 * * 1-5 /home/nxn/alarm" in it and saving, and although it does start, I only hear a second. Same thing happens if I try to do it by editing /etc/crontab with my entry. I have also tried to just put the mplayer command directly into the crontab entry, but no change.

Any ideas?

---

### Post by DMon on 2005-12-05
Try to add an & after mplayer <mp3 location> seems like cron doesnt let go of the process.

---

### Post by nxn on 2005-12-05
Didn't change anything.

---

### Post by quonsar on 2005-12-06
try adding nohup, as in:

nohup mplayer <mp3location> &

---

### Post by nxn on 2005-12-07
Unfortunately that didn't affect it in any way when executing through crontab, if I run it myself my mplayer output doesn't display in the terminal so I'm assuming there aren't any problems with nohup. Also, instead of putting it in the alarm file itself I also tried it right from crontab and still no luck.

I'm pretty sure vixie-cron would work, at least it does on my gentoo box. Would getting that and removing anacron/cron create any problems with ubuntu?

---

### Post by flopsy on 2005-12-07
This worked for me:
```

59 15 * * 1-5 mplayer /home/gee/Music/Destroy\ Rock\ \&\ Roll/Mylo/01\ Valley\ of\ the\ Dolls.mp3  </dev>& /dev/null&

```

---

### Post by nxn on 2005-12-07
Oh snap, that does work. Thanks man.

---

