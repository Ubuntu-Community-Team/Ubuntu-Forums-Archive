---
title: "Mnemosyne doesn't launch at all (only error message)"
date: 2009-02-27
forum: General Help
---

### Post by s3a on 2009-02-27
When I choose to launch mnemosyne wehther as user or as root, it gives me an error message. When I try to launch it as user (by clicking the launcher and not using terminal) I get an error saying "Either Mnemosyne didn't shut down properly or another copy of Mnemosyne is still running. Continuing in the latter case could lead to data loss!" to which I can select either "Exit" or "Continue." I select "Continue" and then get another error message saying "Unable to load database. Creating tmp file." and I can only select "Ok" to that and then nothing happens. Anyone have an idea as to what I need to do?

Any help would be greatly appreciated as always!
Thanks in advance!

---

### Post by yeats on 2009-02-27
You could try:

```

ps ax | grep mnemosyne
```

which should show the duplicate process, which you could then kill manually:

```
kill *pid*
```

where "pid" is the process id number.

---

### Post by s3a on 2009-02-27
> **chrissharp123 said:**
> You could try:

```

ps ax | grep mnemosyne
```

which should show the duplicate process, which you could then kill manually:

```
kill *pid*
```

where "pid" is the process id number.

What exactly is "duplicating the process?" And why would I want to kill it? I want to be able to run it so that I can study! :(

---

### Post by s3a on 2009-02-27
I just had to go to home/**username**/.mnemosyne/ and then I had to delete config and config.py and then ran it as user (=normally) and then Mnemosyne just recreates the two files by re-asking you to configure Mnemosyne! Thanks for your help though!

---

