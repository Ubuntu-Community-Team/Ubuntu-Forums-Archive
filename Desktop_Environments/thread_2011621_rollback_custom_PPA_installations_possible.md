---
title: "rollback custom PPA installations possible?"
date: 2012-06-27
forum: Desktop Environments
---

### Post by bravegag on 2012-06-27
Hello,

I had to recently install the X-updates PPA in order to get the driver for my nVidia 670 card installed and working properly. The problem is that as side effect and after receiving all the accompanying updates for this PPA I get Segmentation Faults and my applications (Scientific HP computing benchmarking) do not work properly anymore.

Is there a way to rollback the custom PPA as if they were not installed and the corresponding updates rolled back? 

Many TIA,
Best regards,
Giovanni

---

### Post by LarsKongo on 2012-06-27
sudo apt-get install ppa-purge
sudo ppa-purge ppa:repository-name/subdirectory

Should fix it.

---

