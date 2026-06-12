---
title: "[Breezy] Cannot Edit KDE Menu"
date: 2005-11-26
forum: Desktop Environments
---

### Post by carney1979 on 2005-11-26
I have the full Kubuntu desktop installed.

If I make a change to the KDE menu using the built-in KDE menu editor, the changes are not recognized.

So, how does one change/add/delete items from the KDE menu?

David

---

### Post by gingermark on 2005-11-26
Are you clicking the save icon after making your changes? Don't wanna sound insulting, it's just that's all I could think it might be.

If you have, do you then get an "Updating System Configuration" dialog box?

---

### Post by GeneralZod on 2005-11-26
What you're doing should be fine (as long as, as Gingermark says, you are clicking "Save" afterwards :))

It seems you're not the only one:

[http://ubuntuforums.org/showthread.php?t=93616&highlight=kmenuedit](http://ubuntuforums.org/showthread.php?t=93616&highlight=kmenuedit)

Back when I used Mandrake, I would have this problem quite frequently, and it always turned out to be a problem with DCOP.  Try doing the kmenuedit thing I described in the linked thread, and let us know the results.  If it's still not working, then this is a bug and should be reported.

---

### Post by carney1979 on 2005-11-26
[QUOTE=gingermark]Are you clicking the save icon after making your changes? Don't wanna sound insulting, it's just that's all I could think it might be.

If you have, do you then get an "Updating System Configuration" dialog box?[/QUOTE]

Yes to both.

Thanks, though.

David

---

### Post by yjsoon on 2005-12-06
Found this after clicking through a link on the other thread, just in case anyone's looking at this one and can't find the answer...

[http://www.ubuntuforums.org/showthread.php?p=531087#post531087](http://www.ubuntuforums.org/showthread.php?p=531087#post531087)

---

### Post by EisenPM on 2006-01-19
as is write in the other thread, which is too old and nobody is reading it,

the solution doesnt work on my computer and i dont understand the solution completely.

is it just that the kdecache and the home directory have to be "mine"? and then the menu should remember the changes upon saving?

---

### Post by Paul Gilster on 2006-01-19
I also was able to work out the menu editing problem with this command:

sudo chown -R <username> /var/tmp/kdecache-<username>

And many thanks to this forum for the help. But I'm still in the dark as to what is happening here. In other words, I used Kubuntu for several weeks (and edited the menu normally), and suddenly I couldn't because ownership of certain files changed. It would be terrific if someone could pin down why this occurs. In my case, it seems to have been associated with launching a graphical program (kate) with the sudo command and editing xorg.conf. I know now to use kdesu when launching a graphical program, but am not sure whether or not that would have prevented the problem. And just how did xorg.conf cause this problem? I assume it became saved with root permission or something...

---

### Post by SuspiciouS on 2006-01-19
Are you saying there that it's bad to use 'sudo kate xorg.conf' for editing, because this is the cause of youre problems?

---

### Post by EisenPM on 2006-01-19
i execute that command, but i still cant change the menu... when i open the shell and run kmenuedit from it, delete an icon and save, the shell will show this error:

```
eisenpm@FUCKUP:~$ kmenuedit
eisenpm@FUCKUP:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2c0035c

```

the application icon in question is a not working Kpdf. maybe i should uninstall it, and reinstall it again? it's the same with the context menu: there's an additional linked kpdf which is not working, thus when i click on a pdf file, it doesnt open. i have to manually select the working kpdf icin from the context menu.

---

### Post by Paul Gilster on 2006-01-20
Re the question about using a command like sudo kate xorg.conf (i.e., using sudo to launch a graphical program within KDE), I'm suspicious that that can cause problems. I believe I've read elsewhere that the proper way to launch a graphical program within KDE is to use kdesu; hence the command would be:

kdesu kate xorg.conf

As far as I can tell, this hasn't caused me problems, but twice when I used sudo kate xorg.conf, I wound up with various permissions being changed when I saved my changes, and in one instance couldn't get KDE to come up at all. So I'm suspicious, but I don't know enough about the deep workings of Kubuntu to know exactly what's going on.

---

