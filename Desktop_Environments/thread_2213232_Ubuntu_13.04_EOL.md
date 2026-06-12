---
title: "Ubuntu 13.04 EOL"
date: 2014-03-25
forum: Desktop Environments
---

### Post by nibal on 2014-03-25
According to [http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life), Ubuntu 13.04 is just past its EOL.
I still see it supported in [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Can i get from somewhere a x64 image of 13.04? A rather sudden business need for 13.04 has arisen :-(

TIA

---

### Post by westie457 on 2014-03-25
Take a look here. [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by deadflowr on 2014-03-25
You can a 13.04 image from the old-release link in the link you posted.

As well, you would have to change all the sources.list entry in /etc/apt/sources.list to eflect the old-release archives, instead of the normal archives.
Otherwise you won't be able to grab the dead packages using apt-get, but instead would need to install the packages more manually.

Anyway, I advise against, but it's your choice.

Edit: It seems they haven't moved raring yet, oddly.
Look here
[http://releases.ubuntu.com/raring/](http://releases.ubuntu.com/raring/)

---

### Post by nibal on 2014-03-25
> **deadflowr said:**
> You can a 13.04 image from the old-release link in the link you posted.

As well, you would have to change all the sources.list entry in /etc/apt/sources.list to eflect the old-release archives, instead of the normal archives.
Otherwise you won't be able to grab the dead packages using apt-get, but instead would need to install the packages more manually.

Anyway, I advise against, but it's your choice.

Edit: It seems they haven't moved raring yet, oddly.
Look here
[http://releases.ubuntu.com/raring/](http://releases.ubuntu.com/raring/)

Thank you so much. Just what the doctor ordered ;-)

---

### Post by grahammechanical on 2014-03-25
package.ubuntu.com is only providing information about the packages in the relevant repositories. The repositories of releases that have reached End Of Life are closed but not deleted. They are moved to a different location but those packages are no longer upgraded (supported in that sense). And in time the repositories are deleted. For this reason you do not see 10.10, 11.04 and 11.10 or anything older than 10.04 in that list.

Regards.

---

