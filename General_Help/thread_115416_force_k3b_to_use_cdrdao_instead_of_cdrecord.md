---
title: "force k3b to use cdrdao instead of cdrecord"
date: 2006-01-10
forum: General Help
---

### Post by RikoW on 2006-01-10
Dear all,

is there a way to do the above?

Background is the following. I used to have a cd-rw drive which was working fine with k3b. As far as I remember, whenever I burned a data or iso cd, k3b would use cdrdao to do the job.

Now, I have swapped the (internal) drive (it's a laptop) with a DVD-RW drive SONY DW-Q58A. When I now try to burn anything with k3b, I get an error message that 'high-speed medium is not suitable for the driver' (error log is attached). However, now k3b runs cdrecord and not cdrdao. When trying to burn the CD from the CLI using cdrdao directly, it works.

Any ideas?

Thanks in advance,

          Riko

[ATTACH]5254[/ATTACH]

---

### Post by az on 2006-01-10
[QUOTE=RikoW]Dear all,

is there a way to do the above?

Background is the following. I used to have a cd-rw drive which was working fine with k3b. As far as I remember, whenever I burned a data or iso cd, k3b would use cdrdao to do the job.

Now, I have swapped the (internal) drive (it's a laptop) with a DVD-RW drive SONY DW-Q58A. When I now try to burn anything with k3b, I get an error message that 'high-speed medium is not suitable for the driver' (error log is attached). However, now k3b runs cdrecord and not cdrdao. When trying to burn the CD from the CLI using cdrdao directly, it works.

Any ideas?

Thanks in advance,

          Riko

[ATTACH]5254[/ATTACH][/QUOTE]

I am not in front of K3B at the moment, but I am certain there is a configuration where you tell it to use cdrdao for a task instead of cdrecord.

---

### Post by lysis on 2006-01-10
sudo apt-get install cdrdao    k3b will automatically use cdrdao with root priveledges as long as it's installed.  on first run without cdrdao as long as you DON'T check that "do not show this msg again" it'll let you know it prefers it. =)

---

### Post by RikoW on 2006-01-10
Oh, indeed, after looking for the 5th time, I finally found it.

Under the "Writing" tab of the "configure k3b" menu is a little check box which says "Manual writing application selection". Selecting that, you can indeed select the application in the burn dialog.

Thanks for the encouragement, azz,  to look one more time

Cheers,

                Riko

---

