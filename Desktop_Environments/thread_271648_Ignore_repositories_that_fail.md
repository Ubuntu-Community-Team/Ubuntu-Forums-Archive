---
title: "Ignore repositories that fail?"
date: 2006-10-05
forum: Desktop Environments
---

### Post by Megatog615 on 2006-10-05
I use a repository on a network, and that computer is sometimes down. Is there a way to have apt-get update ignore the repository if it fails to download the files during apt-get update?

---

### Post by donatell0 on 2006-10-05
For that you either edit the /etc/apt/sources.list and comment out the corresponding repos by putting a hash mark (#) before the line. Or you can just use synaptic and uncheck the corresponding repo in one of the menus.

---

### Post by Megatog615 on 2006-10-05
Well I know that. The computer I'm taling about could be up or down and I wouldn't know it. Is there a way to give the repo a lesser priority that ignores the repo and continues to form the package database after the repo fails instead of stop with an error?

---

