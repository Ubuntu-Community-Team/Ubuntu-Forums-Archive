---
title: "7 installations on network, don't want to download updates for each"
date: 2009-02-10
forum: General Help
---

### Post by pssturges on 2009-02-10
Hi,

I have 7 ununtu/mythbuntu installations on my home network. As I have a limited download quota each month, I'd like to find a way to download each update only once.

I have one Mythbuntu backend box which basically runs as a server (samba, apache, cups etc). Ideally I'd like to be able to run updates on any of the pc's and have the downloaded packages cached on my server. Then when the next pc updates it checks my server first, then if they are not found, download them from the repos (and of cache them on my server for other pc's). I use serveral third party repos also.

Any ideas how I can achieve this?

Thanks in advance
Phil

---

### Post by pssturges on 2009-02-12
Anyone, any thoughts?

---

### Post by perrti-y02 on 2009-02-12
It is possible to download the entire repository to a hard drive and then compile an index that the package manager can read.

This gives you a vague idea how to do it. [http://ubuntuforums.org/showthread.php?t=20217](http://ubuntuforums.org/showthread.php?t=20217)

Obviously, with your download limit you only need to download those that you need. It should work. I think. I have used this to set up a repository on one machine of six, but haven't yet got it working mostly due to problems with actually getting machines to see each other.

---

### Post by pssturges on 2009-02-13
Thanks! There seems to be lot in there that I can use. The link at post #28 looks particularly useful. I have a samba share on the server that is permanently mounted on all the other pc's, I'll create my repository there and it should be available to all the other pc's.

Hmmm. Just thinking out loud...If I create a symlink in my shared folder of /var/cache/apt, then create a symlink on each of the clients replacing the apt folder under /var/cache. That might work? Possibly some permissions issues?

Will play with this some time over the next few days.

Thanks again,
Phil

---

