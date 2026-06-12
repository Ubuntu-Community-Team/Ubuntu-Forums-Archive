---
title: "Controlling gvfs mount points?"
date: 2012-05-08
forum: Desktop Environments
---

### Post by Newbunto on 2012-05-08
[SIZE=2]gvfs by default uses a mount point name like "share on host". (I'm using SMB but I imagine that the same issue arises with other backends.)

Is there any way to control the name of the mount point?

I have several reasons for disliking the current naming.
[/SIZE]
[LIST]
[*][SIZE=2]It's verbose to type.[/SIZE]
[*][SIZE=2]The spaces require escaping to type in typical shell commands.[/SIZE]
[*][SIZE=2]Some applications may handle spaces in path names poorly, awkwardly or not at all. (For example, I am attempting without success to get [/SIZE][FONT=Lucida Console][SIZE=2]make[/SIZE][/FONT][SIZE=2] to do the right thing with such a path name.)
[/SIZE]
[/LIST]
[SIZE=2]The current default must remain as it is but I am using gvfs-mount to mount shares explicitly so am looking for a means of changing the name of the mount point when using gvfs-mount.[/SIZE]

[SIZE=2]In my environment, the share name by itself is unique so that would work much better for me. The current default must remain as it is but I would change to using the share name alone if I could.[/SIZE]

[SIZE=2]Even then I have one share name with an unusual character in it where explicit control over the name of the mount point would suit me better. (However with some effort I could change the share name.)
[/SIZE]

[SIZE=2]Related but different ... the name of the gvfs folder itself (~/.gvfs) is not ideal from my perspective i.e. it's hidden so I often have to unhide it. Changing to show *all* hidden files is not ideal because there are a lot of hidden files that I want to keep hidden. The current default must remain as it is but I would change it (e.g. to gvfs) if I could.
[/SIZE]

[SIZE=2]I'm running Ubuntu 11.10 and essentially all files are on a central server accessed via gvfs.
[/SIZE]

---

### Post by Newbunto on 2012-05-10
No takers?

Are there any command line options? configuration files? environment variables? something else? that control the behaviour of gvfs?

---

### Post by LewisTM on 2012-05-10
Juste make symlinks to .gvfs or any child dir, name them what you like and put them wherever you want. Bookmarks work well too.

Cheers!

---

### Post by Newbunto on 2012-05-13
[SIZE=2]That workaround works. [FONT=Courier New]make[/FONT] is happy with that. Thanks.

I'm still interested if anyone knows of any means of directly controlling the mount point naming.[/SIZE]

---

### Post by selahlynch on 2012-05-17
I am also very interested in this.  I have 10's of different network directories I must access and they are often changing.  It is very inconvenient to have to make new links every time.

---

### Post by LewisTM on 2012-05-17
I'm quite sure you can't control GVFS in that fashion but feel free to request a feature.
I fail to see how that would help you. If your network names change often any custom command would have to take that into account. Or would you want to have a given name for any network connection matching certain criteria?
I guess one could write a simple script that monitors the .gvfs directory and creates/updates links based on the names of the connections.

---

### Post by Morbius1 on 2012-05-17
> [SIZE=2] I'm still interested if anyone knows of any means of directly controlling the mount point naming.[/SIZE]     You can control where the mountpoints are located:

Create a Folder, for example:
```
mkdir ~/GVFSmount
```Then run the following command:
```
/usr/lib/gvfs/gvfs-fuse-daemon ~/GVFSmount
```It's temporary and doesn't survive a reboot so you'd have to create a script and add it to the startup applications I guess.

But the things will still mount like: "share on server" within GVFSmount.

I usually just create a bookmark to the $HOME/.gvfs folder itself. Then it shows up in the Open and Save AS boxes on the left panel. Within that bookmark are the remote shares I have mounted.

---

### Post by Newbunto on 2012-05-18
> **LewisTM said:**
> feel free to request a feature.

How would I do that?

> I guess one could write a simple script that monitors the .gvfs directory and creates/updates links based on the names of the connections.

For the moment, all the shares are mounted using gvfs-mount commands. Hence a simple wrapper script would be able to create (and delete) the symlinks, without any need for monitoring or polling a directory. However I am mindful of the possibility that a share might be mounted temporarily and manually by the user.

I would think that it needs a sequence of matching rules (per user) that map a "URL" into a mount point. The idea is that some software may pass around the original URL but it should be possible for all such software to identify unambiguously where the URL is mounted.

---

### Post by Newbunto on 2012-05-22
> **Newbunto said:**
> How would I do that?

No takers?

---

### Post by LewisTM on 2012-05-22
GVFS is a component is GIO which is itself part of the GNOME project.
Here's a [page]("https://live.gnome.org/") at GNOME.org with instructions on how to give feedback and contribute.

---

