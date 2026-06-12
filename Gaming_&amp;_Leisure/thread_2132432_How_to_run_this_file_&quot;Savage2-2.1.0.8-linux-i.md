---
title: "How to run this file: &quot;Savage2-2.1.0.8-linux-installer.run&quot;?"
date: 2013-04-04
forum: Gaming &amp; Leisure
---

### Post by candre on 2013-04-04
HelloI have downloaded this file "**Savage2-2.1.0.8-linux-installer.run**".
But I can't run it.
I typed in the terminal "**sudo sh** **Savage2-2.1.0.8-linux-installer.run" **and it says [B]end of file unexpected (expecting ")").
[/B]
What should I do?

---

### Post by myromance123 on 2013-04-05
SH is only used for script files. For example "sh install.sh"

What you want to do is this:
```
./Savage2-2.1.0.8-linux-installer.run
```

Or if you really need the sudo part, then:
```
sudo ./Savage2-2.1.0.8-linux-installer.run
```

Better yet though, why not run it like a normal GUI program? Right click the installer, and go to Properties. Click the Permissions tab and tick "Allow executing file as a program".

Now just double click the installer.run and it will run in a GUI form with Next buttons and all. I hope this helps a bit :)

---

