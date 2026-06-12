---
title: "How do you access network files from an application?"
date: 2008-12-13
forum: General Help
---

### Post by SteveDee on 2008-12-13
In Nautilus I can click on "Network" under "Places" and do what I like with any files located in remote shared folders.

But how do I access these shared files from the "Open" dialogue presented by applications (e.g. gedit, mplayer & so on)?

There must be an easy way to edit a file that is located on a remote computer, so long as suitable sharing/file permissions have been set.

---

### Post by vanadium on 2008-12-13
The gnome open/save dialog should allow you to follow the same path as that wheat you see in nautilus. For applications that do not know gnome user space, you can access the mounted paths in ~/.gvfs

I do not have the experience myself. I prefer the old command line approaches to mount network drives.

---

### Post by SteveDee on 2008-12-13
> **vanadium said:**
> The gnome open/save dialog should allow you to follow the same path as that wheat you see in nautilus. For applications that do not know gnome user space, you can access the mounted paths in ~/.gvfs

I do not have the experience myself. I prefer the old command line approaches to mount network drives.

Thanks for your reply, but I don't really understand.

As none of the apps I have tried present me with a Network option, are you implying this may just be a config issue? (e.g. a change to some conf file which allows Gnome to share this info).

Re: accessing the mounted paths in ~/.gvfs, I assume this is either a hidden folder or file, but I cannot find it.

---

### Post by vanadium on 2008-12-13
It is a hidden folder. In a gnome dialog, you can right-click and select "show hidden folders" to see it. If you look inside, you will see directories for mounted file systems if any. Anyway, this is more applicable for accessing these mounted file systems using command line tools. In gnome dialogs, you should find the mounted file systems under "Places".

---

### Post by SteveDee on 2008-12-13
Yes, there is a .gvfs directory under ../home/steve/ but its empty.

So I guess what I need is some way to get Gnome to list network drives in all "Places" views (i.e. for all applications).

When I create a network bookmark in Nautilus, I can see that in an application. But when I select it, a dialog says "Location is already mounted".

Any other suggestions?

---

### Post by vanadium on 2008-12-13
You might indeed need to explicitly mount a network location for this to work. In Nautilus, there is a File - Connect to server command. This will mount a network location locally, so you can browse to it and use it as if it were a local file system. Such connections will show up in the .gvfs directory where they can be accessed from the command line.

---

### Post by fragos on 2008-12-13
If both systems are Linux try the following -- it works for me:

I use NFS between my Desktop and Laptop as my server. Both being on the same LAN. On the server there must be an /etc/exports with the following. Replace the fields in {} with your information. In my example I'm giving access to the entire home folder tree. This scheme works with any mix of 8.04 and 8.10. There can be multiple entries giving more clients permission.

/home/{Laptop user} {Desktop hostname}.local(rw)

This allows the Desktop to access the home folder of the laptop. Prior to Ubuntu 8.04 you need to run "sudo exportfs -rv" for the system to read /etc/exports. New versions do this for you at boot.

On the Desktop create a folder to mount to. In my case I placed that folder in my home folder.

On the Desktop side I run

sudo mount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

To un-mount I run

sudo umount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

You can extrapolate what to do from this working example. I chose not to use fstab to mount and wrote a couple of bash scripts that supply the parameters to the mount and umount commands.

---

### Post by SteveDee on 2008-12-14
I just wanted to say that I was embarrassed when I posed this question, as I expected someone to come back with a "duh!...just click the..." reply. 

Editing files across a peer-to-peer network is no big deal on that other OS (I think its called "Gates" by Bill Windows) but appears to be tricky for us 'Buntus.

Although my original need was quite trivial, this problem has now grown legs. So now I have to follow this through, even if it means writing a script to run during startup.

I'm gonna explore the options in both posts (thanks to vanadium & George Fragos) and I may come back with any useful conclusions.

---

### Post by vanadium on 2008-12-14
fragos refers to the good old classical command line tools, which I also use because I find them powerful, convenient and reliable. You *can* do this the easy way using nautilus, though. You set up a connection once using "File - Connect to server". In the dialog, check "Add bookmark" and provide a name.

