---
title: "Xubuntu + Thunar + Networking Browsering?"
date: 2010-12-06
forum: Desktop Environments
---

### Post by Sugi on 2010-12-06
I was on Ubuntu Lucid Lynx then installed Xubuntu-desktop [xfce].

I am wondering if gigolo is even worth it? There are tons of posts and threads about how inaccessible it is.  Currently I am using nautilus, but I would like to switch over to something light weight. but close as possible to networking browsing with nautilus.

Please provide me with your own experience of network browsing in xfce.

Reference:
[http://wwww.ubuntuforums.org/showthread.php?p=7546836](http://wwww.ubuntuforums.org/showthread.php?p=7546836)
[http://ubuntuforums.org/showthread.php?t=1481683&page=2](http://ubuntuforums.org/showthread.php?t=1481683&page=2)
[http://ubuntu-lxde.wikidot.com/intrepid](http://ubuntu-lxde.wikidot.com/intrepid)

Thanks,
Sugi

---

### Post by inobe on 2010-12-06
the last time i checked several years ago an app called "py neighborhood" was buggy and worked for some with tweaking, it didn't work for me.

so basically it was good for a file server but not browsing a server.

i haven't tried since.

---

### Post by Sugi on 2010-12-06
Thanks for your input. I have read some threads about "py neighborhood".

Sugi

---

### Post by Sugi on 2010-12-09
Bump.

---

### Post by Sugi on 2010-12-11
Still need opinions.

---

### Post by Jose Catre-Vandis on 2010-12-11
Don't have any trouble with gigolo when using it to connect to network filesystems. You just have to get into the practice of connecting via gigolo then accessing files via thunar. I don't use regular ubuntu nor nautilus, and rarely have a need for gigolo as my network shares all come through via nfs or samba, so they are well handled by the system and thunar.

---

### Post by ugm6hr on 2010-12-11
I'm back with Gnome again (on 10.10), but found Gigolo perfect on 10.04.
Gigolo is also now default on Xubuntu.
Consider adding Bookmarks in thunar for your commonly used network servers - makes it easy to connect, then just click in thunar to open.

---

### Post by Sugi on 2010-12-26
Sorry for the late reply [had some computer problems :S], thanks for the input.  I'll look into tutorials or just testing out Gigolo now.  Jose Catre-Vandis, I would be interest in hearing more about your methods.

Sugi

---

### Post by Morbius1 on 2010-12-26
I used to use the traditional method of automounting remote shares by adding lines to fstab but somewhere along the way things changed and it doesn't work as well as it used to. Today I automount using Gigolo. 

Gigolo is more than a browser it can automount remote shares as well. In fact you can have it automatically wait until the machine or device that has the remote share is up and running before it attempts to mount.

It's really a very impressive little utility. Check this out for more info:
[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

[COLOR=Blue]**EDIT:**[/COLOR] The only real drawback to it is not because of Gigolo but because it's really a front end to gvfs-mount smb://. It will mount the remote share the same way as Nautilus does in a "hidden" directory:
> /home/your-user-name/.gvfs
If you can live with it in a hidden directory than that's fine. If not you can always create a symbolic link from the .gvfs directory to a "real" directory.

---

### Post by Sugi on 2010-12-26
Honestly, I would just prefer to use smb://, and I don't mind hidden directories at all. Actually, I would rather have them and dirtying up my /home directory.  Thanks Morbius1 for the link, I am going to pull out my old laptop and check all of these great comments.

Thanks guys and if anyone else has comments or thought, please let us know!

Sugi

---

### Post by ugm6hr on 2010-12-27
> **Morbius1 said:**
> If you can live with it in a hidden directory than that's fine. If not you can always create a symbolic link from the .gvfs directory to a "real" directory.

Or add a bookmark in Thunar to the hidden directory.

---

