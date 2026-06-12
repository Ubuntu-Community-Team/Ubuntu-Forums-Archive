---
title: "Local shared directory"
date: 2006-08-08
forum: Desktop Environments
---

### Post by neveceral on 2006-08-08
Hi, i have ubuntu 6.06 on my home PC with 3 users and, as a really newbie, i would like to create a local shared directory „pub“, for sharing movies, songs etc. with other 2 users. All users should have a permission for creating, deleting and writing all files and subdirectories of „pub“. How to do it (i prefer GUI settings J ), and  where i should create a „pub“ directory according to linux conventions?
I read this [http://ubuntuforums.org/showthread.php?t=208753](http://ubuntuforums.org/showthread.php?t=208753) but there is no answer, how to do it for subfolders.

---

### Post by simonn on 2006-08-08
I put my public folder it in /var.

I created a group and user called public and made public:public the owner of the public folder. I added all users who needed access to the pub folder a member of the public group.

```

$sudo groupadd public
$sudo useradd -g public public
$sudo mkdir /var/pub
$sudo chown public:public /var/pub
$sudo chmod 770 /var/pub

```

Now add the users using the GUI tools.

---

### Post by scxtt on 2006-08-08
simonn's right, but i don't see the need for the public user:group, unless you're trying to restrict some users and allow others ... just do:

sudo mkdir /var/pub
chmod 777 /var/pub

you can put it where ever you want /pub, /var/pub, /opt/pub, /public -- anywhere, since it's highly unlikely that any program will make use of it ... the only real way it'd matter is if you've separated out your /home, /var, /tmp, etc. folders and don't have the space on your root partition ...

---

### Post by simonn on 2006-08-08
> **scxtt said:**
> i don't see the need for the public user:group, unless you're trying to restrict some users and allow others ...

You answered your own question.

Security.

Why do we not browse t'interweb as root?

The less places that anyone can write to the better.

> **scxtt said:**
> you can put it where ever you want /pub, /var/pub, /opt/pub, /public -- anywhere, since it's highly unlikely that any program will make use of it ... 

You can however, the [FHS](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) implies that files that may change in length a lot (configuration files do not count because they should not change much, if at all, in a production system) should be under /tmp, /var or /home. This is why most applications will use these to save data, logs and temporary files and only badly designed ones write to other areas of the file system.

This allows a lot of the file system to be mounted read only most of the time.

> the only real way it'd matter is if you've separated out your /home, /var, /tmp, etc. folders and don't have the space on your root partition ...

/var/public is a mount point on my system :).

---

### Post by scxtt on 2006-08-08
> **simonn said:**
> You answered your own question.

Security.

Why do we not browse t'interweb as root?

The less places that anyone can write to the better.i didn't ask a question, so i couldn't have answered it ...