The server will be added to your bookmarks, and next time you can connect to it using the Bookmarks menu or "Places" in the left pane, which also should work from within a gtk file dialog.

Alternatively, when using command line tools to mount a server, the server will appear somewhere in your file system (where you mounted it) just like any local folder.

---

### Post by SteveDee on 2008-12-14
Yes, using Nautilus to pick the required remote folder seems a bit like mapping a drive in Windows. I get a network folder icon on my desktop, and I can also access this in apps like gedit in its "Places" pane when selecting Open.

It just so happens that I originally hit this problem using WikidPad, where (I now realise) finding my remote Linux wiki involves the following steps:-
 -mount remote folder
 -select Open in WikidPad
 -navigate to /home/steve
 -right click in right pane & select "show hidden files"
 -navigate to /home/steve/.gvfs
 -select folder/file

Not exactly "seamless" but once done, the location is stored in the Recent list. Anyhow, this ties in with your earlier comments on .gvfs which I would not have found other-wise.

I think I can live with this approach because its not something other family members will need to do. It would be a nice touch if I could auto map/mount remote folders at startup, so long as this did not increase OS load time (as it does in Windows). I'll play some more with the cli approach.

I struggle with the Connect To Server dialog, not least because the Help tells me "..you may click on the Browse network button..".  I don't have this button in my dialog. Entering the name or IP of another computer in the Server field does not work (I assume because none of my computers are servers).

Thanks once again, " 'job's a good-un!"

---

### Post by vanadium on 2008-12-14
You could create a symbolic link to your mount in .gvfs in your home directory. Then the steps would reduce to

* Mount your remote folder
* Navigate to your link

There will not anymore be a need to display hidden files, and you do not need to navigate outside of your home directory anymore. The symbolic link obviously will only work when the remote file system is mounted.

You can create a symbolic link with nautilus by pressing Ctrl+shift, and then dragging the directory you want to link to the place where you want the link to appear.

To mount automatically at startup, you would need to take a command line approach.

---

### Post by fragos on 2008-12-14
CLI can be a bit cumbersome but creating simple shell scripts can make things simple. Here's my script "dell-mount" that requires no parameters but also allows me to use the last part of a local IP if I choose.

#!/bin/bash
if [ -n "$1" ]; then
echo Mounting 192.168.1.$1
sudo mount 192.168.1.$1:/home/fragos /home/fragos/dell
else
echo Mounting dell.local
sudo mount dell.local:/home/fragos /home/fragos/dell
fi

---

### Post by SteveDee on 2008-12-16
I was curious to see if I could use Nautilus to auto mount a remote directory, rather than use NFS. So I created a script like this;

#!/bin/bash

nautilus -n smb://davis-desktop/linuxwiki

nautilus -q

*{I was then going to check the contents of the .gvfs directory to test for success}*

This works except Nautilus stays open, and if I run the script in a terminal I can see that it generates this error:-
 ** (nautilus:8126): WARNING **: Unable to add monitor: Not supported

The connection to my remote linuxwiki directory survives if a manually close Nautilus.

I haven't been able to find a definition for this error so far.

---

### Post by vanadium on 2008-12-16
What is the good reason do try that if you need to use the command line anyway?

---

### Post by SteveDee on 2008-12-16
> **vanadium said:**
> What is the good reason do try that if you need to use the command line anyway?

Well, as I said in an earlier post, this issue has grown out of all proportion to the original problem.

I guess I'm just following it up out of interest, ...or perhaps in an effort to avoid Christmas shopping!

But I had a couple of rather vague ideas on how I might use this.

The first was to auto-run this script (as Ubuntu/Gnome loads) to attempt connection to several remote directories on the other 3 computers we have scattered around the house. However, I don't think this will work unless I delay the running of this script for a couple of minutes, as I can't normally "see" the other network computers immediately after startup.

The second idea is that when I want to access and edit a remote wiki, I just click on a panel icon which (via a script) attempts to connect to the remote directory, checks that its there (via .gvfs), and then loads WikidPad.

---

