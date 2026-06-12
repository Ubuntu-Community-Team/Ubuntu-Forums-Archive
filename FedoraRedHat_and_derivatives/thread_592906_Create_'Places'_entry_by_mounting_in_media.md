---
title: "Create 'Places' entry by mounting in /media"
date: 2007-10-26
forum: Fedora/RedHat and derivatives
---

### Post by hrod beraht on 2007-10-26
If I mount a network smbfs/cifs share under /media in Ubuntu, it automatically places a disk icon on the desktop and under Places (and goes away when you unmount it).

How can I make that happen in Fedora 7?

Bob :)

---

### Post by pelle.k on 2007-10-28
The only distro i've seen this behavior is in ubuntu, and btw i friggin love it. Since you asked, i did some research and i found a wiki entry;
[https://wiki.ubuntu.com/MediaOnDesktop](https://wiki.ubuntu.com/MediaOnDesktop)

and this this old bugreport;
[https://launchpad.net/ubuntu/+source/gnome-vfs2/+bug/34886](https://launchpad.net/ubuntu/+source/gnome-vfs2/+bug/34886)

And this led me to belive this behaviour is in;
/usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi

Specifically;
```
     <!-- Ignore fixed partitions which are not mounted in /media -->
     <match key="@block.storage_device:storage.hotpluggable" bool="false">
       <match key="@block.storage_device:storage.removable" bool="false">
         <match key="volume.is_mounted" bool="true">
           <merge key="volume.ignore" type="bool">true</merge>
           <!-- Show /media/ drives -->
           <match key="volume.mount_point" compare_gt="/media">
             <match key="volume.mount_point" compare_lt="/media0">
               <merge key="volume.ignore" type="bool">false</merge>
             </match>
           </match>
         </match>
       </match>
     </match>

```

Feel free to try it out (you might have to restart the computer), and report back if it works. Otherwise i will try it out when i have some time to spare...

---

