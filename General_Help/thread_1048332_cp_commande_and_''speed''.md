---
title: "cp commande and ''speed''"
date: 2009-01-23
forum: General Help
---

### Post by yield999 on 2009-01-23
Hi Folks,

I am scripting something to connect to a Windows server and transfer files automaticly to a local linuxbox I have.

That part is done and working fine. 

My question is, since I don't see what my script is doing while running, how can I know what pucentage of my file have been copied over and in what amount of time ...
May be I shold use SCP instead ?...

---

### Post by boof1988 on 2009-01-23
> **yield999 said:**
> My question is, since I don't see what my script is doing while running, how can I know what pucentage of my file have been copied over and in what amount of time ...
May be I shold use SCP instead ?...

I don't know an option to give the percentage...  But, I believe, you can use: ```
-v
``` as an option and that will display what file is currently being copied.

Also...```
man cp
``` may give some good ideas.

---

### Post by hyper_ch on 2009-01-23
doesn't "cp" has a "-v" option?

---

### Post by Slim Odds on 2009-01-23
> **hyper_ch said:**
> doesn't "cp" has a "-v" option?

Yes, but it doesn't show progress, just the filenames

---

### Post by sedawk on 2009-01-23
You can add "date" command at the start and end of the script and
then check from the output how long it took from start to end.
```

...
echo "Starting at $(date)"
...
echo "Finished at $(date)"
exit 0

```

The "time" command may be your friend, e.g put it simply (on the
same line) before your "cp" or "scp" command or start your script
with it. Here I time the sleep command:
```

time sleep 10

real	0m10.003s
user	0m0.000s
sys	0m0.008s

```

---

### Post by puppywhacker on 2009-01-23
when I copy files I always look at the filesize of the file I'm going to copy versus the destination file. you would see the filesize increase everytime the meta-data is updated. That way you can check progress regardless of underlaying copy methods.

SCP has the benefit of encryption and showing the progress-bar. But has as drawback that encryption slows down copying and the progress-bar is hard to script around.

---

### Post by Slim Odds on 2009-01-23
I think that's looking for progress..   Not just completion info

---

### Post by hyper_ch on 2009-01-23
wget can show progress... I don't know and have never tried it... but maybe you can also "wget /path/to/folder/file" from a directory...

---

### Post by caljohnsmith on 2009-01-23
Instead of using "cp", you might want to check out "rsync" which is a much more powerful version of cp. It has a "--progress" flag that shows the progress of the copying, so you could give that a try.

---

### Post by Slim Odds on 2009-01-23
> **hyper_ch said:**
> wget can show progress... I don't know and have never tried it... but maybe you can also "wget /path/to/folder/file" from a directory...

wget is only for http or ftp transfers

---

