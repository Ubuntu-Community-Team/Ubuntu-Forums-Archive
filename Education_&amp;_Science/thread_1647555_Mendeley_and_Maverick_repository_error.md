---
title: "Mendeley and Maverick repository error"
date: 2010-12-17
forum: Education &amp; Science
---

### Post by myotis on 2010-12-17
Is anyone having problems using the Mendeley repository with Maverick.

I am getting an error

Failed to fetch [http://www.mendeley.com/repositories/xUbuntu_10.10/Sources.gz](http://www.mendeley.com/repositories/xUbuntu_10.10/Sources.gz)  404
  Not Found
Some index files failed to download, they have been ignored, or old ones used
instead.

The lines in my sources.list are

deb [http://www.mendeley.com/repositories/xUbuntu_10.10](http://www.mendeley.com/repositories/xUbuntu_10.10) /
deb-src [http://www.mendeley.com/repositories/xUbuntu_10.10](http://www.mendeley.com/repositories/xUbuntu_10.10) /

I contacted Mendeley over a week ago now, and they asked me to send my sources.list file to check, but I haven't had a reply since I sent it or to my email chasing it up.

Has anyone any idea what the problem might be.

Thanks,

Graham

---

### Post by sikander3786 on 2010-12-17
Not in a clear state of mind at the moment. *Forestpiskie* brought me back... :-)

deb-src is giving an error. You can safely disable that for the moment. I have tested the other repository in my sources.list and that is working fine.

[s]Is mandeley open source? If not, deb-src is definitely supposed to return an error ;-)

And the deb sources entry is not returning an error in apt-get update so I hope that is just working fine.And the address is opening fine in my browser too.[/s]

Just place a # in the beginning of deb-src line or remove the complete line and you should be able to install from mendeleys' repos.

---

### Post by Elfy on 2010-12-17
> Is mandeley open source? If not, deb-src is definitely supposed to return an errorPardon? that would just be the sources ... 

The sources.gz does not open here.

The lines look ok to me though.

---

### Post by myotis on 2010-12-17
> **sikander3786 said:**
> 

Just place a # in the beginning of deb-src line or remove the complete line and you should be able to install from mendeleys' repos.

Thanks, now done and downloaded.

What is the down side of not having the src line active, I just copied the other line from the Mendeley web page and Ubuntu added the src line.

Graham

---

### Post by Elfy on 2010-12-17
deb-src

[http://ubuntuforums.org/showpost.php?p=9752784&postcount=5](http://ubuntuforums.org/showpost.php?p=9752784&postcount=5)

---

### Post by myotis on 2010-12-17
> **forestpiskie said:**
> deb-src

[http://ubuntuforums.org/showpost.php?p=9752784&postcount=5](http://ubuntuforums.org/showpost.php?p=9752784&postcount=5)

Thanks,

Graham

---

