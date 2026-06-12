---
title: "Crontab editor"
date: 2006-09-13
forum: Desktop Environments
---

### Post by amsch on 2006-09-13
Hello!

Im new to (k)ubuntu and I want to edit my crontab but I would like to use vim and not nano - how can I change the crontab-editor?

Thank ins advance!

---

### Post by whizbaby on 2006-09-13
Type

[B]export EDITOR=vim
[/B]
in your terminal and append that line to your /home/YourUserName/*.bashrc*

---

### Post by skymt on 2006-09-13
Or, for a system-wide change, run "sudo update-alternatives --config editor" and pick vim.

---

### Post by amsch on 2006-09-14
Thank you very much - it worked!

---

