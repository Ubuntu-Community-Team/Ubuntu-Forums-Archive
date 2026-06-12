---
title: "Active sudo or root  alert ?"
date: 2009-05-02
forum: General Help
---

### Post by hufferd on 2009-05-02
This may seem like a stupid question but is there a way to set the system to change to a different background when sudo is active (ie. the 15 min time window after sudo is entered?) or also changing background if root is active? 

Kind of like an alert system I guess? 

Any ideas?

---

### Post by codeseer on 2009-05-02
There may be. I'll give it some thought. You could probably set it up as a bash script and pass the parameters through that instead of sudo; but this may pose some security issues, unless you're well protecting the bash script. There should be some way of polling the sudo timeout countdown also.

However, why, may I ask, are you, yourself, wanting to do this?

I recommend setting the sudo timeout to 0, so that it always prompts for a password; however, everyone's needs and paranoia are different.

Edit:

I can't think of a way to grab the output of a command that has sudo in it without being prompted for the password. If you could do that, then you could tell that way when sudo was active.

---

### Post by hufferd on 2009-05-02
> **codeseer said:**
> There may be. I'll give it some thought. You could probably set it up as a bash script and pass the parameters through that instead of sudo; but this may pose some security issues, unless you're well protecting the bash script. There should be some way of polling the sudo timeout countdown also.

However, why, may I ask, are you, yourself, wanting to do this?

I recommend setting the sudo timeout to 0, so that it always prompts for a password; however, everyone's needs and paranoia are different.

Edit:

I can't think of a way to grab the output of a command that has sudo in it without being prompted for the password. If you could do that, then you could tell that way when sudo was active.

I really have no reason to want to do it other then wanting to LOL But with that said ... I have never changed the default time out of sudo but you bring up a good point maybe I should :confused:

---

### Post by codeseer on 2009-05-02
> **hufferd said:**
> I really have no reason to want to do it other then wanting to LOL But with that said ... I have never changed the default time out of sudo but you bring up a good point maybe I should :confused:

```

sudo visudo

```

Change your Defaults line to look something like this, eseentially tacking on the timeout part:

```

Defaults        env_reset,timestamp_timeout=0

```

---

