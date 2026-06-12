---
title: "HOWTO: Security and easy backup for documents and e-mail"
date: 2007-03-05
forum: Desktop Environments
---

### Post by tbraun on 2007-03-05
Hello!

This is a bit longer, but most of it is just explanatory text, so
don't despair...

As a long-time user of laptops, I have always strived to find
ways to reliably backup my data and also secure it against
unauthorized access. Both are important, considering that
laptops are popular targets of theft. However, this does not
only apply to laptops: Every user can benefit from securing
the personal data on their machine. Consider having to hand
over the machine for maintenance, or any other reason - 
legitimate or not - of someone else having access to your 
machine.

This HowTo describes how I have set this up for myself. It is
of course possible to modify this kind of setup to your liking.
Towards the end I am discussing some of the issues that users
of the Evolution e-mail client will face, and how they can be
overcome. The first sections, however, are independent of the
chosen e-mail client or desktop. 

**_Encrypted container files_**

Obviously, a key element of protecting your data is encryption.
There are two popular ways of doing it: Either an entire
partition of your hard drive is encrypted, or you create a
'virtual' partition inside of an encrypted container file.
The container is a single, large file that resides in your
normal, unencrypted file system. However, it contains all of
the data of an entire file system itself. With the right software
it can be mounted to any chosen mount point in your system.
All accesses to/from the file-system in the container file are
encrypted/decrypted on the fly, completely transparently.
You need to provide a password when you mount it, but after
that, you access it like any other partition. To secure your
data again, simply unmount the partition. The mount point will
be 'empty', and all you are left with is that container file,
filled with random-looking data.

I have always preferred the encrypted container file, simply
because it provides unsurpassed ease and comfort when backing
up all your data: I plug in my USB drive, and simply drag-and-drop
a single file from my hard drive to the USB drive. All the data
will be safely stored on the USB drive, and will also be
encrypted.

**_Truecrypt_**

There are a number of utilities out there, which know how to
deal with encrypted disk data. Truecrypt is a popular open
source choice for Linux. It now seems to be in the repositories,
which makes installation easy:

```

    sudo apt-get install truecrypt

```

