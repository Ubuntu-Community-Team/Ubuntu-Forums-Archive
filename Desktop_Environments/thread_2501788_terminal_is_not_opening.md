---
title: "terminal is not opening"
date: 2024-10-21
forum: Desktop Environments
---

### Post by bihag on 2024-10-21
after a pop up window arrives i updated the ubuntu After completing the update the terminal is not opening .it is loading only .please resolve as soon as possible i have updated to ubuntu24.04LTS

---

### Post by hifron on 2024-10-21
may be related:
[https://github.com/ros2/ros2/issues/1406](https://github.com/ros2/ros2/issues/1406) for vscode(only snap) problem, maybe due some timeout problem or not set properly or to zero...

try in terminal(ctrl alt F1 or F2)
systemctl --type=service --user
or maybe
systemctl --type=service

to see if gnome.terminal.server is running

---

### Post by grahammechanical on 2024-10-21
You confused me by posting almost the same problem in two places. The thread title of the other post is inaccurate.

[https://ubuntuforums.org/showthread.php?t=2501806](https://ubuntuforums.org/showthread.php?t=2501806)

Regards

---

