---
title: "download_and_compile.sh to build flightgear always start &quot;big&quot; download from start"
date: 2010-07-10
forum: Gaming &amp; Leisure
---

### Post by scotty64 on 2010-07-10
I am trying to build flightgear 2 with the download_and_compile.sh build script. I am using the following options in order to avoid rebuilding the libraries at any restart:
./download_and_compile.sh -r n ALL
My problem is that when I restart the script it always says "initializing empty git repository" and then starts the nervewrecking big fgfs download again and the hundreds of megabytes I downloaded before are gone.
Is there a way to tell this script to simply continue the download where it stopped ?

---

### Post by d3v1150m471c on 2010-07-10
have you ever actually let it finish downloading?

---

### Post by scotty64 on 2010-07-10
> **d3v1150m471c said:**
> have you ever actually let it finish downloading?

No. The download seems to be of about 2Gb and that takes hours with our slow broadband connection here on the countryside. I just do not want the machine to run overnight and sometimes I need the bandwidth for other things.
This why I am asking if there is any way to split this download across multiple sessions.

---

