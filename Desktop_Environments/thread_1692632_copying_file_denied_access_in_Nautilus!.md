---
title: "copying file denied access in Nautilus!"
date: 2011-02-21
forum: Desktop Environments
---

### Post by goosefartfan on 2011-02-21
Well, I'm having big headaches trying to get my amd-64 to play flash player sites like YOUTUBE with firefox.
I'm trying to copy the adobe player "square" which is supposed to work for 64 bit cpus.
the file I'm trying to copy is under /home/username/downloads/filename
I'm trying to copy it to /usr/lib/firefox-addons (forgive misspelling)

I'm doing this under natilus, with root privileges

I'm getting permission denied.

for fun, I noticed that the /home/ etc... is owned by me (admin).
the /usr/lib isn't showing any owners or permissions.

Please explain to me how I can copy the file over so I can to try to watch videos on the net.

a frustrated thanks............:(

---

### Post by mikewhatever on 2011-02-21
Naturally, /usr/lib is owned by root, and if you get a 'permission denied' error, then Nautilus is probably not run as root.

---

### Post by inobe on 2011-02-21
just use flash aid and call it a day.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

big thanks goes out to lovinglinux

---

### Post by gordintoronto on 2011-02-21
Why are you jerking around with /root folders?

Copy the video to your videos folder!

---

### Post by pafufta503 on 2011-02-21
> **inobe said:**
> just use flash aid and call it a day.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

big thanks goes out to lovinglinux

flashaid is a frakking miracle!

---

### Post by Copper Bezel on 2011-02-22
Let's not talk about this as if it's a Flash problem. Dude has an unnukeable folder. That's the thing to address first. (I mean, unless the Flash Aid bit already helped with that.)

> Why are you jerking around with /root folders?

Because he's modifying installed software? Reading comprehension is key! = )

> Naturally, /usr/lib is owned by root, and if you get a 'permission denied' error, then Nautilus is probably not run as root.

Except that he specifically said that he was running Nautilus as root and even checked the permissions of other folders owned by root, but this particular one isn't displaying permissions info at all.

Hmm. Try checking the permissions from command line, yeah?

---

### Post by goosefartfan on 2011-02-22
[SIZE=3]**Thanks a million to** inobe and pafufta503 for the flash aid tip!  It works!!:guitar:

gordintoronto, didn't you play both lead roles in Dumb and Dumber??

Copper Bezel, thanks for the  intelligent response, how do I  check from command line?[/SIZE]

---

### Post by Copper Bezel on 2011-02-22
```
ls -l "your path"
```

= )

Edit: For comparison, when I run this on /usr/lib, all subdirectories and files come up as owned by root (as they should.)

---

### Post by goosefartfan on 2011-02-22
maybe I should have posted this in the absolute beginner forum:(

anyway, here's the results!
tatti@tatti-desktop:/$ ls -l
total 96
drwxr-xr-x   2 root root  4096 2011-02-17 18:36 bin
drwxr-xr-x   3 root root  4096 2011-02-17 19:35 boot
drwxr-xr-x   2 root root  4096 2011-02-17 18:00 cdrom
drwxr-xr-x  16 root root  4080 2011-02-22 02:32 dev
drwxr-xr-x 135 root root 12288 2011-02-22 11:31 etc
drwxr-xr-x   7 root root  4096 2011-02-17 18:22 home
lrwxrwxrwx   1 root root    33 2011-02-17 18:43 initrd.img -> boot/initrd.img-2.6.32-28-generic
lrwxrwxrwx   1 root root    33 2011-02-17 18:04 initrd.img.old -> boot/initrd.img-2.6.32-24-generic
drwxr-xr-x  17 root root 12288 2011-02-22 00:00 lib
lrwxrwxrwx   1 root root     4 2011-02-17 17:47 lib64 -> /lib
drwx------   2 root root 16384 2011-02-17 17:46 lost+found
drwxr-xr-x   3 root root  4096 2011-02-21 00:46 media
drwxr-xr-x   2 root root  4096 2010-04-23 13:23 mnt
drwxr-xr-x   2 root root  4096 2010-08-16 12:53 opt
dr-xr-xr-x 227 root root     0 2011-02-21 14:27 proc
drwx------  14 root root  4096 2011-02-22 00:21 root
drwxr-xr-x   2 root root  4096 2011-02-17 18:46 sbin
drwxr-xr-x   2 root root  4096 2009-12-06 00:25 selinux
drwxr-xr-x   2 root root  4096 2010-08-16 12:53 srv
drwxr-xr-x  13 root root     0 2011-02-21 14:27 sys
drwxrwxrwt  31 root root  4096 2011-02-22 23:48 tmp
drwxr-xr-x  11 root root  4096 2011-02-17 19:32 usr
drwxr-xr-x  15 root root  4096 2010-08-16 13:08 var
lrwxrwxrwx   1 root root    30 2011-02-17 18:43 vmlinuz -> boot/vmlinuz-2.6.32-28-generic
lrwxrwxrwx   1 root root    30 2011-02-17 18:04 vmlinuz.old -> boot/vmlinuz-2.6.32-24-generic

---

### Post by Copper Bezel on 2011-02-22
No problems there, then. I wonder why Nautilus wasn't displaying the permissions, then...?

---

### Post by asmoore82 on 2011-02-23
I'm missing something here.
I ran 64bit for a good while ~ all I did was install the "nonfree"
flash plugin package from the standard repos — no hocus pocus.

If you're having trouble poking around in system folders, it may be
a good sign that you are not yet ready to do so. Especially if you think
you've got a privileged nautilus open and it's still not working.
Something else is amiss.

---

### Post by goosefartfan on 2011-02-24
you're right about the lack of experience, but I haven't screwed up anything yet....

the firefox problem was resolved!

In terms of my posting of the output, and everything seeming to be OK, there's a great line from an old blues song...
"if it wasn't for bad luck, I wouldn't have no luck at all!"

so, thanks everyone for your help, I'm off to try to research file system permissions in ubuntu!!

---

### Post by debd on 2011-02-24
well, its easy.
i dont know why nobody told ya yet..

press Alt+F2
type in : gksudo nautilus
give ur password

now nautilus will open with root priviages

copy your files.

this should work.

if you still cant play flash in firefox, open nautilus again as root. go to the files where you pasted. right click on them> permissions tab, now set Others permission to Folder permissions: access files
Files permissions: read only

that should work.
let me know if it did. :)

---

### Post by goosefartfan on 2011-02-26
press Alt+F2
type in : gksudo nautilus
give ur password

now nautilus will open with root priviages

copy your files.

this should work.

[SIZE=2]I had done that, and that's why I was frustrated...it was supposed to work!

I did what you said to do at the end, I changed permissions, and it worked!

thanks!
[/SIZE]

---

### Post by inobe on 2011-02-26
been there, did that, we rarely need to go there anymore, enjoy the luxuries, i am! :)

thanks to folks like lovinglinux to take the time and make something so easy to use.

---

