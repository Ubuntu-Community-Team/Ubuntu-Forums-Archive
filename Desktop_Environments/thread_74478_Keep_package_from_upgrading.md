---
title: "Keep package from upgrading?"
date: 2005-10-11
forum: Desktop Environments
---

### Post by Billquinn1 on 2005-10-11
How do I keep an older version of something when there are new packages wanting to replace it. I saw a thread talking about the /etc/apt/preferences file but I don't have that. I just installed fresh breezy and need to keep a certain version of Wine (I know) but the last upgrade put me back to the newest Wine.

Any help or suggestions?

---

### Post by mlomker on 2005-10-11
If you use Synaptic you can highlight the package and then select 'lock version' from the Packages menu.  

If you intend to use apt-get from the command line then I think you have to create the /etc/apt/preferences file.  By default all repositories are given equal weight, which is why it's unsafe to have non-Ubuntu repositories always in your list.

[I found some docs here.]("http://www.argon.org/~roderick/apt-pinning.html")  I looked through it and it didn't seem all that clear to me, either.

---

### Post by Billquinn1 on 2005-10-11
I see it. I wonder if the new adept thing has that. I will just use Synaptic until further notice.
Thanks for the quick reply

---

### Post by mlomker on 2005-10-11
No problem.  I just found some much clearer [documentation]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version") on the debian website.  I found that in an [interesting thread]("http://forums.xandros.com/viewtopic.php?t=708&postdays=0&postorder=asc&start=0") on the Xandros board.

---