You can also get a .deb file from the Truecrypt web-site
at [http://www.truecrypt.org]("http://www.truecrypt.org").

First you need to create the encrypted container file. This
is done via the command line. A number of options exists.
However, to create a 100 MByte container, you do this:

```

    # truecrypt -c

```

Truecrypt will now ask you interactively for a number of
parameters. The first question is for the volume type. For
more information on this you can look through the documentation
on the Truecrypt web-site. For starters, you can just choose
[1] 'Normal' here.

Next, it will ask you for a filename for the new volume, and
you may specify whatever you like. Let's say we call it
'testvolume.tru'.

Now it will ask you for the filesystem, and it offers 'FAT'
or 'None'. Choose [2] 'None'.

You can now set the volume size. In our case we specify
'100M'.

For the hash and encryption algorithms, just accept the defaults
that are offered ('RIPEMD-160' and 'AES'). But you may choose
whichever combination you like. The Truecrypt web-site has a
good discussion about the different algorithms.

Finally, a password for the new volume is requested. Choose
something a bit longer and none trivial. Think 'pass phrase',
rather than password.

For the keyfile-path, simply accept the default [none].

Before starting to create the volume, Truecrypt requires some
random data, which it can get via the keyboard or mouse. Simply
follow the instructions displayed on the screen. Once it has
all the data it needs, Truecrypt starts to create the new
volume. For larger ones, this can take a few minutes.

If everything went fine, Truecrypt will conclude with the
message: 'Volume created'.

You now have an empty encrypted container file, ready to
house a file system. However, before you can use it to store
any data, you actually have to format it like any normal
disk drive.

If we choose ext2 as file system, then this is done like
this:

```

    # truecrypt -N0 testvolume.tru
    # mkfs.ext2 /dev/mapper/truecrypt0
    # truecrypt -d testvolume.tru

```

Of course, you may have to change 'testvolume.tru' to whatever
name you have chosen for the container file. What happens here
is that the container file is mounted as a block device, which
can then be worked on by the mkfs utility as usual. Once that
is done, the container file's block device is unmounted again.

Finally, you can mount your new encrypted partition to the
mount point of your choice. I have an empty directory called
'SECURE' in my home directory. So, to mount it, I say:

```

    sudo truecrypt --filesystem ext2 --mount-options "sync,rw" ~/testvolume.tru ~/SECURE
    sudo chown tombraun:tombraun ~/SECURE

```

The second line is required to give me all the needed read and
write access to the mounted file. There is probably a more
systematic way to do it, but it works. I place those two lines
into a script, which allows me to easily execute these
instructions with just a single command.

To unmount the encrypted volume again, I type:

```

    sync
    sudo truecrypt -d ~/SECURE

```

Again, I place those instructions into a small script, so that
this can be executed with just a single command.

Note that Truecrypt will not allow you to unmount the partition
if there are still files in use. This forces you to first shut
down the usual applications you work with correctly, and prevents
any possible data corruption.

Now that you have an encrypted volume ready for your use, it is
time to arrange your personal data so that it is really stored
there.


_**Securing your data**_

Before we start with this it would be a good idea for you to make
a traditional backup of all your important data! Please, only
proceed once you have done this. A small typo, and it could all
be gone...

Now, assume you have the encrypted volume mounted under the
'~/SECURE' directory and you are now ready to secure your data.

To keep things simple, it is often easiest to move all your
relevant folders into the encrypted volume and create soft links
from their original location to the new location. For example,
to move all your Evolution files (e-mails, address books,
calendar, etc.) into the encrypted partition, you can do this:

```

    cp -a ~/.evolution ~/SECURE/evolution
    mv .evolution evolution_old
    ln -s ~/SECURE/evolution .evolution

```

Then you start Evolution and see if you still get access to all
your e-mails, addresses and calendar entries. Once that check
succeeds, you can erase the old e-mail folder:

```

    rm -rf evolution_old

```

All of this can be accomplished with less instructions, but I
like to be on the safe side and first test if the copy to the
encrypted partition works correctly and I can still start my
applications.

For other e-mail clients, you just need to move their respective
directories in the same way. I also do the same for my .gaim
directory, as well as for my work and document directories.

Once you have done this, you will find that you will not be able
to start your applications, or at least won't get access to any
useful data, if you have not first mounted the encrypted volume.
This, of course, is exactly what you want. As a laptop user, just
make sure you unmount it before hibernate or suspend your laptop
for transport. If it should get snatched from you in the airport,
the thieve at least won't be able to get to your data.


**_Backing up your data_**

The backup of your important data can now be accomplished with
a single drag-and-drop or copy command. Plug in your backup
media, for example a USB drive, and just copy the testvolume.tru
file over. That's all!

I would recommend un-mounting the volume first, though, to prevent
any possible data corruption in the backup.

The ease with which you can backup your data is one of the biggest
advantages of this method:

[LIST=1]
[*]It's so easy, you don't mind doing it more often.
[*]The backup itself is also encrypted.
[*]Restore is easy as well: A single copy operation.
[/LIST]

Note that I use a 2 GByte encrypted volume. It is backed up to
my USB drive in around 6 minutes, giving me time to read the
news or get a coffee. Sure, it's not an incremental backup, but
making a complete backup is quick and easy.

**_A few issues with Evolution_**

Evolution e-mail is tightly integrated with the Gnome desktop,
which can cause problems. In particular, just closing the
Evolution window will not shut down all the processes related
to Evolution. For example, the alarm-notification will remain
running. The best way to shut all of Evolution down is to use:

```

    evolution --force-shutdown

```

However, under Gnome, the clock applet is integrated with the
Evolution calendar. Thus, a few moments after you issue this
command, some of Evolution's background processes will magically
have started up again. Unfortunately, the alarm notification is
now all confused, if you have unmounted the encrypted volume in
the meantime. This strange behavior for a while has left me with
missed appointments. I finally found a solution, however.

Maybe there is a simpler way to do this, but the script I use
to unmount the encrypted volume now looks like this:

```

    sync
    sudo chmod ugo-x /usr/lib/evolution/2.8/evolution-exchange-storage /usr/lib/evolution/2.8/evolution-alarm-notify /usr/lib/evolution/evolution-data-server-1.8
    sync
    evolution --force-shutdown
    killall gnome-panel
    sleep 1
    sync
    truecrypt -d ~/SECURE

```

This does the following:

[LIST=1]
[*]It makes all the evolution components non-executable, which prevents an automatic restart.
[*]It then shuts down all the Evolution components.
[*]It finally kills the gnome-panel, which includes the clock applet. The panel will briefly disappear and then reappear again. No harm done. The clock applet cannot force a restart of the evolution components anymore, since they are not executable.
[*]Finally, it unmounts the encrypted volume.
[/LIST]

To mount my encrypted volume again, my script looks like
this:

```

    sudo truecrypt --filesystem ext2 --mount-options "sync,rw" ~/testvolume.tru ~/SECURE
    sudo chown tombraun:tombraun ~/SECURE
    sudo chmod ugo+x /usr/lib/evolution/2.8/evolution-exchange-storage /usr/lib/evolution/2.8/evolution-alarm-notify /usr/lib/evolution/evolution-data-server-1.8
    killall gnome-panel

```

This makes the various Evolution components executable again,
and also restarts the clock applet (by restarting the gnome-panel).
This allows the clock applet to integrate with the data of the
Evolution calendar, a feature all Gnome/Evolution users enjoy.


**_In closing_**

I hope all of this was of help to you. If you have any comments
or feedback, or if you know of better ways to do some of those
funky things with the clock applet, please let me know.

Tom

---

### Post by tbraun on 2007-03-07
So far, no comments on this, interestingly. I would like to hear from others
how they are securing and backing up their vital data...

Tom

---

### Post by NIT006.5 on 2007-07-09
Hi Tom,

Thanks for this post. Have tried it out and it is now working well for me.

However, I am having a few problems with formatting the container file as ext2/ext3. I eventually got it working on my PC, but it kept freezing my PC when I ran mkfs.ext2 or mkfs.ext3. It would get to "Writing inode tables" and would freeze at a different point every time. I initially tried with a 40Gb container file, then tried with 20Gb. Even on 20Gb it froze quite a few times (requiring a hard reboot) and eventually it went through to the end.

I am now trying the same thing for one of my other users, this time with a 10Gb container file (and completely different hardware), and it's doing the same thing. On the fifth attempt (and reboot) it managed to get past the writing of inode tables, and then froze on "Writing superblocks and file system accounting information". On the following try, it froze again on inode tables.

Each time it has a problem, it freezes absolutely everything, including the mouse pointer. Sometimes the mouse pointer disappears altogether. Since it seems to freeze at a different point in the process every time, I'm quite baffled by this. I did think that maybe I just wasn't giving it enough time to run, but then surely if it was still busy, it wouldn't cause the PC to become non-responsive? Also, for a little while after the "freeze" I sometimes see hard drive activity, but eventually that seems to stop too. Could it be the "size" of the container file that is causing the problem? The reason I'm using large container files is because we want to use them to store other sensitive documents as well as evolution mail. And if the size is a problem, then why did it eventually succeed on my PC with a 20Gb container?

I plan on repeating this setup for a number of "senior" users who require encryption, so if you (or anyone else) have any ideas on this it would be greatly appreciated.

---

### Post by tbraun on 2007-07-09
> **NIT006.5 said:**
> 
However, I am having a few problems with formatting the container file as ext2/ext3. I eventually got it working on my PC, but it kept freezing my PC when I ran mkfs.ext2 or mkfs.ext3. It would get to "Writing inode tables" and would freeze at a different point every time. I initially tried with a 40Gb container file, then tried with 20Gb. Even on 20Gb it froze quite a few times (requiring a hard reboot) and eventually it went through to the end.


This is very strange. I have never had that problem before. You are right, maybe this is because of the
size of the container files. I am usually creating 2 or 4 GB sized containers, the largest one being 12 GB.

Also, I found that having a few individual container files has advantages: You can back up the portions
of your systems that have changed more easily and quickly. For example, I have one larger one for photos,
and a somewhat smaller one for e-mail and documents. The latter one changes much more often, therefore,
I usually only need to back it up, which is much faster due to its smaller size.

At any rate, the system should not hang, but I do not know what the cause of the problem is.

One last tip: Since you managed to create the 20 GByte container now, you can just take it and copy
it to other computers, and even give it to other people, as long as you haven't stored sensitive data in
it (if you have, you might want to wipe that data). This is possible, because once you changed the
password, it's not accessible to you anymore, and they won't know how to access your copy of it
either. That might save you from having to go through the container creation trouble more than once.

Tom

---

### Post by NIT006.5 on 2007-07-10
Hi again,

Thanks for the reply. Yes, I did consider copying the container file but the user I'm setting it up for now has no need for a 20Gb one. I might just have to do that though. It's just frustrating that I can't figure out what the problem is (unless I'm doing something stupid somewhere). Will have another look and go through it again, step by step, when I have time again. Unfortunately I'm travelling for the next few days, so it'll have to wait. 

Also, while I might consider multiple container files for myself, most of the users I'm setting up are pretty "fresh" off Windows and they are not very "advanced" users, so I need to make things as simple and as automatic as possible - for that reason, I'm hesitant to try them with multiple containers because I fear they will tie themselves in knots - one encrypted container file is probably about as much as they can handle at this point.

Anyway, gotta hit the road. Thanks for the help.

---

