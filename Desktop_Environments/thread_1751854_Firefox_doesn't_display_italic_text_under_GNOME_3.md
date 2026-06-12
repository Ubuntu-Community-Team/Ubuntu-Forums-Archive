---
title: "Firefox doesn't display italic text under GNOME 3"
date: 2011-05-07
forum: Desktop Environments
---

### Post by rezonatix3 on 2011-05-07
I am posting this under "Desktop Environments" because this does not occur under Unity, nor under KDE (tested with Kubuntu live-CD).

I run Firefox 4.0.1 on Ubuntu 11.04, having installed GNOME 3 via PPA. The following HTML file is not displayed correctly in Firefox:

```

<html>
  <body>
    <p>This is <em>italic text</em>.</p>
  </body>
</html>

```
Firefox displays this file as:

> 
This is .

Oddly enough, *italic text* works just fine here on this forum. It appears to be a font issue.

---

### Post by rezonatix3 on 2011-05-07
As it turns out, the DejaVu fonts were not properly installed: I had only ttf-dejavu-core, not ttf-dejavu-extra. The following installs both packages and fixes the problem:

```

sudo apt-get remove ttf-dejavu-core
sudo apt-get install ttf-dejavu

```

---

