---
title: "Software Updater 17.04 Failed to download repository information, no suitable servers"
date: 2018-03-05
forum: Desktop Environments
---

### Post by amitmo81 on 2018-03-05
Hello,

I have been using and updating my 17.04 ubuntu regularly since I installed it in August 2017. Starting about a month ago or so, trying to update Ubuntu Base has yielded the following error (I can update other packages, such as Chrome and Skype, without any issues).
[INDENT]Failed to download repository information
Check you internet connection[/INDENT]

Details:
```
[FONT=Verdana]/ubuntu zesty Release' does not have a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository '[http://mirror.isoc.org.il/pub/ubuntu](http://mirror.isoc.org.il/pub/ubuntu) zesty-updates Release' does not have a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository '[http://mirror.isoc.org.il/pub/ubuntu](http://mirror.isoc.org.il/pub/ubuntu) zesty-backports Release' does not have a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository '[http://mirror.isoc.org.il/pub/ubuntu](http://mirror.isoc.org.il/pub/ubuntu) zesty-security Release' does not have a Release file.[/FONT]

```

The same results occur when I used the Main Server. Upon examining some solutions, I tried Setting > Download from: > Other and on the "Choose a Download Server" dialog box > Select Best Server. The search results in an error:[INDENT]
No Suitable Download Server Was Found. Please check your internet connection.[/INDENT]

My internet connection is working well and I am not using a proxy as far as I know.

How can I fix this?

---

### Post by cruzer001 on 2018-03-05
17.04 has reached end of life and no longer supported, the repositories have been removed.  

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by amitmo81 on 2018-03-05
Doh. Thanks. This is my first time running a non-LTS release so never had to deal with this before.

---

### Post by cruzer001 on 2018-03-05
No problem :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

