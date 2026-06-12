---
title: "dd image over scp"
date: 2006-08-12
forum: Desktop Environments
---

### Post by dmizer on 2006-08-12
i think this is possible, i'm just unsure of the syntax.

so i need to make an image and send it via ssh.  i can't save the image first and send it later because there's not enough space remaining on the host.

so i'm looking for something like:
dd if=/dev/hda of='scp [email]root@targetip:/file/save/path.iso[/email]'

which i know does not work.  anyone know how this can actually be accomplished?

---

### Post by chavo on 2006-08-12
I found this little gem on google. I've never tried it of course, but it sounds feasible. You'll have to substitute the "emerge" part for apt-get install. I'm not on my Linux box at the moment so I can't tell you if netcat is in the repos either, but it should be easy to install regardless.

[http://gentoo-wiki.com/HOWTO_Backup#Backing_up_a_whole_partition_on_a_remote_machine](http://gentoo-wiki.com/HOWTO_Backup#Backing_up_a_whole_partition_on_a_remote_machine)

---

### Post by dmizer on 2006-08-12
yeah ... i actually bumped into that very site earlier in my search.

here's from the site:
> Be aware that this is a rather liberal use of the word "remote". This method is neither efficient nor secure and that it is only suitable if both machines are connected to the same internal, private network.
i'm not going to be doing this over a private network.

---

### Post by chavo on 2006-08-12
Yeah then this is going to be pretty iffy. You can try something like this ->

dd if=/dev/hda | ssh -c'blowfish' user@host 'dd of=/path/to/hda.iso'

Now this may or may not work depending on your machine.

Have you considered rsync?

---

### Post by dmizer on 2006-08-12
> **chavo said:**
> 'blowfish'

lol ... not sure how that fits in?  am i missing something?

hadn't considered rsync.  have some ideas about that?

---

### Post by jinglespur on 2006-08-12
You could try sshfs:

[http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)

(You'll need to apt-get it, and add your username to the newly created 'fuse' group.)  Mount the folder from the remote system on your local host, then dd to it:

mkdir Mountpoint
sshfs root@targetip:/file/save/ Mountpoint/
dd if=/dev/hda of='Mountpoint/path.iso'

Hope this helps.

---

### Post by dmizer on 2006-08-13
looks like fuse would have worked, but i screwed up and installed it on the wrong machine.

anyway here's what ultimately ended up working:
```
dd if=/dev/hda | gzip -c | ssh root@host 'dd of=/path/to/file.img' bs=2048
```

---

