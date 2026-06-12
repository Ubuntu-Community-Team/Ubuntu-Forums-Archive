---
title: "fstab mountpoints  - icons in &quot;Desktop&quot;, &quot;Computer&quot; or &quot;Places&quot;"
date: 2006-09-18
forum: Desktop Environments
---

### Post by domm on 2006-09-18
Hello dear ubuntu users,

Is it possible to have another partition displayed like the "Filesystem" (root part.) icon in nautilus's "computer" window? One that does not show up on the desktop when mounted but only in "copmuter"?

I get somewhat like it when I am adding "noauto" in fstab, but then ofcourse the partition doesn't get mounted untill I click it in the "computer" window (But when mounted there's no icon on the desktop!) Also it will not show up under "Places".

I am aware of the other cases:
1. mount without "noauto" (in /media/<partition>) it will show up on desktop and in "computer"
2. mount somewhere else than /media => it will be neither on the desktop nor in "Computer"
(3. pmount.allow => same as 2.)

Disabling "volumes_visible" in gconf is no option for me since I want removable medias to pop up on the desktop.


Any ideas?

(BTW - slightly offtopic: Does someone know what's the difference between the "users" and the "user" options in fstab? Only the first one is documented in fstab's manpage, though I quite often stumble upon the latter during googleathics)


Update:
What is also confusing me is that I have a webdav folder mounted in fstab with "users,noauto" that does show up in "Places" and on the desktop when I mount it by clicking it's icon in "Computer". But for the hd partition mounted with the same fstab options there's just an icon in "Computer" and nowhere else.

---

### Post by turbojugend_gr on 2006-09-18
Simply edit your fstab to mount it under a catalogue like : "/my_partition"

This way it will show in computer and in filesytem (under /my_partition) while it will not show up in your desktop.

PS: My fat32 partition used for multimedia storing is like:
    /dev/sda4       /winux          vfat    defaults,utf8,umask=007,gid=46 0       1

---

### Post by gommle on 2006-09-18
gconf-editor
Apps -> nautlis -> Desktop -> toggle volumes_visible.

---

