---
title: "dialer-app (phone) starts but not showing anything"
date: 2020-08-04
forum: Desktop Environments
---

### Post by itamarm2 on 2020-08-04
Hi,

I have install dialer-app on my laptop which runs Ubuntu 20.04.1 LTS. following those [simple instructions ]("https://snapcraft.io/install/dialer-app/ubuntu")
Installation complied successfully and "Phone" shortcut was created in favorites applications
weird thing is when I launch 'Phone' from application it open a blank window
[IMG]https://drive.google.com/file/d/1dW4kjCrwK2CkEaKiXQSnZ_r9Ho26jTZy/view?usp=sharing[/IMG][ATTACH=CONFIG]286602[/ATTACH]

Here are syslogs when launching the app:
Aug  4 21:31:13 IMPC01 systemd[1919]: Started Application launched by gnome-shell.
Aug  4 21:31:13 IMPC01 dialer-app_dialer-app.desktop[7434]: Qt: Session management error: None of the authentication protocols specified are supported
Aug  4 21:31:13 IMPC01 dialer-app_dialer-app.desktop[7434]: void installIconPath()
Aug  4 21:31:13 IMPC01 dialer-app_dialer-app.desktop[7434]: file:///home/renato/projects/phablet/dialer-app/snappy/parts/dialer-app/src/src/qml/dialer-app.qml: File not found
Aug  4 21:31:13 IMPC01 dialer-app_dialer-app.desktop[7434]: XmbTextListToTextProperty result code -2

any idea what am I missing?

---