i don't think it's *wrong* to have a public:public user / group (tho you'd most likely only need the public group) - but this is for someone who is apparently just sharing 1 folder w/ (most likely) everyone else that uses the box, which is why i said "unless you're trying to restrict some users and allow others" ...

---

### Post by neveceral on 2006-08-08
> **simonn said:**
> 
```

$sudo groupadd public
$sudo useradd -g public public
$sudo mkdir /var/pub
$sudo chown public:public /var/pub
$sudo chmod 770 /var/pub

```


Thank you very much, but i read in our Czech forum, that there is a problem with writing and deleting permissions for new created subfolders of public folder, so that i have permission only for reading and not for deleting or rewriting subfolders and files in them, that the subfolders don't have 770 but only 600.

---

### Post by simonn on 2006-08-08
> **neveceral said:**
> subfolders don't have 770 but only 600.

That is a bug with nautilus.

You could set up a cron job to change the permissions.

---

### Post by scxtt on 2006-08-08
using sudo would easily make that a non-issue ...

---

### Post by simonn on 2006-08-08
> **scxtt said:**
> using sudo would easily make that a non-issue ...

How?

---

### Post by scxtt on 2006-08-08
the OP can do anything to any folder if they can use sudo (and the 1st account is sudo-enabled) ... i'm assuming the OP is basically the admin of this box ...

---

### Post by simonn on 2006-08-08
OP = user a. There are also users b and c.

a goes away on holiday.

b and c cannot see each others files until a returns.

---

### Post by scxtt on 2006-08-08
sure they can see them, they just can't move/delete files/dirs created by their counterparts ...

i'm sure 99% of file managers do 644 for files and 755 for directories when created, and i'm betting that default behavior can be changed ...

so if b and c play nice ("hey b, will you delete large_file_owned_by_b.mpg?") - they'll be fine until a gets back ...

---

### Post by simonn on 2006-08-08
[http://bugzilla.gnome.org/show_bug.cgi?id=327249](http://bugzilla.gnome.org/show_bug.cgi?id=327249)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=314796](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=314796)

---

### Post by scxtt on 2006-08-08
i've never seen the 600 problem and i'd been using Gnome for about 2 years straight til i switched to KDE (again, used it for ~4 years in my RH/Fedora days) about a week ago (and i get 755 / 644 anytime i create dirs / files), actually i'da preferred 600 since i generally switched everything to 600 or 700 anyways ... i don't have it installed ATM, so i can't confirm or deny that it's a problem ...

---

### Post by neveceral on 2006-08-08
i mean, that *the sharing problem* is, that the new subfolder automatically don&#8217;t inherit (?) the permissions form parent folder. How to do it?

---

### Post by scxtt on 2006-08-08
at worst, whenever someone creates a folder they'll just have to set the permissions ... something tells me using umask will solve that problem ...

check out: [http://unixhelp.ed.ac.uk/examples/umask.html](http://unixhelp.ed.ac.uk/examples/umask.html)

---

### Post by simonn on 2006-08-08
> **scxtt said:**
> i've never seen the 600 problem and i'd been using Gnome for about 2 years straight til i switched to KDE (again, used it for ~4 years in my RH/Fedora days) about a week ago (and i get 755 / 644 anytime i create dirs / files), actually i'da preferred 600 since i generally switched everything to 600 or 700 anyways ... i don't have it installed ATM, so i can't confirm or deny that it's a problem ...

Good for you!

> **neveceral said:**
> i mean, that *the sharing problem* is, that the new subfolder automatically don’t inherit (?) the permissions form parent folder. How to do it?

Things do not work like that in linux. 

In linux you set a umask which defines which permissions a file created by a user will NOT have. Usually this is 022, so files are created with 644 permissions (see [http://rute.2038bug.com/node17.html.gz#SECTION001720000000000000000)](http://rute.2038bug.com/node17.html.gz#SECTION001720000000000000000)).

Nautilus (the default Ubuntu file manager) ignores the umask setting and creates the files with 600 and ownded by the user creating them, in other words they cannot be written or read by other users. This is a bug.

I assume folders created with nautilus are 700? (sorry I do not have access to a GUI session at present).

So, realistically, either create or copy files with the command line (probably not what you want) or create a cron job which sets the permissions to 640 for files and 750 for directories under the pub tree on a regular basis - how viable this is would depend on how many files there are going to be under it.

Try the following as cron job:

chown -R public:public /var/pub/*
find /var/pub -not -type d -printf "chmod 640 \"%P\"\n" | sh
find /var/pub -type d -printf "chmod 750 \"%P\"\n" | sh

Not ideal, but the best I can come up with.

---

### Post by simonn on 2006-08-08
> **scxtt said:**
> at worst, whenever someone creates a folder they'll just have to set the permissions ... something tells me using umask will solve that problem ...

Nautilus ignores umask.

---

### Post by neveceral on 2006-08-08
Someone from czech forum tried it with usmask, but he wrote, that there was a permission problem by moving files to and from pub folder :-/ So i feel, that in this case is ubuntu very unfriendly. In Mandriva exists GUI for this settings and it works very well.

---

### Post by scxtt on 2006-08-08
> **simonn said:**
> Nautilus ignores umask.even if it does, the user can right-click on anything they create and change the permissions for any file from the "permissions" tab ... the shell heeds any umask i set, but i can't seem to create files (just directories) from nautilus using this SUSE 10.1 Live CD ... so some thinking will be involved to allow a,b,c users to have complete control over any file in /var/pub, but no one ever died from having to think ...

---

### Post by simonn on 2006-08-08
> **scxtt said:**
>  no one ever died from having to think ...

But, many people have died from other people not thinking, or forgetting.

---

### Post by scxtt on 2006-08-08
[quote=simonn]But, many people have died from other people not thinking, or forgetting.[/quote]being a bit dramatic?

i think worst-case scenario, once the /var/pub folder is created and users start making dirs/files in it, at worst, other users can't delete these things {w/o the user who created them paying a little more attn.} that don't belong to them - and how is that really a big deal? - i doubt we're dealing w/ any malicious users here ...

---

### Post by simonn on 2006-08-08
> **neveceral said:**
> Someone from czech forum tried it with usmask, but he wrote, that there was a permission problem by moving files to and from pub folder :-/ So i feel, that in this case is ubuntu very unfriendly. In Mandriva exists GUI for this settings and it works very well.

Nautilus creates files with 600 permissions and folders with 755. files copied to it will keep their existing permissions.

So if you follow my example creating a public directory, i.e. [http://ubuntuforums.org/showpost.php?p=1352748&postcount=2](http://ubuntuforums.org/showpost.php?p=1352748&postcount=2), the only worries you will have are as scxtt pointed out above.

Users will have to learn about permissions, which is not such a bad thing.

---

### Post by scxtt on 2006-08-08
konqueror also ignores any bash umask settings, so i'm wondering if it's the fact that it's bash-specific (hence it ALWAYS working in the shell) or an actual bug ... i'm guessing the devs of both nautilus/konqueror purposefully do it that way ...

looks like a cron is your best bet ...

---

### Post by neveceral on 2006-08-08
i saw the cron script, but it is a little bit unsophisticated - sometimes i will have to wait for rewriting permissions and it consumes computer performance.
I know, it is solution (thank you for it), but i hope, that someone knows better solution :-)

---

### Post by John RG on 2008-02-24
Thanks Simonn, as a newbie I found your original posting helpful & it worked!  Bonus :-)

It's surprisingly tricky to find a posting which describes how to do this. One more hurdle for Windoze refugees.

Ta,

John

---

