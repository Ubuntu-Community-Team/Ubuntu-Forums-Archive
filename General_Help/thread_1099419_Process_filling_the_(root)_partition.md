---
title: "Process filling the (root) partition"
date: 2009-03-18
forum: General Help
---

### Post by kramulous on 2009-03-18
Hi,

I've been having an issue that pops up from time to time and I'm looking for a better solution.

If I have a process that is writing text to a file, fills the partition but I cannot kill the process, what is the best way to deal with this. Please note, yes I could kill the process but I must stress that this cannot occur.

Presently, I try using sed to start deleting lines of text from the beginning of the file, so that space can be available on the partition and eventually, the monitoring process will kill the process writing the file.

But I don't like using

```
sed -i -n '1-10000000d' filename > /dev/null
```

(or some variant) as sed will create a temporary file. I sometimes try using the temporary file on another partition (another only being available on a network). This also takes a really, really long time (as the offending file can be greater than a couple hundred gigabytes).

The partition in question is /

Any thoughts?

---

### Post by geirha on 2009-03-18
If the process shouldn't be killed, then it should really provide the ability to rotate its own log file. I don't see any other options.

EDIT:
Oh wait, does the process have the ability to log to syslog? If so, you can safely let logrotate rotate syslog's log files. If it doesn't have the ability to log to syslog, you could have a separate process that tails the log file and sends it to syslog.

```
tail -f /var/log/thelogfile.log | logger -p local0.notice
```

You'll have two sets of the same log, but you can logrotate the logs sent to syslog, and truncate your process's logfile once in a while.
```
> /var/log/thelogfile.log
```

---

### Post by kramulous on 2009-03-18
Unfortunately, file rotation is not an option as the process that is creating the large file is some simulation (own code, some program, etc).

---

