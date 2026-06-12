---
title: "Locked myself out of Breezey Badger"
date: 2006-05-28
forum: Desktop Environments
---

### Post by wb7ubb on 2006-05-28
I went to User Properties in Gnome and set my username to have / access. I thought maybe this would boot me into the root dir.

Now when I put in the login screen, my username and password it says "Your $HOME/.dmrc file has incorrect permissions and is being ignored" The next screen says it was logged in for 10 seconds and then goes back to the login screen.

If I could add a new user in the terminal window, I might be able to fix this problem but not being too familiar with Linux I'm not sure how to do this:-k :confused: 

Please help

---

### Post by TTT_travis on 2006-05-28
[QUOTE=wb7ubb]I went to User Properties in Gnome and set my username to have / access. I thought maybe this would boot me into the root dir.

Now when I put in the login screen, my username and password it says "Your $HOME/.dmrc file has incorrect permissions and is being ignored" The next screen says it was logged in for 10 seconds and then goes back to the login screen.

If I could add a new user in the terminal window, I might be able to fix this problem but not being too familiar with Linux I'm not sure how to do this:-k :confused: 

Please help[/QUOTE]

Try to get to the terminal some how and then run

```
sudo su
```

```
vi /etc/passwd
```

this will open up a editor, find your username 

it will be a line that looks something like

```
username:x:1002:100:Name:/:/bin/bash
```

after :Name: there is a / change that to /home/YOURUSERNAME

so if your username was username 

```
username:x:1002:100:Name:/home/username:/bin/bash
```

Hope this helps,
Travis

---

### Post by wb7ubb on 2006-05-28
Worked like a charm! Thank You

---

