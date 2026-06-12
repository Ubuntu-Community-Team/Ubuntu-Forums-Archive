---
title: "Help installing e17L can't find zlib.h"
date: 2008-12-19
forum: Desktop Environments
---

### Post by maphco on 2008-12-19
I'm trying to install Enlightenment DR17 and I'm running into a couple problems.

I went to [http://download.enlightenment.org/releases/](http://download.enlightenment.org/releases/) and downloaded the newest release and saved it to my desktop.

Unpacked it to my desktop and tried to run ./configure

Didn't work because it seems I didn't have g++ installed so I installed that.

Now when I run it the last couple lines of ./configure gives me:

checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no
configure: error: "Cannot find zlib.h. Make sure your CFLAGS environment variable contains include lines for the location of this file"


So I googled the file zlib.h and came to a website [http://www.koders.com/cpp/fid250AD067FF17C9575FE9AA5F20F486D60624AAEE.aspx?s=cdef%3Atree](http://www.koders.com/cpp/fid250AD067FF17C9575FE9AA5F20F486D60624AAEE.aspx?s=cdef%3Atree)   and downloaded the file to my desktop  to see if it fixed that problem.  But it didn't :(

Anyone know how I should advance at this point or now a different way to get Enlightenment DR17 hooked up?

---

### Post by Tim Sharitt on 2008-12-19
Try moving it to /usr/include, thats where I found it on my system.

---

### Post by maphco on 2008-12-19
Well, I moved the file there and got the same error back. Where is the CFLAGS variable? I found a line

WIN32_CFLAGS=""

in the configure file so I changed the line to

WIN32_CFLAGS="/usr/include"

but that didn't work.

EDIT: Sorry, that was in the configure.in file. But still.

---

### Post by andrew.46 on 2008-12-19
Hi,

Perhaps try:

```
sudo apt-get install zlib1g-dev
```

and this may get you out of trouble.

  Andrew

---

### Post by maphco on 2008-12-19
I got that installed, and the other package after that that it said I needed.  So now I'm just trying to get it to show up as a session choice at login.

---

### Post by andrew.46 on 2008-12-19
Hi maphco,

Do you know that there is quite an active thread devoted to e17 on these forums? Address is:

[http://ubuntuforums.org/showthread.php?t=916690](http://ubuntuforums.org/showthread.php?t=916690)

All the best,

  Andrew

---

