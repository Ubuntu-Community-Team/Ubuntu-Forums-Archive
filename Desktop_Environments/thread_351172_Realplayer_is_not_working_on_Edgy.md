---
title: "Realplayer is not working on Edgy"
date: 2007-02-01
forum: Desktop Environments
---

### Post by mesh2005 on 2007-02-01
I installed Edgy, I installed Realplayer but it didn't work. I tried to open rm or mp3 files but it hangs and no sound is displayed although my sound card is correctly detected. Realplayer was working fine on 5.10 and 6.06, Please help
Thank you

---

### Post by flossgeek on 2007-02-01
RealPlayer works fine for myself on edgy. How did you install RealPlayer?

You should add the commercial repository to your *sources.list* found in the */etc/apt* directory.

Issue 

```
gksudo gedit /etc/apt/sources.list
```

then add the commercial repository to the end of the file.

```
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main
```

Then do 

```
sudo apt-get update
``` 

and finally install realplayer 

```
sudo apt-get install realplay
```

---

