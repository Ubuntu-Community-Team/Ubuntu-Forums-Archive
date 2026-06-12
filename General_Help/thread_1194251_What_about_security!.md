---
title: "What about security?!"
date: 2009-06-22
forum: General Help
---

### Post by Acemcloud777 on 2009-06-22
I haven't been advised or counselled into trying or using a firewall, or a anti-virus software...any suggestions specifically designed for the latest ubuntu?:D

---

### Post by Amilo1718 on 2009-06-22
why do you want that?

---

### Post by Acemcloud777 on 2009-06-22
well...I guess i am used to being given a software suggestion funded by the operating system's company. I am very new to ubuntu, i used to have windows, and they let me know where I wasn't really protected. I completely reinstalled windows to have a "fresh start", and chose ubuntu to use. I am on the internet, I don't know if I should be yet without any protaction.

---

### Post by mcduck on 2009-06-22
> **Acemcloud777 said:**
> I haven't been advised or counselled into trying or using a firewall, or a anti-virus software...any suggestions specifically designed for the latest ubuntu?:D

Most likely you don't need either of those.

There are currently no viruses that would be a thereat for Linux systems, so antivirus software is only useful mail servers and such situations, to help protecting Windows machines.

And unless you install some server program that listens for incoming network connections there's nothing in Ubuntu that would be open for outside attacks so firewall isn't necessary. But in case you plan on running some servers then I recommend using UFW, or Gufw if you want a graphical user interface.

---

### Post by Amilo1718 on 2009-06-22
[link]("http://ubuntuforums.org/showthread.php?t=1193423")
:popcorn:

---

### Post by Acemcloud777 on 2009-06-22
> **mcduck said:**
> Most likely you don't need either of those.

There are currently no viruses that would be a thereat for Linux systems, so antivirus software is only useful mail servers and such situations, to help protecting Windows machines.

And unless you install some server program that listens for incoming network connections there's nothing in Ubuntu that would be open for outside attacks so firewall isn't necessary. But in case you plan on running some servers then I recommend using UFW, or Gufw if you want a graphical user interface.

so..trojans can't affect my computer?

---

### Post by jonobr on 2009-06-22
Hello


[Heres]("https://help.ubuntu.com/community/Antivirus") a link with references to anti virus software, 
Although one should never be complacent, the fact of the matter is that the vast majority of viruses and so on are written for windows systems.

You could also take a look at Iptables which will require you to know a bit more about ip itself and figure out which packets you want to hold onto, and which you want to filer or pass.

Cheers

---

### Post by lovinglinux on 2009-06-22
I strongly recommend reading the [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial.

You can also read a plethora of threads asking if a [firewall](http://www.google.com/search?q=need+firewall+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) or [anti-virus](http://www.google.com/search?q=need+anti-virus+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) are needed.

---

### Post by Soul-Sing on 2009-06-22
please read this information: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by mcduck on 2009-06-22
> **Acemcloud777 said:**
> so..trojans can't affect my computer?

Trojans can, at least in theory, as their functionality pretty much depends on human stupidity and nothing else. Common sense is how you protect against trojans, as long as you only install programs from trusted sources you'll have no problems.

Real viruses, like I said, are not a problem.

In other words, if you for some strange reason choose to not use package management, or even downloading from some well-known web site, and instead download and install binary files from some shady website nobody has ever even heard of, nothing's protecting you. But you are not going to get any real virus that would be able to spread to your system without you actively installing it.

---

