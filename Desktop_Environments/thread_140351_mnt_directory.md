---
title: "mnt directory"
date: 2006-03-06
forum: Desktop Environments
---

### Post by aqualad on 2006-03-06
Yesterday I attempted to update my kernel but something went wrong and I was faced with the decision to format.  I formatted, but when I reinstalled my directories got changed a little, so now my playlist (which is still intact luckily on another drive) is off.  The problem is that before the format I had a folder in /mnt called "shared".  The folder "shared" pointed to another partition, which is now called hdb6.  I was wondering if there was any way to map it so that mnt/shared points to hdb6?  If I can do that then my playlist will be fine :)  thanks

---

### Post by Sutekh on 2006-03-06
You should create a 'symbolic link'

A symbolic link is basically a shortcut

This will require some terminal work

```
[COLOR="Navy"]cd /mnt[/COLOR]
sudo [COLOR="Red"]ln -s[/COLOR] [COLOR="Green"]/media/hda6[/COLOR] [COLOR="DarkOrchid"]shared[/COLOR]

```
 - [COLOR="Navy"]cd /mnt[/COLOR] - will change to the /mnt folder

 - [COLOR="Red"]ln -s[/COLOR] - will create the symbolic link

 - [COLOR="Green"]/media/hda6[/COLOR] - is the location of the folder with your stuff.  I don't know exactly where it is mounted, but you can determine this using ```
cat /etc/fstab
``` - Look for the entry that looks something like this (and change if appropriate) ```
/dev/hda6 [COLOR="Green"]/media/hda6[/COLOR] .....
```
 - If it is not in there, you will need to set that up too.

 - [COLOR="DarkOrchid"]shared[/COLOR] - this is the 'name' of the link.  If you called it 'shared' then anything that looks in /mnt/shared will be directed to hda6

---

### Post by aqualad on 2006-03-06
thank you :) now let's just hope that it doesn't require the command every reboot (but i believe that's the point of editting fstab)

thanks again

---

### Post by Sutekh on 2006-03-06
What did you do? (no need to edit the fstab, unless there wasn't an entry for hda6)  

The symbolic link will always be there unless you delete it.

---

