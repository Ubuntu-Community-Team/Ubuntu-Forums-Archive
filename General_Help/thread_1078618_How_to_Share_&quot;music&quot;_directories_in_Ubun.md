---
title: "How to Share &quot;music&quot; directories in Ubuntu betwen users?"
date: 2009-02-23
forum: General Help
---

### Post by linuxaz on 2009-02-23
Hello,
I have finished setting up a home desktop machine for a friend of mine using Ubuntu 8.10.  The machine has three users total, one adult, two teens.

I have restricted the teens to have no administrator authority, but they would like to view each others pictures, and music if required, without having to log in as another user, or switch users between open sessions.

What would be the easiest way to set that up?

Allowing rw access to those directories would be OK in this case.

Thanks,

linuxaz

---

### Post by mb_webguy on 2009-02-23
Well, you could give those directories rx (*not* rw) permissions for others.  Of course, this would mean that they'd need to be able to see the contents of the user's home directory as well.

Or, if you want a universal Music directory, create a music directory somewhere that has read/write/execute permissions for others, and change the Music directory in each user's home directory to a symlink to this directory.

---

### Post by trash.eighty on 2009-02-23
> **mb_webguy said:**
> Or, if you want a universal Music directory, create a music directory somewhere that has read/write/execute permissions for others, and change the Music directory in each user's home directory to a symlink to this directory.

Probably the best way to do this.  If you need a hint on the bash-fu;
```
mkdir /usr/music
chmod -R 666 /usr/music
ln -s /usr/music /home/user1/Music
ln -s /usr/music /home/user2/Music
```
This makes a directory /usr/music*, changes the permissions to be read/write by everyone, and creates a symbolic link to /usr/music in each user's ~ folder.

*Forgive me if /usr isn't the proper place to put that

---

### Post by HermanAB on 2009-02-23
The easiest way to share MP3s is to use Edna:
[http://aeronetworks.ca/ogg2mp3-howto.html](http://aeronetworks.ca/ogg2mp3-howto.html)
[http://edna.sourceforge.net/](http://edna.sourceforge.net/)

It works like a charm!

Cheers,

Herman

---

### Post by linuxaz on 2009-02-24
Thanks to all.

I will give these a try.

---

### Post by vanadium on 2009-02-24
[quote=trash.eighProbably the best way to do this. If you need a hint on the bash-fu;ty
[/quote]
You will not be able to navigate directories if you disable the execute bit. You will need permissions 777.

This is a rather insecure approach. However, this won't matter probably in a home environment.

The more secure approach would be make all users member of a common group, e.g. "music". Then chown the group of the music files and directories to that common group "music". At that point, you can set permissions for "the rest of the world" (others) more restrictive, e.g. 775 (read-only for others). Only the "priviledged" users that belong to the music group, have read/write access the music, others can not make changes.

---

