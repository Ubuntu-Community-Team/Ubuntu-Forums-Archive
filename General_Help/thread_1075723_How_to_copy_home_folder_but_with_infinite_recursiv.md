---
title: "How to copy home folder but with infinite recursive symbolic links in .wine"
date: 2009-02-20
forum: General Help
---

### Post by desconocido on 2009-02-20
I'm trying to copy the whole of my home folder (to burn:/// so that I can do a back up). But my version of .wine has infinite recursive symbolic links so the copy gets messed up or never ends.

Is there a simple way of specifying a copy of all of a folder and its sub-folders EXCEPT for one sub-folder? I would like to be able to do this fairly easily. A unix command would be fine.

By the way, what do people use more: Brasero or the Nautilus Go to CD DVD Creator? ANd do I need to worry about DVD + or - RW in Ubuntu?

Regards

---

### Post by Slim Odds on 2009-02-20
Why don't you just go find the link and delete it?

---

### Post by geirha on 2009-02-20
.wine has infinite recursion because z: is a symbolic link to / by default. I'm a bit surprised that natuilus actually follows symbolic links when copying to burn://. I would not expect that. Try with brasero and see if that, as well, follows symbolic links.

---

### Post by desconocido on 2009-03-02
> **Slim Odds said:**
> Why don't you just go find the link and delete it?

Yeees, but I'm not sure whether the link is doing anything essential.

---

### Post by desconocido on 2009-03-02
> **geirha said:**
> .wine has infinite recursion because z: is a symbolic link to / by default. I'm a bit surprised that natuilus actually follows symbolic links when copying to burn://. I would not expect that. Try with brasero and see if that, as well, follows symbolic links.

The recursive symbolic links are inside z:/sys/devices/platform/pcspkr
(See the attached screenshot)

I tried brasero first and I imagine I had a similar problem because it never finished trying to create the Data Project.

Do you think I could just delete the pcspkr directory?

Useful would be an option on the cp command to omit a particular directory when doing a copy.

I suppose I could write a script to make .wine unreadable; do the copy; and then restore the permissions on .wine, but that means finding the storage box that has my Unix manuals in it.

---

### Post by geirha on 2009-03-02
It's safe to remove the symlink. ```
rm ~/.wine/dosdevices/z:
``` Do not remove anything outside your homedir. 

After you've copied it back, you can recreate it just as easily with
```
ln -s / ~/.wine/dosdevices/z:
```
or by running "winecfg" and recreate it in the drives tab.

Another option is to use genisoimage, which does not follow symlinks by default, to create an iso-image, but it is a command-line application
```
genisofs -r -o /path/to/store/iso/home.iso $HOME
```
If you also want the resulting CD/DVD to be readable from windows, add the -J option to get the joliet extension as well.

---

### Post by desconocido on 2009-03-05
> **geirha said:**
> It's safe to remove the symlink. ```
rm ~/.wine/dosdevices/z:
``` Do not remove anything outside your homedir. 

After you've copied it back, you can recreate it just as easily with
```
ln -s / ~/.wine/dosdevices/z:
```

I tried that:
```
bob@faustino:~/.wine/dosdevices$ rm ~/.wine/dosdevices/z:
bob@faustino:~/.wine/dosdevices$ cp -a $HOME burn:///
cp: cannot stat `/home/bob/.dbus/session-bus': Permission denied
cp: cannot copy a directory, `/home/bob', into itself, `burn:///'

```

but it turned out I was just creating a directory called "burn:" in the current directory. Obviously the nautilus syntax for burn:/// wasn't recognised by the shell.

So I went back to nautilus and copied this new "burn:" folder to burn:///.
That worked except for one thing. All my files were OK but all the folders lost their dates and permissions, which is not what I need in a backup.

I couldn't find anything useful in Google or Ubuntu Forums (except that there seems to be a plan to remove this feature in future versions of Ubuntu).

Anyone know where burn:/// actually is in the file system?

Or should I have a go with Brasero?

---

### Post by desconocido on 2009-03-06
I tried Brasero. Ha.
See [http://ubuntuforums.org/showthread.php?p=6850270#post6850270](http://ubuntuforums.org/showthread.php?p=6850270#post6850270)

---

### Post by desconocido on 2009-03-09
Final approach is:

```
rm ~/.wine/dosdevices/z:
tar -cvvz --totals --ignore-failed-read -f  /home/somewherethatisnotbob/bob.tar.gz /home/bob
ln -s / ~/.wine/dosdevices/z:
```

Then use Brasero to burn /home/somewherethatisnotbob/bob.tar.gz.

I'm happy with this. Thanks everyone for the help.

---

### Post by Yleeyas on 2009-07-15
Thanx for the info geirha. I've got a similiar symbolic link problem with CrossOver Office V8. I resorted to selective backups, but this option helps.

thanx again

---

### Post by jerome1232 on 2009-07-15
I believe cd's filesystems do not support unix style file permissions. So if you wanted to preserve said file permissions you would have to tar up the files you wish to backup and burn the archive to cd.

---

