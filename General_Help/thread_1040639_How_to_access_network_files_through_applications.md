---
title: "How to access network files through applications?"
date: 2009-01-15
forum: General Help
---

### Post by joewski on 2009-01-15
I know how to get at network resources through Nautilus on the Gnome desktop, but when I open an application I can not see the network drives or resources from within the dialog box. 

In MS windows you can the network resource or you could navigate to it from any application with a file selector dialogue box.

How can I create the same environment in Ubuntu so that I can navigate to any network drive from within any application with a file selector dialogue box?

---

### Post by mssever on 2009-01-15
> **joewski said:**
> I know how to get at network resources through Nautilus on the Gnome desktop, but when I open an application I can not see the network drives or resources from within the dialog box. 

In MS windows you can the network resource or you could navigate to it from any application with a file selector dialogue box.

How can I create the same environment in Ubuntu so that I can navigate to any network drive from within any application with a file selector dialogue box?
What apps are we talking about? Apps that use the Gnome open dialog should show the same thing that Nautilus does. Others will use other methods. Also, what kind of network devices are we talking about?

---

### Post by joewski on 2009-01-15
I am using FreeNAS with a SAMBA server and installed a program called KeePassX in Ubuntu so I could access my Password database across multiple platforms.

I can't see how to get onto the network drive from this application. 
Any ideas how I can do this?

---

### Post by mssever on 2009-01-15
> **joewski said:**
> I am using FreeNAS with a SAMBA server and installed a program called KeePassX in Ubuntu so I could access my Password database across multiple platforms.

I can't see how to get onto the network drive from this application. 
Any ideas how I can do this?
I'm not familiar with KeePassX or FreeNAS. If they aren't Gnome programs, they probably won't be able to handle shares mounted using Nautilus' methods, since Nautilus uses non-standard ways to do that.

You should consider mounting your shares via fstab entries. Then, they'll work with every tool out there. Search for tutorials on fstab and CIFS if you don't know how to do this.

---

