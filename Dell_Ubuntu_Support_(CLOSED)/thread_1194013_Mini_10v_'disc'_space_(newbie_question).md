---
title: "Mini 10v 'disc' space (newbie question)"
date: 2009-06-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wrinkley1 on 2009-06-22
I have just installed the 190 updates from Update Manager. My SD 'disc' space has decreased from 2.8Gb to 2.5Gb. Does anyone know if this is because the new files are this much larger than the originals or because Update Manager does not tidy up the files it downloaded (or maybe it's the originals of the replaced files) ?
If it's the downloaded files or the originals, will the space eventually be reclaimed or do I have to do something (assuming I can do something!).
As I've only got 8Gb I want to keep it as clean as possible.

---

### Post by Waappu on 2009-06-22
Hi

Try issue these command on terminal
```

sudo apt-get autoclean
sudo apt-get clean
sudo aptitude -y purge ~c

```

See this post also
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by ugm6hr on 2009-06-22
[http://ubuntuforums.org/showpost.php?p=7421989&postcount=15](http://ubuntuforums.org/showpost.php?p=7421989&postcount=15)

---

