---
title: "I click on a APP icon, but the APP doesn't start."
date: 2020-05-06
forum: Desktop Environments
---

### Post by rocco.martinello on 2020-05-06
[IMG]http://www.roccomartinello.it/screenshot8595.png[/IMG]
If I click on "ESET..." icon, the software doesn't start, all others software starts, how can I solve this issue?
Thank you in advance!!!

---

### Post by Perfect Storm on 2020-05-06
Try start it through the terminal.

```
/opt/eset/esets/bin/esets_gui
```

---

### Post by rocco.martinello on 2020-05-06
[IMG]http://www.roccomartinello.it/screenshotEset.png[/IMG]
Maybe bacause I already udsed the command _install-libappindicator1_

---

### Post by Perfect Storm on 2020-05-06
First try with:
```
sudo systemctl stop eset
```

---

### Post by rocco.martinello on 2020-05-06
[IMG]http://www.roccomartinello.it/screenshot86396.png[/IMG]

---

### Post by Perfect Storm on 2020-05-06
You better take it to eset nod support forum for further help as it it specific problem with theirs software. I don't know if the app is listed in startup. You could try disable it there and reboot and then try start the app again.

This is how startup looks like on my eOS, I think Ubuntu have something similar.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=285762&stc=1&d=1588768193[/IMG]

---

### Post by Perfect Storm on 2020-05-06
I'll give a try on my computer, but don't get your hopes up. I suspect it uses the depreciated systemtray/indicator, that's why it's complaining.

EDIT: Same things happen also on my system.

---

### Post by Perfect Storm on 2020-05-06
Here's a solution. You need to open **System Monitor Utility** in Ubuntu find **esets_gui** and end its process. Then you can start the gui up again.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=285763&stc=1&d=1588769603[/IMG]

---

