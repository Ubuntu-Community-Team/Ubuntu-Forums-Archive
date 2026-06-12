---
title: "Backup open files without manual client installation"
date: 2009-02-03
forum: General Help
---

### Post by supanatral on 2009-02-03
I'm looking to backup open files on a windows computer without having to manually install something on the client computer. It's ok to install something on the client computer but it would have to be a push install from the linux box. Is this possible?

---

### Post by Titan8990 on 2009-02-03
Your post is a bit confusing. First you say that you can't install anything on the client machine and then you say that you can....


If you can't install anything then you only have 2 options: copy and NTBackup


If you can install something, I recommend delta copy (rsync for windows). It actually doesn't need to be installed, just unzipped to a directory.

---

### Post by supanatral on 2009-02-03
Sorry, if I confused you. put it this way, I don't want to walk around to all the client machines and install something. But if the ubuntu server can push out an install file to the client and have it installed automatically, then that's ok.

the issue if I'm not mistaken is that rsync can't copy open files, can it?

---

### Post by Titan8990 on 2009-02-03
> the issue if I'm not mistaken is that rsync can't copy open files, can it?


I am uncertain of that. If all the Window's machines have shares, you can push delta copy to all the shares but I am not sure how you would push the schedules as I think it uses the windows scheduler.

---

### Post by supanatral on 2009-02-03
Ya, but then that still depends on the client. I'd rather a centralized managed system otherwise its no better then what we have now. Right now, we're just using windows backup which does the job.

If it can't be done, then it can't be done I guess.

---

### Post by Titan8990 on 2009-02-03
Alright, I think Acronis is exactly what you are looking for but I usually don't like to recommend proprietary products...

---

