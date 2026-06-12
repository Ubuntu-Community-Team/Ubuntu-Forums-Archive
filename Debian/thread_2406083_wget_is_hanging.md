---
title: "wget is hanging"
date: 2018-11-15
forum: Debian
---

### Post by spjackson on 2018-11-15
Here's a command I've been using without problem for over a year to backup several websites.
```

wget -r --user=blah --password=blah --mirror ftp://some-ftp.site.com/

```
The computer I run this from is running Debian GNU/Linux 8 (jessie). My router configuration has not changed recently. For some websites the above continues to work but for one it has in the last week begun to hang after a varying amount of time, maybe 1s, maybe 8s, maybe 15s. The folder on which it hangs varies. When it hangs, it appears to hang indefinitely, or rather until I kill it after maybe an hour or more.

The failure point varies but always looks something like this:
```

--2018-11-15 14:35:27--  ftp://some-ftp.site.com/public_html/.listing
           => ‘some-ftp.site.com/public_html/.listing’
==> CWD not required.
==> PASV ... done.    ==> RETR .listing ...

```
It seems to me that something must have changed on the server hosting the problem website. I don't have much control over that server.

Are there any options to wget that might solve this problem?

Is there some other backup command that will achieve similar results? (i.e. not fetching files that are unchanged from last time, preserving tree structure, permissions and timestamps? I have ftp & ssh access with a restricted shell to the server in question.

---

### Post by SeijiSensei on 2018-11-15
By default, rsync runs over SSH and will only transfer files that have changed.  See its [man page]("https://linux.die.net/man/1/rsync") for details.

---

### Post by spjackson on 2018-11-16
Thanks. I seem to have got there with:
```

rsync -avz --copy-links user@some-ftp.site.com: .

```

---

