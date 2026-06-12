---
title: "Crontabs and www-data user"
date: 2010-03-14
forum: Desktop Environments
---

### Post by osa2t on 2010-03-14
Hello !

I have problem with crontabs. I have Ubuntu 9.04 Desktop. I install in my ubuntu mpg321 music player. In system I have 3 crontabs in:
```
/var/spool/cron/crontabs/

osa2t
root
www-data
```

When I add cron jobs

```
* * * * * mpg321 /path.../1.mp3 
```

In osa2t and root jobs works correct (I have music in speaker) , but in www-data user don't play any sound. If I add other jobs example to put some data to SQL, jobs works correct in all user. 
So my quastion is why mpg321 software don't work in www-data? How I can fix this?

---

### Post by mister_p_1998 on 2010-03-15
you should have the FULL path to your music player in the Cron eg

usr/bin/musicplayer not just musicplayer.

Steve

---

### Post by osa2t on 2010-03-15
Hello mister P,

I try run crobjobs with full path, and it's works only in osa2t and root crontable not in www-data (apache) user. Maybe You have other idea what I can do ?

---

### Post by mister_p_1998 on 2010-03-16
Hmm, well heres what I do to play music on a cron:

# Start Radio Paradise
32 08 * * 1-5 DISPLAY=0 &&  /usr/bin/cvlc [http://www.radioparadise.com/musiclinks/rp_128.m3u](http://www.radioparadise.com/musiclinks/rp_128.m3u)

This launches a command line version of VLC, might be worth ditching mpg321 in favour of this.
Steve

---

### Post by mister_p_1998 on 2010-03-16
> **osa2t said:**
> Hello !

I have problem with crontabs. I have Ubuntu 9.04 Desktop. I install in my ubuntu mpg321 music player. In system I have 3 crontabs in:
```
/var/spool/cron/crontabs/

osa2t
root
www-data
```

When I add cron jobs

```
* * * * * mpg321 /path.../1.mp3 
```

In osa2t and root jobs works correct (I have music in speaker) , but in www-data user don't play any sound. If I add other jobs example to put some data to SQL, jobs works correct in all user. 
So my quastion is why mpg321 software don't work in www-data? How I can fix this?
Could be the user name is confusing the system? does ANY cron job work in www-data?

Steve

---

### Post by osa2t on 2010-03-16
I check cvlc and he works only in osa2t user, www-data don't play any sound (I check local mp3 and internet link to radio from You) so maybe it not software player is problem, maybe www-data user don't have powers to use audio device? but I don't have idea how I can check this. I don't have other cronjobs is www-data user. If user name is confusing the system? I don't know, it's  standard user when I install apache server.

---

### Post by asmoore82 on 2010-03-16
are you running pulseaudio?
If so, www-data probably isn't allowed to playback sound.

---

### Post by osa2t on 2010-03-16
yes I have run demon pulseaudio. If I kill process "pulseaudio -k" I don't have any music in all user. If I play some music and after that I kill pulseaudio me music is turn off.

---

