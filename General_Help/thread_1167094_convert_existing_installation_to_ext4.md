---
title: "convert existing installation to ext4?"
date: 2009-05-22
forum: General Help
---

### Post by alexweber15 on 2009-05-22
I never had a choice (used 'automatic' install options)... apparently ext4 has better performance so I figured I'd give it a shot.

I'm dual booting with windows so it doesn't make a difference what file system it is from that standpoint.

First off: is it worth it?  (the performance and other benefits?)
And: is it possible to "convert" my only partition from ext3 to ext4?

thanks!

Alex

---

### Post by kellemes on 2009-05-22
> **alexweber15 said:**
> I never had a choice (used 'automatic' install options)... apparently ext4 has better performance so I figured I'd give it a shot.

I'm dual booting with windows so it doesn't make a difference what file system it is from that standpoint.

First off: is it worth it?  (the performance and other benefits?)
And: is it possible to "convert" my only partition from ext3 to ext4?

thanks!

Alex

Is it worth it?
No, you won't notice better performance, I don't anyway.

Possible to convert?
Don't know, well, don't know if it's possible without losing data. I wouldn't gamble on it myself.

If there is no special reason to go ext4 just wait until it's the default filesystem, nothing wrong with ext3.

[More info..]("http://ubuntuforums.org/showthread.php?t=1133719")

---

### Post by ibuclaw on 2009-05-22
Yes, it is possible to convert.

But it is not recommended in the kernel that was released with Jaunty. As if you have a particularly unstable system, you may find that configuration files in your home directory will zero out.

---

### Post by logos34 on 2009-05-22
> **alexweber15 said:**
> I'm dual booting with windows so it doesn't make a difference what file system it is from that standpoint.

First off: is it worth it?  (the performance and other benefits?)
And: is it possible to "convert" my only partition from ext3 to ext4?


actually it does make a difference for people using the fs-driver to read+write to ext3 linux--the driver doesn't (yet) support ext4, so you wouldn't be able to access linux files from win2k/xp/vista

I'd wait a while to convert, till the [bugs are ironed out (-->#3 + #4)]("http://www.ubuntu.com/getubuntu/releasenotes/904#Other%20known%20issues")

---

### Post by alexweber15 on 2009-05-22
thanks for the replies! :)

oh and I didn't even know I could access ext3 from XP, ill have to read up on that...

i guess if it aint broke dont fix it! ;)

---

