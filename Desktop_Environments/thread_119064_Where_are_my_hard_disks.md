---
title: "Where are my hard disks?"
date: 2006-01-18
forum: Desktop Environments
---

### Post by patrickfromspain on 2006-01-18
Hi there!! I installed ubuntu on both my notebook and desktop and well, I like gnome. But yesterday I though I'd install also kde, so I can change when I want to. Better than having a nice desktop, is having 2 of them. Well, no problem installing and so on. But 2 questions: First, if I right click on a compressed file, I don't have the option "Extract here". Is that so??? I find it quite dissapointing having to open the file and extracting from ark. Any solution? Second: if I go to System -> Storing media (media:/) I only see my dvd-rom and dvd-+rw.. Where are hda1 (windows) and hda3 (/)?? (notebook) Where are my sda1, sda5, sda7 (/) and sda8? (Desktop) If I go to /media/ there I see all of them. Any ideas? Thanx!

---

### Post by GoldBuggie on 2006-01-18
For the extract here thingy(if i remember correctly) install
```
sudo apt-get install konq-plugins
```

for the HD to show up in media:/
```
sudo adduser hal disk
```

hope it helps

---

