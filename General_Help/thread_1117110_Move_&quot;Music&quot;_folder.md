---
title: "Move &quot;Music&quot; folder"
date: 2009-04-05
forum: General Help
---

### Post by shiv379 on 2009-04-05
Hi all!
I've just installed Ubuntu (well technically Mint) for my gf, and I have hit on something that (being a Linux n00b) I haven't been able to solve myself yet. Ubuntu defaults to ~/Music for the music folder, however I would like to use the path /mnt/data/Music. Does the ~/Music folder have any special relevance or can I just delete the links to ~/Music in the Nautilus sidebar and manually replace them with links to /mnt/data/Music?

If it does have a special relevance, is there a way to create a hard-link from ~/Music to /mnt/data/Music? I tried ln but it doesn't like it:
```
ln: creating hard link `/mnt/data/Music/Music' => `/home/gemma/Music': Invalid cross-device link
```
From reading the man page for ln it seems this is pretty much to be expected.

~Shiv

---

### Post by WatchingThePain on 2009-04-05
Hi,
I'm a noob too, but I know that a hard link cannot cross a filesystem, which is kind of what that error message is saying.
Sym links can.

---

### Post by 3Miro on 2009-04-05
```

ln -s target link_name

```

So I guess in your case it would be:
```

ln -s /mnt/data/Music/Music /home/gemma/Music

```

I don't know the implications of deleting the original Music folder, it should be fine though.

---

