---
title: "How do I install non apt-get games correctly?"
date: 2005-04-17
forum: Gaming &amp; Leisure
---

### Post by fipeso on 2005-04-17
Im new to Linux and Ubuntu.

I do not want to mess up the Ubuntu installation, by doing things the wrong way, so I like to ask some basic questions.

If I want to install a game that is not in apt-get, I have to down load it from the games web page.

1) Does it mater where I download the tar files? 
2) Should I unpack the tar file somwhere else than home dir?
    Some games seems to install the game, where I unpacked the tar file.
3) Should I unpack the files in CLI or GUI?
4) What shall I do as "root" and what as "looser user"
5) What is the correct place where games should end up, not home dir I guess?
6) Can one just move a game dir from one dir to an other, there is no "registry" as in windows that gets messed up?
7) Is there a risk, as in Windows, that system files get over writen?
    Guess if I do most of the installation as normal user, the system cant be destroyed?

Any other suggestions one should think off ?

---

### Post by nautilus on 2005-04-17
A very good question!

It's rare a new user thinks of keeping their filesystem tidy, and later on (like me) end up either wiping the disc clean and trying again, or spending the hours(days) cleaning it all up ;)

**1) Does it mater where I download the tar files? **
I highly suggest you have a downloads directory in your home directory.  I personally sort those by catagory: ~/downloads/gaming/open/ <- open source games

** 2) Should I unpack the tar file somwhere else than home dir?**
This is a tough one... Some might suggest this, it's what I do personally, but now that you mention it, it may make sense to create a directory somewhere safe and perm:

/usr/local/share/games/turkeypuncher3

for instance... and then put the 'untared' contents in the source/ directory, for safe keeping.

* Some games seems to install the game, where I unpacked the tar file.*

Evil games :(  Move them.

** 3) Should I unpack the files in CLI or GUI?**
I think this is a matter of preference.  I alternate, although doing it using GUI is somewhat new to me, but KDE's integration is improving so quickly, in some cases it's just more convenient :)

** 4) What shall I do as "root" and what as "looser user"**
Do it all as a normal user if possible, except the actual installation (which may be as simple as moving the directory in some cases)

** 5) What is the correct place where games should end up, not home dir I guess?**
No, never!

Ubuntu stores, in the spirit of Debian, all the 'non-DEB' stuff, user-installed stuff, in /usr/local instead of /usr, so they should end up somewhere in there.  Probably /usr/local/games, and that's where most commercial games (enemy territory, neverwinter nights, etc) seem to like to install to.

** 6) Can one just move a game dir from one dir to an other, there is no "registry" as in windows that gets messed up?**
There isn't really a registry, but some games don't take this sort of thing very nicely at all (such as Unreal Tournament 2004).  Sometimes, you have to reinstall (if it has an installer), and for many open source games (which integrate themselves all over your filesystem sometimes) you have to recompile them entirely.

** 7) Is there a risk, as in Windows, that system files get over writen?**
Well.... A slim-ish one, because nobody but you is controlling what's happening, whoever made the archive or makefile might have had a bad day at the post office, and feel like ruining somebody's Linux system... It **could** happen, but only if it was intentional, pretty much.

** Guess if I do most of the installation as normal user, the system cant be destroyed?**

this would suggest you only install somewhere your user has permission to, such as /home/*you*, which really is the safest way to do **anything**.  also, this severely limits your ability to break the system in any way, like you suspected, to be practically impossible.  the only downside is, well, it'll all be crammed in your home directory :P

and finally, if a game you downloaded requires extras, libraries and such: Whenever possible, use the ones available in the Ubuntu repositories.  maintaining libraries from source is a severe chore, and sometimes they can collide with Ubuntu provided libraries in bad ways.

---

### Post by fipeso on 2005-04-17
Thank You for your anwser :)

Well I'm now downloading Americ's Army and will try to install it in a few hours.
(744MB down load  :-? )

---

