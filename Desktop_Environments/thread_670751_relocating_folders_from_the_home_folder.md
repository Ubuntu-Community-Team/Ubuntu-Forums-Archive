---
title: "relocating folders from the home folder"
date: 2008-01-17
forum: Desktop Environments
---

### Post by christopher.newell on 2008-01-17
Is it possible to set a new location for folders within the home folder?  For example, I have my photos and videos on a separate hard drive and I'd like the folders within my home folder to go directly to the other drive instead.  So far, I have a shortcut in each folder.  It's not a bad system, but it's an extra step that I'd like to cut out.

---

### Post by PeterJS on 2008-01-17
How is the shortcut setup? If you created a symlink between ~/Pictures and /media/some/place/Pictures, the two folder names could be used interchangeably, and be the same location for 99% of cases(there are some like going up a folder, in nautilus that may be weird, but the back button should get you to the right spot).

---

### Post by snkiz on 2008-01-18
I have a similiar setup on my system. My media files on seperate drive. all I did was create sim links to the folders then rename them to replace the folders in my home directory. this even works with multi user acess if the permissions are set. i just haven't figured out how to make a file take on the permissions of the folder its being written to, so every so often i have to do cleanup.

---

### Post by vanadium on 2008-01-18
symbolic links indeed are what you should use here.

---

### Post by yota on 2008-01-18
The locations can be configured in  ~/.config/user-dirs.dirs
> 
cat ~/.config/user-dirs.dirs 
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Modelli"
XDG_PUBLICSHARE_DIR="$HOME/Pubblici"
XDG_DOCUMENTS_DIR="$HOME/Documenti"
XDG_MUSIC_DIR="$HOME/Musica"
XDG_PICTURES_DIR="$HOME/Immagini"
XDG_VIDEOS_DIR="$HOME/Video"


see the "xdg-user-dirs" package

Hope this helps!

---

### Post by christopher.newell on 2008-01-20
Sorry yota, I didn't understand your post.  If I'm reading correctly, that looks like a way to rename folders within the home directory, whereas I wanted to click on the photos folder in my file browser and go to a file on a separate volume.  I did get the symbolic links to work, so thanks for the help everyone.  It actually took me quite a while to find out how to make symbolic links.  I searched this forum and I Googled it, but it seemed like every link I followed was a suggestion that someone needed one or a note that someone made one!  Finally I found a source that said 'type this to make a symbolic link'.  Now onto the next problem... er, I mean the next learning opportunity!

---

### Post by yota on 2008-01-21
Hi Cristopher,

first of all if the symlink solution meets your need simply forget my post, it's a perfectly sane solution. Maybe I misunderstood what you meant with "relocate" since, as you can see I'm not an english motherlanguage.

by the way, the file in ~/.config/user-dirs.dirs ("~" is your home directory) is a text file that can be edited to explicitly set the position of the Documents, Pictures etc. folders.
Let's say that you do not want a "Music" folder under your home at all, but you want to place your music in the /public/music folder instead. If so you can set the path by editing that file.

One last handy hint: to create symlinks with the gui you can drag&drop with the third mouse button (the wheel usually).

Hope this helps!

---

### Post by christopher.newell on 2008-01-21
Thanks yota.  I understand what you meant now.

---

### Post by jomaveger on 2008-05-02
Hi!

First of all, forgive my poor english. I do not speak english very well. My name is Jose Maria and I am from Madrid, Spain. I've just installed Ubuntu 8.04 and I think it's great: sound card, graphics card and wireless work fine. But I am new to Linux and I am a bit lost.

I have an internal hard disk with Windows Vista and Ubuntu and I also have an external usb hard disk with all personal files: documents, pictures, music and videos. I have configured Windows Vista to look for Documents, pictures and the other private stuff on that usb hard disk and now I am trying to do the same with Ubuntu to have centralized access to all that stuff for the two oss. The fact is I am not able to get it work in ubuntu. 

I've tried what yota said, editing the *users-dirs.dirs* file, but it doesn't work. For example, I replaced the line

XDG_VIDEOS_DIR="$HOME/Video"

with this other line

XDG_VIDEOS_DIR="/media/usbdisk/personal_Folder/Video"

and nothing happens.

I would appreciate any help that anyone can give me.

Regards.

---

### Post by snkiz on 2008-05-08
Your lucky I still have notifaction set on this thread, you really should have made a new post and just refernced this one. That being said I think I can help you. the path to the dir you want should start with $ To tell the command  witch shell to use. If that doesn't work try my sim link suggestion see above. to make a sim link right click on the folder you want and select make link, or try the middle click suggestion above.

---

