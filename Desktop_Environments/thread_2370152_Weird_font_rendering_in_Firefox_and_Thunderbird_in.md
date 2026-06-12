---
title: "Weird font rendering in Firefox and Thunderbird in Xubnutu 16.04"
date: 2017-08-31
forum: Desktop Environments
---

### Post by ak0ska on 2017-08-31
Hello,

Since last week, the rendering in Firefox (55.02) and Thunderbird became very jerky. For a few samples look here:[ http://imgur.com/a/y0kRw]("http://imgur.com/a/y0kRw"). I tried Firefox with safe mode and issue persists.

Other GTK apps don't have this issue, however these apps were not updated recently. The most recent update log from apt before the issue surface is as follows: 

```

Start-Date: 2017-08-23  14:05:42
Commandline: aptdaemon role='role-commit-packages' sender=':1.167'
Upgrade: atom:amd64 (1.19.2-1~webupd8~1, 1.19.3-1~webupd8~0), ubuntu-drivers-common:amd64 (1:0.4.17.2, 1:0.4.17.3), libxfont1:amd64 (1:1.5.1-1ubuntu0.16.04.1, 1:1.5.1-1ubuntu0.16.04.2), libgraphite2-3:amd64 (1.3.6-1ubuntu1, 1.3.10-0ubuntu0.16.04.1)
End-Date: 2017-08-23  14:05:57

```

I tried downgrading ubuntu-drivers-common, libxfont1, and libgraphite2-3 but it did not help. Also tried reinstalling Firefox while deleting ~/.mozilla/firefox, didn't help either. Here is a [screenshot]("http://pix.toile-libre.org/upload/original/1504170229.png") of my font settings. 

Any idea what I should try?

---

### Post by vasa1 on 2017-08-31
You can upload images here directly using the paper-clip icon.

---

### Post by vasa1 on 2017-08-31
Have you tried turning off hardware acceleration? See [https://support.mozilla.org/en-US/kb/performance-settings](https://support.mozilla.org/en-US/kb/performance-settings)

---

### Post by ak0ska on 2017-08-31
Thanks for the suggestion. I turned it off but the issue persists.

---

### Post by ak0ska on 2017-09-06
This solved my issue: [https://support.mozilla.org/en-US/questions/1160316](https://support.mozilla.org/en-US/questions/1160316)

---

