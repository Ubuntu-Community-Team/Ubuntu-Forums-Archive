---
title: "xine not working"
date: 2007-01-24
forum: Desktop Environments
---

### Post by lozenge on 2007-01-24
I updated my OS to edgy to see what would happen and to work on any broken things... but this is just stupid...

xine won't work, at all. I have no sound systemwide, for an unknown reason. Amarok errors out and says that xine can't initialise any drivers... I'm not really sure what to do about it. I've replaced the newest available xine with 1.1.0 but it still does the same thing.

Any ideas?

EDIT: I can run the following command and get white noise, so I'll assume that this isn't a big thing to fix?
```
sudo cat /dev/urandom > /dev/dsp
```

I just came across this, I don't know what relevance it has or does not have, but it seems to be an error with ALSA that could be the issue:
```
james@monkey:~$ esd &
[1] 6353
james@monkey:~$ ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.ipc_key'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM dmix:AudioPCI

```

---

### Post by lozenge on 2007-01-25
Bump?

---

### Post by lozenge on 2007-01-26
Bumping again, hopefully someone will be able to help me out soon.

---

### Post by lozenge on 2007-01-28
Reposting for a third time and hoping I can get some answers to this problem soon.

---

### Post by marrit on 2007-02-07
I've got the same error - messages (not with xine) after updating to edgy. I removed in my home directory: 

.asoundrc
.asoundrc.asoundconf

good luck, marrit

---

