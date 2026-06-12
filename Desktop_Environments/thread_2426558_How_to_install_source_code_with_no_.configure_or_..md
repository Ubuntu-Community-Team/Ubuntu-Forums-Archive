---
title: "How to install source code with no .configure or .make files"
date: 2019-09-10
forum: Desktop Environments
---

### Post by shag00 on 2019-09-10
Running version 19.04.

I am keen to install this program [https://github.com/SubtitleEdit/subtitleedit/releases](https://github.com/SubtitleEdit/subtitleedit/releases) which this month was released as a tar and a zip source code but without a configure or make file.

Is there a way for me to install this program and if yes, what is it. I am not a programmer but can follow simple instructions.

Previous attempts to install in Wine have been successful but with limited functionality, making it near worthless.

---

### Post by mc4man on 2019-09-10
It would appear you need to use the se3510.zip and run the included SubtitleEdit.exe with mono.
How it actually works no clue as no real use for here.

---

### Post by shag00 on 2019-09-10
Thanks for your quick response but your suggestion leads to the same issues as running it under wine. What I am hoping for is to make a native linux build so I get 100% functionality.

---

### Post by CatKiller on 2019-09-10
It isn't a native Linux application: it uses .NET. You can only run it with Mono.

---

