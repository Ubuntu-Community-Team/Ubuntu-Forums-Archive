---
title: "Desktop problems after latest update"
date: 2012-09-24
forum: Desktop Environments
---

### Post by raroth on 2012-09-24
Was tickled by Update Manager yesterday that updates were available for my install of 12.04.  I performed the update this morning and now have multiple problems:

1.  Launcher icons no longer adjustable;  the control within Settings/Appearance no longer contains an adjustment for Launcher icon size.
2.  The mouse cursor has gone "flaky":  when hovering over icon or link it flutters in and out, sometimes to the point where I lose it from view altogether even though it is there when I click.
3.  When booting up and logging in, the monitor goes white immediately after I execute my password.  Then the usual screen setups begin. Here are the first several lines from dpkg log:

2012-09-24 02:18:20 startup archives unpack
2012-09-24 02:18:24 install linux-image-3.2.0-31-generic <none> 3.2.0-31.50
2012-09-24 02:18:24 status half-installed linux-image-3.2.0-31-generic 3.2.0-31.50
2012-09-24 02:18:42 status unpacked linux-image-3.2.0-31-generic 3.2.0-31.50
2012-09-24 02:18:43 status unpacked linux-image-3.2.0-31-generic 3.2.0-31.50
2012-09-24 02:18:46 upgrade libgs9 9.05~dfsg-0ubuntu4.1 9.05~dfsg-0ubuntu4.2
2012-09-24 02:18:46 status half-configured libgs9 9.05~dfsg-0ubuntu4.1
2012-09-24 02:18:46 status unpacked libgs9 9.05~dfsg-0ubuntu4.1
2012-09-24 02:18:46 status half-installed libgs9 9.05~dfsg-0ubuntu4.1
2012-09-24 02:18:47 status half-installed libgs9 9.05~dfsg-0ubuntu4.1
2012-09-24 02:18:47 status unpacked libgs9 9.05~dfsg-0ubuntu4.2
2012-09-24 02:18:47 status unpacked libgs9 9.05~dfsg-0ubuntu4.2
2012-09-24 02:18:50 upgrade libgs9-common 9.05~dfsg-0ubuntu4.1 9.05~dfsg-0ubuntu4.2
2012-09-24 02:18:50 status half-configured libgs9-common 9.05~dfsg-0ubuntu4.1
2012-09-24 02:18:51 status unpacked libgs9-common 9.05~dfsg-0ubuntu4.1
2012-09-24 02:18:53 status half-installed libgs9-common 9.05~dfsg-0ubuntu4.1
2012-09-24 02:18:57 status half-installed libgs9-common 9.05~dfsg-0ubuntu4.1

Any help in sorting this out would be appreciated!

Thanks,
****

---

### Post by raroth on 2012-09-24
Well, the problem was the video driver.

When in its wisdom Update Center did its stuff, it replaced the proprietary Nvidia driver with an OSS version that just plain doesn't work properly (that's why I went with the proprietary version to begin with)!

Don't know why this update acted differently than previous updates, but I now have the symptoms and solution burnished in what is left for my brain.

ttfn,
****

---