### Post by domm on 2006-09-18
@turbojugend_gr
Tanke for your quick reply.
Unfortunatly, this doesn't work for me. It's just like mounting somewhere else than /media. No icons at all :( 

@gommle
> **gommle said:**
> gconf-editor
Apps -> nautlis -> Desktop -> toggle volumes_visible.

Did you read what I wrote? 
"Disabling "volumes_visible" in gconf is no option for me since I want removable medias to pop up on the desktop."

But thanks anyway!

---

### Post by turbojugend_gr on 2006-09-18
> @turbojugend_gr
unfortunatly, this doesn't work for me. It's just like mounting somewhere esle than /media. No icons at all

Have you tried it, cause in this case the volumes show in computer, as I said before, and as you asked for...

---

### Post by turbojugend_gr on 2006-09-18
BTW users is a value to define the desired group for "gid" parametre (the permissions in other words), while user is a parametre itslef used to provide  all users in the same group defined for "gid" can mount-unmount the volume.

---

### Post by domm on 2006-09-18
I tried it (even rebooted twice now). But no icons:
fstab entry looks like this:
```

/dev/sda4       /share          ext3    defaults        0       1

```


> **turbojugend_gr said:**
> BTW users is a value to define the desired group for "gid" parametre (the permissions in other words), while user is a parametre itslef used to provide  all users in the same group defined for "gid" can mount-unmount the volume.

thanks for the clarification!

---

### Post by turbojugend_gr on 2006-09-18
You need to add ,the following parametres: gid=users,user. Then it will show up. Do it quickly plz and tell me if it worked... IU am in a hurry...lmbao

---

### Post by turbojugend_gr on 2006-09-18
BTW if you wish to remount all your fstab listed drives without rebooting do in a terminal: sudo mount -a

---

### Post by domm on 2006-09-18
> **turbojugend_gr said:**
> You need to add ,the following parametres: gid=users,user. Then it will show up. Do it quickly plz and tell me if it worked... IU am in a hurry...lmbao

Damn.. That worked!
Great, thank you man!

EDIT: Ups... no - it didn't

---

### Post by turbojugend_gr on 2006-09-18
> **domm said:**
> Damn.. That worked!
Great, thank you man!

Any time m8. You see inorder to appear in computer there must be a reason (haveing the ability to mount-unmount will do the trick - so your BTW question was also your answer!)

PS: The thing is that I told you that a while ago, you see that's why I posted my fstab line (but then I noticed you was asking for that part so I had to explain first - you can make out why from my signature)

---

### Post by domm on 2006-09-18
> **domm said:**
> Damn.. That worked!
Great, thank you man!

I correct: It partly worked....
The Icons show up in the desired locations BUT I can't mount the partition anymore
```

EXT3-fs: Unrecognized mount option "gid=100"

```
th gid,uid options are not valid on ext3 filesystems (they actually support real file-permissions, so these options aren't necessary)


EDIT:
Actually, i think it only worked because the partition got not mounted. As when using the "noauto" option.
This is the same for my ntfs windows partition:
```
/dev/sda2   /windows    ntfs  noauto,user,nls=utf8,umask=0222 0    0
```
=> Icons as desired
```
/dev/sda2   /windows    ntfs gid=100,user,nls=utf8,umask=0222 0  0
```
=> No icons

For now icons only show up when the partition is not mounted at boot time.


sad.. but hey

---

### Post by turbojugend_gr on 2006-09-18
Hmm I see, well, did you remove the default parametre? If you did put it back on.

If you didn't. plz post your fstab file so I will hit back with a possibly working version of it.

---

### Post by domm on 2006-09-18
Here's my fstab. The defaults parameter doesn't seem to make a difference -as far as i can see.

```
/dev/sda1   /     ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /mnt/windows    ntfs    defaults,noauto,user,nls=utf8,umask=0222 0    0
#/dev/sda2      /windows        ntfs    defaults,gid=users,user,nls=utf8,umask=0222 0    0
/dev/sda4       /share      ext3    defaults,user   0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
#GMX Mediacenter
https://mediacenter.gmx.net    /media/gmx    davfs   user,noauto   0     0

```

---

### Post by turbojugend_gr on 2006-09-18
Well from what I c it is not a problem with your fstab, for instance /share partition is as it should be , yet it doesn't appear in computer as it would in my system (and in a normal ubuntu machine in general) or that is what I understand from your previous posts... SO I admit I am useless... I can't make out a thing! Maybe if you mention using or doing anything unsusual in your machine? Have you changed anything in your nautilus bahaviour?

At the moment i can only take a long shot: Open your gconf-editor and go to desktop>gnome>volume_manager and make sure automount_drives and automount_media are checked then see if the drives appear (maybe restart first). I don't believe that's the case most propably it is sth else that my mind can't forsee.

PS: I have issued all my knowledge on this subject, everything I know it might obstruct the drives from appearing I have told you (the gconf-editor thing is my last shot propably), and even my google searches haven't reach any output on your problem. I hope someone else can step in and put his wisdom over your issue. :(

---

### Post by domm on 2006-09-19
Well - wanted to let you know I figured out how to change what mounts are appearing in Computer&Desktop.

While this is not the problem I was complaining about (I want a partition to appear ONLY in Computer and not in computer & Desktop) I thought it might be useful for someone else too - though the /media exception seems quite handy.

As described in [https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/34886]("https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/34886")
one needs to modify the "usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi"
The relating part is:
```

<match key="volume.is_mounted" bool="true">
  <!-- Show /media/ drives -->
  <match key="volume.mount_point" compare_gt="/media">
      <match key="volume.mount_point" compare_lt="/media0">
	  <merge key="volume.ignore" type="bool">false</merge>
      </match>
  </match>
</match>

```

Maby I can figure out how the exception for the root partition and the "Filesystem" icon (which is the kinf of behavior I want for my other partition) is done.

I'll let you know then;)


Edit:
What some people might want is that their Windows partitions alwayas show up regardless of where they are mounted. To accompish this just add the following in 
"usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi" befor or after the above mentioned lines (for the /media exception):

```

<!-- Show windows drives -->
 <match key="volume.fstype" string="vfat">
     <merge key="volume.ignore" type="bool">false</merge>
 </match>
 <match key="volume.fstype" string="ntfs">
     <merge key="volume.ignore" type="bool">false</merge>
 </match>

```

---

