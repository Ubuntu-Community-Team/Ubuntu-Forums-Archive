---
title: "OpenOffice in Hoary"
date: 2005-09-27
forum: Desktop Environments
---

### Post by Curlydave on 2005-09-27
The version of OO that comes with hoary is rather useless for me as it can't read .odt files. This is because it is an older version that doesn't support the new version. There is a new version in synaptec, but it's retarded and is definitely not OO2. It's really ugly and ghettofied, and while it says it can open .odt files, it crashes when I try to open one. 

Is there a way to get the real OO2 beta on hoary? On their site theres an easy windows installer, but no linux binaries. I followed this tutorial that downloads and unpacks it, and it says you need to move this .gz file into your ~/openoffice2 directory. I did this just like it says, but it still bitches, and as a result I have no way of accessing the oo2 programs I just installed. What's up? How can I get OO2? Thanks! :)

---

### Post by RikoW on 2005-09-27
Hi,

you get just get the package from openoffice.org.
if you unpack the tar file, you get a directory with rpm.

use *alien* to convert rpm to deb. 
use *dpkg -i *.deb* to install

worked fine for me. However, I find OOo2 still kind of unstable.

Post again, if you need more details.

Cheers,

              Riko

---

### Post by Zelut on 2005-09-27
I had the same problem last nite.  I made sure I had the latest repositories and it installed the non-ghetto version but it still didn't open my .odt file.  I had to open it on my notebook that is running 5.10 for that to work.  So far that is the only solution I have found for that issue.  5.10

---

