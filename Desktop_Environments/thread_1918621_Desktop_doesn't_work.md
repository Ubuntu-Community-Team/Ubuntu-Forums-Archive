---
title: "Desktop doesn't work"
date: 2012-02-01
forum: Desktop Environments
---

### Post by brunoproduit on 2012-02-01
Hello,

I have a problem with my desktop folder. When i try to click/rightclick on my desktop it just does not respond.
I tried to change the owner/rights of the folder using "Chown" and "Chmod" but still nothing
The folder "Desktop" exist and is at the right place, but it appears to be a common folder not related to the real desktop. I am currently using ubuntu 10.04.

i hope this is not a repost,
any help would be greatly appreciated!

---

### Post by Paddy Landau on 2012-02-01
You shouldn't have to chmod or chown your desktop!

Please open a terminal (press Ctrl-Alt-T) and type the following two commands. Post the results here (between [noparse]```
[/noparse] and [noparse]
```[/noparse] please).
```
ls -l /home
ls -l ~
```Thanks

---

### Post by brunoproduit on 2012-02-01
Hi,

Thanks for your answer,

I think thats what you need 

```


drwxr-xr-x 99 bruno bruno  12288 2012-02-01 18:55 bruno

drwxrwxrwx  2 bruno bruno     4096 2012-02-01 15:48 Desktop

```

bruno is me as you can see.
Thanks.

---

### Post by Paddy Landau on 2012-02-02
Hmm, everything looks correct. I am most puzzled as to why a right-click on your desktop does nothing.

What version of Ubuntu did you install?

---

### Post by brunoproduit on 2012-02-02
Hi yes as you see the folder "desktop" is there but it seems to be a useless folder which is named desktop with no relation to the real thing.
My Ubuntu version is 10.04 (lucid lynx) the long term support version of Ubuntu.
What should i do? create another desktop? is that even possible?
Thanks

---

### Post by Paddy Landau on 2012-02-02
Hang about, I've just realised that the second command showed only your Desktop, and nothing else -- no Pictures, Documents, Videos, Music, anything.

That is most bizarre!

Please enter the following three commands, and cut-and-paste the results here (each one within its own separate [noparse]```
[/noparse] and [noparse]
```[/noparse] please).
```
echo ${USER}
ls -lq ~
ls -lqA ~
```

---

### Post by brunoproduit on 2012-02-02
Hello,
It does have music images etc. i just thought this wasn't needed for you i just took out desktop.

for your first command it just gives me

```

bruno@bruno-laptop:~$ echo ${USER}
bruno

``````

bruno@bruno-laptop:~$ ls -lq ~
drwxrwxrwx  2 bruno bruno  4096 2012-02-01 22:19 Desktop
drwxr-xr-x  9 bruno bruno  4096 2012-01-23 21:59 Documents
drwxr-xr-x  2 bruno bruno  4096 2012-01-30 16:36 Downloads
drwxr-xr-x  6 bruno bruno 20480 2012-01-30 15:55 Music
drwxr-xr-x 13 bruno bruno  4096 2012-02-01 21:02 other
drwxr-xr-x  6 bruno bruno  4096 2012-01-29 00:22 Pictures
drwxr-xr-x  2 bruno bruno  4096 2010-06-27 11:16 Public
drwxr-xr-x  2 bruno bruno  4096 2012-01-29 00:13 Templates
drwxrwxr-x  2 bruno bruno  4096 2010-08-31 16:56 Ubuntu One
drwxr-xr-x  2 bruno bruno  4096 2012-01-29 00:22 Videos



```everything looks good


I took out all the known unnessesary programs

---

### Post by Paddy Landau on 2012-02-02
All right, that looks better. I used "-q" in the option in case there was some funny character in the folder name.

I would recommend you reset the Desktop permissions, although this is not necessary:
```
chmod go-w ~/Desktop
```If you right-click the desktop itself, nothing happens. Is that correct?

What happens if you right-click the Desktop folder in Nautilus? What happens if you right-click any other folder in Nautilus?

