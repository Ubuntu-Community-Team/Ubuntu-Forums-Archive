---
title: "loose creation date when copying files"
date: 2008-06-08
forum: Desktop Environments
---

### Post by RamonV on 2008-06-08
My God! How can this have happened?

Creation date is an important metadata of files. Copying has nothing to do with creation. It may be a backup, a directory reorganization, anything!

Please CORRECT this immediately. I'm about to return to "W".

The problem was with NTFS and now it has spread, instead of resolving it.

Le sens commun n'est pas si commun. Voltaire.

---

### Post by soxs on 2008-06-08
Which date do you refer to, how do you obtain it. When i copy files, the last edited and last access gets updated.

---

### Post by RamonV on 2008-06-08
> **soxs said:**
> Which date do you refer to, how do you obtain it. When i copy files, the last edited and last access gets updated.
Last update date/time is changed when you copy a file with copy/paste or drag&drop in nautilus (hardy). Or CP by the way.
To copy a file is NOT an update!
When you copy a directory all the "last update date/time" of the files contained are set to the date/time of the copy !!

---

### Post by kaibob on 2008-06-08
> **soxs said:**
> Which date do you refer to, how do you obtain it. When i copy files, the last edited and last access gets updated.

The cp command has a preserve timestamp option that will do what you want. Have a look at the cp manual page for specifics or ask and I will provide further detail. You could make this permanent with an alias in your bashrc file. Unfortunately, I don't know how to do the same thing with Nautilus; perhaps someone else will have an idea.

BTW, I assume we are talking about the date/time shown by Nautilus in the "Date Modified" column and the date time shown in a terminal window with the ls -l command.

---

### Post by louieb on 2008-06-08
cp has the -p option. this is from [B]man cp
[/B]```

       -p     same as --preserve=mode,ownership,timestamps

       --preserve[=ATTR_LIST]
              preserve   the   specified   attributes   (default:  mode,owner&#8208;
              ship,timestamps), if possible  additional  attributes:  context,
              links, all



```
:)beaten to it

---

### Post by kaibob on 2008-06-08
> **kaibob said:**
> ...Unfortunately, I don't know how to do the same thing with Nautilus; perhaps someone else will have an idea....


The following is a bug report entitled "Nautilus not preserving timestamps":

[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/215499](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/215499)

And, here is a spirited discussion as to whether or not Nautilus should preserve timestamps:

[http://bugzilla.gnome.org/show_bug.cgi?id=515777](http://bugzilla.gnome.org/show_bug.cgi?id=515777)

The not-unanimous opinion is that the timestamp should be preserved. Anyway, this whole issue is being discussed.

---

### Post by lonetree on 2008-06-12
I face the same problem here, this problem used to happen few years back when I was using 5.04. In 6.06 I managed to edit the /etc/fstab with the gid and uid values and it copied the file well, date and time copied over from source to target remain the same except folder, which the date of creation gets updated to the date and time of copy.

Now, this was good until 7.10. In 8.04, this starts to happen again and editing gid and uid in fstab didn't help too. 

Was wondering why this happen again and again, isn't this 8.04 supposed to be a much improved version? I wonder if ubuntu developer found out about this.

I am going to try out other distro, maybe fc, and see if this happen too.

---
4 hours later
----

I downloaded kubuntu 8.04, test copy files and folder from target to source and the reverse way, timestamp remain as it is. 

I hope some one can do something to this soon. I like gnome over kde.

---

