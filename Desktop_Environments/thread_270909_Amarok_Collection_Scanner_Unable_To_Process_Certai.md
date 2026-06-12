---
title: "Amarok Collection Scanner Unable To Process Certain mounted SMB share files"
date: 2006-10-03
forum: Desktop Environments
---

### Post by nchase on 2006-10-03
Hey, I just moved my music files over to another pc on the network, and set up a samba share and mounted it. I wanted amarok to be able to play these files. I add them to the collection and that's fine, but when I go to scan, after about 86%, it gives me a list of files that it couldn't process. Somehow this leaves me with none of the files from the samba share added to my collection.

I checked the files and they do have the proper permissions, just like every other file in these folders.

I can play the files by going into files and adding them to the playlist manually, but they cannot be added to the collection.

Here is a screenshot of what the error message says:

[img]http://nchase.googlepages.com/collection-scan-report-Screenshot.png[/img]


Has anyone else had a problem like this? Is there a fix for it?

---

### Post by dwasifar on 2006-10-04
I am doing exactly the same thing as you - Amarok under Gnome with the collection folder set to a Samba share - and when I first set it up I found that for some reason the Samba shares were mangling the occasional filename, in such a way that most of the time they LOOKED right in the error window, but were actually not.  I'm guessing Amarok and Nautilus were not reporting them the way the kernel saw them, or something of that nature.  I know it sounds screwy, but that's what it was.  Occasionally I would see a filename in the error list that was visibly wrong, something like .mpx33 or something, which is what clued me in to the problem in general.  

Try this.  Navigate in Nautilus through the folder path to one of the files that Amarok is having trouble with.  Try to rename it.  If it errors because it can't find the file, or because there already exists a file with that name, that's your trouble.

Unfortunately I never found a specific way to fix it.  I wound up doing a clean install of Ubuntu to rid myself of some headaches that came along with having Kubuntu desktop installed over Ubuntu, and when I finished, the problem was gone.  It may have had something to do with how I wound up mounting the shares in /etc/fstab:

```
//192.168.0.25/mp3 /remote/mp3 smbfs username=****,password=****,dmask=777,fmask=777,auto,rw 0 0
//192.168.0.25/misc /remote/misc smbfs username=****,password=****,dmask=777,fmask=777,auto,rw 0 0
```

That works for me now.  I have other issues with Amarok not really reacting well to having a remote drive in its path, but I don't have your issue any more.  

Let me know what you find.  I'll be interested to see the resolution.

---

### Post by nchase on 2006-10-04
Thanks for the info and the quick reply. It's a lot more than I'm used to on forums.

So far I have hit a snag - I tried to edit one of the filenames in nautilus and it told me that I don't have the necessary permissions to edit the file. I don't understand, because the permissions are set to read write and execute for all, and I can't even edit the filename when browsing through nautilus as root.

By the way, my fstab entry looks almost identical to yours except that I have my samba username and password saved in a file called .smbcredentials in the root folder.

---

### Post by dwasifar on 2006-10-04
> **nchase said:**
> Thanks for the info and the quick reply. It's a lot more than I'm used to on forums.

Glad to offer what help I can, such as it is.  :)

> **nchase said:**
> So far I have hit a snag - I tried to edit one of the filenames in nautilus and it told me that I don't have the necessary permissions to edit the file. I don't understand, because the permissions are set to read write and execute for all, and I can't even edit the filename when browsing through nautilus as root.

Two things:  1) What are the permissions like on the server side?  Does the username you use to connect to the share have permission for those files and directories?  and 2) how are the permissions set on your mount point folder /media/netdrive1?

As an experiment, connect to your Samba share from a Windows box and see if you can add/delete/rename in that folder.  If you can, your problem is on your client; if you can't, it's on your server.

> **nchase said:**
> By the way, my fstab entry looks almost identical to yours except that I have my samba username and password saved in a file called .smbcredentials in the root folder.

Yeah, that's the right way to do it.  I was lazy when I set it up and haven't gotten around to fixing it yet.

---

### Post by nchase on 2006-10-04
Looks like I can edit some files, but not others - on both a windows pc and this pc.

---

### Post by dwasifar on 2006-10-04
Is it consistent across client machines, i.e. the same files behave the same way no matter where you're connecting from?  If so, then you need to be looking at the server as the cause.  But other than doing a chmod on the whole directory on the server I'm not sure what to suggest.

---

### Post by dwasifar on 2006-10-11
Hey, if you're still having the problem, this may help you.  I accidentally generated a similar problem by adding unicode mapping to my fstab:

```
//FileServer/mp3 /remote/mp3 smbfs username=****,password=****,iocharset=utf8,codepage=unicode,unicode,dmask=777,fmask=777,auto,rw 0 0
```

I put that in to clean up how the files looked when I browsed them in Nautilus, but it made Amarok barf on a rescan with exactly the same kind of error you're having.

Returning it to its prior state made the problem go away:

```
//FileServer/mp3 /remote/mp3 smbfs username=****,password=****,dmask=777,fmask=777,auto,rw 0 0
```

---

### Post by lordchaos on 2006-11-06
Using cifs fixed my problem I had with smbfs.

TAKEN FROM [http://amarok.kde.org/amarokwiki/index.php/Samba](http://amarok.kde.org/amarokwiki/index.php/Samba)

Mounting shares on Windows boxes

On Windows 2k/XP/Server shares it is important to mount them as cifs. cifs can handle much more files in directories and interacts better with the Microsoft software. Moreover it is important to set iocharset=utf8 because Windows uses Unicode for their filesystem since Windows 2000. This way you are able to use special characters abroad ASCII in your filenames without running into problems. An example line for /etc/fstab:

//server/share /path/to/mountpoint cifs iocharset=utf8,uid=username,gid=users,guest,file_mode=0444,dir_mode=0555 0 0

---