### Post by joewski on 2009-01-15
KeypassX is a password storage system bassed on Keypass. Both are open source. Attached is a screenshot of the dialog box. [http://www.keepassx.org](http://www.keepassx.org)

The Samba drive that is located on my FreeNAS server. (Which by the way is a cut down version of FreeBSD with a really easy to use Web interface, and runs on just about any system.) It can dish out files in a number of ways.

Now I thought you would find mounted systems in the mnt directory off the root directory. But is is not the case. So were is the network drives mounted. Other apps can see the smb://..... mounts, so where do I find the mounts for this type of application?

---

### Post by mssever on 2009-01-15
> **joewski said:**
> KeypassX is a password storage system bassed on Keypass. Both are open source. Attached is a screenshot of the dialog box. [http://www.keepassx.org](http://www.keepassx.org)

The Samba drive that is located on my FreeNAS server. (Which by the way is a cut down version of FreeBSD with a really easy to use Web interface, and runs on just about any system.) It can dish out files in a number of ways.

Now I thought you would find mounted systems in the mnt directory off the root directory. But is is not the case. So were is the network drives mounted. Other apps can see the smb://..... mounts, so where do I find the mounts for this type of application?
Judging from the screenshot, KeypassX appears to be a KDE (or at least Qt) app. The smb:// mounts that you're referring to are a Gnome thing. KDE probably has a separate, incompatible way of handling SMB shares. I'm not a KDE user, so I really don't know how it works. My best advice is to play around with konqueror (KDE3) or dolphin (KDE4) and see if you can figure something out.

My suggestion I made earlier about doing normal mounts via fstab or the mount command will work in all environments--Gnome, KDE, and anything more exotic.

---

### Post by joewski on 2009-01-15
Thanks for your reply.

I tried looking up fstab using the help system, but unfortunately it is crashing on many of the links to fstab, so I'm having some problems doing the research needed for the command.

I also am having the same issue with firefox add-ons that cannot browse the network.

In regards to KDE4 and KDE3 both systems can mount the network drives.

Its just these apps that can only see the local machine.

I'm sure the drives are mounting but where are they in the linux file system tree?

---

### Post by cariboo on 2009-01-15
When you use Nuatilus to mount network share they are mounted using [Gvfs]("http://fedoraproject.org/wiki/Features/Gvfs"). If you have an icon for the share on your desktop, you can navigate to ~/.gvfs, to see where the directory is mounted.

Jim

---

### Post by mssever on 2009-01-15
> **joewski said:**
> Thanks for your reply.

I tried looking up fstab using the help system, but unfortunately it is crashing on many of the links to fstab, so I'm having some problems doing the research needed for the command.

I also am having the same issue with firefox add-ons that cannot browse the network.

In regards to KDE4 and KDE3 both systems can mount the network drives.

Its just these apps that can only see the local machine.

I'm sure the drives are mounting but where are they in the linux file system tree?
That's the problem with the Gnome Virtual File System (GVFS). GVFS allows programs that use it to transparently access various network devices, including SMB. But GVFS doesn't actually mount them; it just makes them available to programs that use GVFS. Non-Gnome apps don't necessarily use GVFS, and KDE apps probably don't, since KDE presumably has its own approach in this regard. Therefore, your shares don't exist in the Linux filesystem tree. They're in a sort of parallel universe.

As far as documentation for my other suggestions goes, the standard location for command and config file documentation is the manual (the man command). ```
man some_command_or_file
man 8 some command_or_file
```The second form demonstrates how to explicitly name the manual section, which is sometimes necessary when the same entry appears in multiple sections. In man pages, cross-references are given with the section in parentheses. For example: ls(1) or mount(8). Some relevant man pages:

[LIST]
[*]man(1) documents the manual itself
[*]fstab(5) documents the format of /etc/fstab
[*]mount(8) documents the mount command and also lists the various mount options for the supported filesystems. The filesystem you're looking for is CIFS.
[*]mount.cifs(8) is documentation specific to CIFS. Note that you'll have to install smbfs to use this.
[/LIST]

---

### Post by mssever on 2009-01-15
> **cariboo907 said:**
> When you use Nuatilus to mount network share they are mounted using [Gvfs]("http://fedoraproject.org/wiki/Features/Gvfs"). If you have an icon for the share on your desktop, you can navigate to ~/.gvfs, to see where the directory is mounted.

Jim
Really? Does that mean that GVFS does real mounts these days? It's been a very long time since I've done anything with GVFS.

---

### Post by joewski on 2009-01-16
After searching the I found out how to do it.
reference here

[http://www.faqs.org/docs/lnag/lnag_drives.html#samba_mount](http://www.faqs.org/docs/lnag/lnag_drives.html#samba_mount)

Unfortunately the instructions are not quite correct.
Here is how I ended up getting it to work.

Now I'm a newbee so I am not sure if I am doing it correctly. So if anybody can see anything glaringly wrong please point it out.


Firstly I needed to make a directory where I can mount the windows directory.

```
sudo mkdir /mnt/landrive
```

replace landrive with whatever you like

Next I mounted the drive using a samba mount

```
sudo smbmount //freenas/landrive /mnt/landrive
```

freenas is the server and landrive is the directory that you normally mount in gnome or any other package.

Now when I navigate to /mnt/landrive I can see all the network files.

To unmount the drive I do this.

```
sudo smbumount /mnt/landrive
```

I found I needed to do this in sudo as it wouldn't work in normal mode.
I'm not sure if this is persistent over reboots or logins.

---

### Post by mssever on 2009-01-16
That's an approach I'm not familiar with. Did you read its man page? I ask because there's one method of mounting SMB shares that's now deprecated, and guides that haven't been updated might be giving outdated information. I don't know whether smbmount uses cifs (the non-deprecated method), but the man page will hopefully warn you if it's deprecated.

Additionally, I'm pretty sure that smbmount will not persist across logins. It appears to be designed to provide a convenient way to mount shares, but not necessarily to handle shares that you want to be available at all times. Persistent mounts need to be listed in fstab.

Finally, requiring sudo to mount is expected. There are only a few situations where you DON'T need to be root to mount or unmount.

---

