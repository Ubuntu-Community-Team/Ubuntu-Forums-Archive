---
title: "DVD trouble"
date: 2006-07-31
forum: Desktop Environments
---

### Post by spahn on 2006-07-31
I am having trouble getting DVDs to play in Dapper-
i have done some research

[http://www.ubuntuforums.org/showthread.php?t=220564&highlight=Play+DVDs+Dapper](http://www.ubuntuforums.org/showthread.php?t=220564&highlight=Play+DVDs+Dapper)

and installed this codec
	- libxine-extracodecs

and i was not able to find the libdvdcss codec, 	
[http://www.ubuntuforums.org/showthread.php?t=217213](http://www.ubuntuforums.org/showthread.php?t=217213)	
	- libdvdcss

the closest i found was libdvdread3 and libdvdread3-dev

i tried searching here the wiki ([http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)) and couldn't find anything.

After installing all the plugins that i could from [http://www.ubuntuforums.org/showthread.php?t=98274](http://www.ubuntuforums.org/showthread.php?t=98274)
i was able to get the FBI warning to play but nothing else...

Seems like i had this trouble with Breezy, but i can't remember how i fixed it.

Any ideas??

---

### Post by x64Jimbo on 2006-07-31
Try this:
[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

---

### Post by spahn on 2006-07-31
Excellent!
My browser history shows that i went to that page yesterday, but i must have missed the command

```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

Thank you

---

### Post by x64Jimbo on 2006-07-31
No worries. :) Just pay it forward. When you get enough experience to start helping others, do so. I only learned what I know from others and I'm paying it forward as the saying goes.

---

