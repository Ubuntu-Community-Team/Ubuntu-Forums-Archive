---
title: "Scaling broken after update (16.04 LTS)"
date: 2018-02-19
forum: Desktop Environments
---

### Post by thermostat on 2018-02-19
Dear forum members,

My system is Ubuntu 16.04 LTS (Unity) on a computer with a 14'' screen and a 1920 x 1080 resolution. Windows used to be displayed just fine using a scaling factor of 1.5, equivalent with specifying a resolution of 144 dpi.

After a system update that I performed today, this configuration appears to be broken. First, I have attached two screenshots below with respective scalings of 1.0 and 1.38. In the latter case, the fonts and icons are larger, but the windows and their content are "normal" (as one would expect).

 [ATTACH=CONFIG]278591[/ATTACH][ATTACH=CONFIG]278590[/ATTACH]

Now compare this with a scaling factor of 1.5. The display settings window suddenly fills the entire screen (before the update, it used to have the same size as in the screenshots above). Likewise, the Wikipedia globe in the browser now fills the entire page (at 100% zoom), whereas the page should be displayed as in the images with smaller scalings.

[ATTACH=CONFIG]278589[/ATTACH][ATTACH=CONFIG]278588[/ATTACH]

Does anyone know what is going wrong? Is it even a known issue?

Below is an excerpt from /var/log/apt/history.log for the recent update that (apparently) broke it.

```
Start-Date: 2018-02-19  22:02:28
Commandline: apt upgrade
Requested-By:
Upgrade: unity-schemas:amd64 (7.4.0+16.04.20160906-0ubuntu1, 7.4.5+16.04.20171201.3), compiz-plugins-default:amd64 (1:0.9.12.2+16.04.20160823-0ubuntu1, 1:0.9.12.3+16.04.20171116-0ubuntu1), libdecoration0:amd64 (1:0.9.12.2+16.04.20160823-0ubuntu1, 1:0.9.12.3+16.04.20171116-0ubuntu1), libunity-protocol-private0:amd64 (7.1.4+16.04.20160701-0ubuntu1, 7.1.4+16.04.20180209.1-0ubuntu1), gir1.2-unity-5.0:amd64 (7.1.4+16.04.20160701-0ubuntu1, 7.1.4+16.04.20180209.1-0ubuntu1), libnuma1:amd64 (2.0.11-1ubuntu1, 2.0.11-1ubuntu1.1), unity-scopes-runner:amd64 (7.1.4+16.04.20160701-0ubuntu1, 7.1.4+16.04.20180209.1-0ubuntu1), unity:amd64 (7.4.0+16.04.20160906-0ubuntu1, 7.4.5+16.04.20171201.3), unity-services:amd64 (7.4.0+16.04.20160906-0ubuntu1, 7.4.5+16.04.20171201.3), libunity-core-6.0-9:amd64 (7.4.0+16.04.20160906-0ubuntu1, 7.4.5+16.04.20171201.3), libunity9:amd64 (7.1.4+16.04.20160701-0ubuntu1, 7.1.4+16.04.20180209.1-0ubuntu1), compiz-gnome:amd64 (1:0.9.12.2+16.04.20160823-0ubuntu1, 1:0.9.12.3+16.04.20171116-0ubuntu1), libcompizconfig0:amd64 (1:0.9.12.2+16.04.20160823-0ubuntu1, 1:0.9.12.3+16.04.20171116-0ubuntu1), compiz:amd64 (1:0.9.12.2+16.04.20160823-0ubuntu1, 1:0.9.12.3+16.04.20171116-0ubuntu1), libunity-scopes-json-def-desktop:amd64 (7.1.4+16.04.20160701-0ubuntu1, 7.1.4+16.04.20180209.1-0ubuntu1), compiz-core:amd64 (1:0.9.12.2+16.04.20160823-0ubuntu1, 1:0.9.12.3+16.04.20171116-0ubuntu1)
End-Date: 2018-02-19  22:02:34
```

---

### Post by thermostat on 2018-02-21
Update: this issue has been reported as a bug by other users. Hopefully the developers will resolve this.
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1750273](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1750273)

---

