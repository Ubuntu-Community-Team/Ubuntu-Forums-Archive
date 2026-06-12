---
title: "[SOLVED] deluge data lose"
date: 2008-12-27
forum: General Help
---

### Post by helmet_chedar on 2008-12-27
i have a problem with deluge.  every time i shut down and restart my computer i loose all data with any uncompleted torrents.  it just restarts the torrent and there is no file any where of the torrent.  i'm using ubuntu 8.10(only been using for about a month,massive virus on windows required new os) and deluge is the one in the repository.

thanks for any help in advance...and mite i add this a very helpful forum..please continue on in your badassedness.

---

### Post by taurus on 2008-12-27
You didn't happen to use /tmp as your _D_estination folder/directory, did you?

---

### Post by 2hot6ft2 on 2008-12-27
> **helmet_chedar said:**
> i have a problem with deluge.  every time i shut down and restart my computer i loose all data with any uncompleted torrents.  it just restarts the torrent and there is no file any where of the torrent.  i'm using ubuntu 8.10(only been using for about a month,massive virus on windows required new os) and deluge is the one in the repository.

thanks for any help in advance...and mite i add this a very helpful forum..please continue on in your badassedness.
I had problems with deluge on and off for a while now and again today so I'm using ktorrent until a newer version comes out to fix it.

Tried purging it and reinstalling. Even going to a previous version. ktorrent is humming along. My brother has had problems with it too, he's using Transmission now.

---

### Post by helmet_chedar on 2008-12-28
i do believe it is using the tmp directory.  does this need to be changed?

---

### Post by taurus on 2008-12-28
The /tmp will get cleaned out each time it boots.  So, why not create one in your $HOME and have that instead.

```
mkdir ~/tmp
```

---

### Post by helmet_chedar on 2008-12-28
sweet...i think it will work fine now.  thanks allot.  see around the forums.

---

### Post by daniel3ub on 2009-03-25
Hi.

I am having the same problem, but I am using my ~/ as destination directory.

What else can cause the unfinished torrents to get deleted?

---

