---
title: "Eterm easy questions"
date: 2005-10-08
forum: Desktop Environments
---

### Post by asterix404 on 2005-10-08
I just did the 

sudo apt-get install eterm-themes

It didn't update in hte eterm window though and the backgrounds are all the same. Does anyone know why?

---

### Post by darkmatter on 2005-10-08
The eterm-themes package installs themes as a whole. To change a theme you need to run Eterm from the command line with
```
Eterm -t <theme_name>
```
To see which themes are available, look in /usr/share/Eterm/themes

---

### Post by asterix404 on 2005-10-08
Yea but the funny thing about that is that the Eterm window background menu is supose to do that right? Like... give me one to choose from?

---

### Post by frylock on 2007-01-21
I was wondering if there's a way to automate all themes to randomly display but not sure how?

---

