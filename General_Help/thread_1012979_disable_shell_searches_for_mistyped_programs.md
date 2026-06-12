---
title: "disable shell searches for mistyped programs"
date: 2008-12-16
forum: General Help
---

### Post by mdecler2 on 2008-12-16
I am a Ubuntu 8.10 user.
 
I would like to disable the shell service that causes a search for every mistyped command, since I usually have an idea of what I wanted anyway.

Was this service integrated into bash? This is really bad. I am quite used to bash, and I don't want to ditch it now.

If you could recommend another shell that has similar configurations and aliasing, please let me know. Alternatively, I could install an older version of bash and let Ubuntu complain every time I update...

---

### Post by eraker on 2008-12-16
I'm not sure what you mean exactly, but forgive me if this doesn't help. It sounds like you are mistyping commands and you don't want bash to spend time searching through $PATH to figure out if it can find that command?

If that's the case, you can always hit CTRL+C in bash to cancel anything. I do this all the time because I have a habit of typing "lz" instead of ls, so I'm pretty quick on the CTRL+C just about every time I type something.

---

### Post by mdecler2 on 2009-11-05
I had forgotten that I solved this and did not post how to remove this "feature".

There has been a new program called command-not-found that adds "interactive functionality" to bash by searching for commands within the repositories if it can't find them in the $PATH directories.

[http://packages.ubuntu.com/search?keywords=command-not-found](http://packages.ubuntu.com/search?keywords=command-not-found)

command-not-found added loads of time to my frequent use of the command line and made my experience inefficient. The reason being, I am a bad typer! I don't need to wait an extra second to search the repos every time I mistype a command...I would much rather have the instant gratification of ```
$ foo
-bash: foo: command not found
```

solution:
```
sudo apt-get remove command-not-found
```

---