In Nautilus, navigate to your Desktop. Right-click in the empty area to create a new empty document (Create Document > Empty File). Does that work? If it does work, try right-clicking the new, empty file on your desktop to see if anything happens.

---

### Post by brunoproduit on 2012-02-02
Hello,

I've done your command, but nothing happens it changes unfortunately nothing...
i really don't know.
I already tried to create files with nautilus and I've done it another time after the command.
the file is created and you can deal with it as normal but only in nautilus as desktop would be an usual folder,
only thing is that nothing appears on the real desktop (not in nautilus) and it still doesn't have a reaction.

Thanks

---

### Post by Paddy Landau on 2012-02-02
It seems that your Linux has stopped seeing the Desktop folder as the desktop. When did that start?

Please view the following file (you can use the usual text editor) and paste the contents here.
```
~/.config/user-dirs.dirs
```

---

### Post by brunoproduit on 2012-02-02
That's the file you want. 
```

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

```
Thanks

---

### Post by brunoproduit on 2012-02-02
That's the file you want. 
 	Code:
 	# This file is written by xdg-user-dirs-update # If you want to change or add directories, just edit the line you're # interested in. All local changes will be retained on the next run # Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped # homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an # absolute path. No other format is supported. #  XDG_DESKTOP_DIR="$HOME/Desktop" XDG_DOWNLOAD_DIR="$HOME/Downloads" XDG_TEMPLATES_DIR="$HOME/Templates" XDG_PUBLICSHARE_DIR="$HOME/Public" XDG_DOCUMENTS_DIR="$HOME/Documents" XDG_MUSIC_DIR="$HOME/Music" XDG_PICTURES_DIR="$HOME/Pictures" XDG_VIDEOS_DIR="$HOME/Videos" 
Thanks

---

### Post by N00b-un-2 on 2012-02-02
your user-dirs.dir file looks correct.  out of curiosity are you running a dual boot?  I found out the hard way once that linking any file on windows to your ~/Desktop folder on the Linux side will cause a whole slew of problems.
Aside from that, the only other thing I can think of would be an issue with nautilus itself.  You may try reinstalling nautilus.

---

### Post by brunoproduit on 2012-02-02
Sorry for the double post.

I am actually not using a dual boot with anything, althought i would want to, but my computer has not enough
space to think about it.
Reinstalling nautilus would be a good idea. can i do it with apt-get install, or how should i do it?

---

### Post by Paddy Landau on 2012-02-02
Reinstalling Nautilus won't do anything unless the programs have been corrupted. To do so:

[LIST]
[*]Reboot into recovery mode: Restart; as the computer restarts, hold down the Shift key until the Grub menu displays; choose the second option (Recovery Mode); scroll down to Drop to root shell prompt.
[*]Enter the following two commands. **Warning:** I have not tried them, so I cannot guarantee that they will work! The last two items (in italic) may not be necessary for you, though it can't hurt to install them.```
apt-get purge nautilus
apt-get install nautilus gnome-session ubuntu-desktop *nautilus-image-converter nautilus-share*
```Then restart.
[/LIST]
 But, I would be tempted to try something else first. Remove the settings that Nautilus has generated, in case that is what is wrong. The following command will remove the settings but place them in old-nautilus just in case you need them again.
```
mv ~/.gconf/apps/nautilus ~/old-nautilus
```Then log out and in again (it's not necessary to restart) to see what happens. If it's all messed up, use the following command to restore the settings.
```
rm -R ~/.gconf/apps/nautilus
mv ~/old-nautilus ~/.gconf/apps/nautilus
```Then log out and in again.

Sorry we can't be more helpful. This is a strange situation that I have not come across before.

---

### Post by brunoproduit on 2012-02-02
Hello I tried

mv ~/.gconf/apps/nautilus ~/old-nautilus
and restarted my computer and it fixed everything!
I obviously then didn't try the other commands.
Thank you so much for your help and your time!
finally working!

---

### Post by Paddy Landau on 2012-02-02
Fantastic. Have fun!

---

### Post by Paddy Landau on 2012-02-02
Oh, yes, you can delete the old-nautilus folder now.

---

