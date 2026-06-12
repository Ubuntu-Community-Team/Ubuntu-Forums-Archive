---
title: "Sharing swapspace between Linux and Windows"
date: 2009-05-12
forum: Desktop Environments
---

### Post by agharbeia on 2009-05-12
In an [archived thread]("http://ubuntuforums.org/showthread.php?t=112073"), there was a discussion about sharing the partition between Linux and Windows in a dual-boot configuration, which could utilise otherwise unused space reserved exclusively for each operating system.

There's a filesystem driver, namely [SwapFS]("http://www.acc.umu.se/~bosse"), (which I haven't tried yet) which allows Windows to use the Linux Swap partition, probably to store its swap file. This has a benefit over the [method mentioned by Milflyboy]("http://ubuntuforums.org/showpost.php?p=790589&postcount=12") in that it doesn't fail when Windows is booted after Linux has been improperly shutdown (i.e. crashed).

My problem is a little more complex, however, as I encrypt my Linux swap partition, which means there will be no Linux swap file system when Linux shuts down. So I might end up having Linux create a stub filesystem on the swap partition when it's shutting down. Alternatively, the idea of loopmounting the Windows swapfile and using it for Linux could be worth something

I also second what Milflyboy wrote in that thread about not using Partition Magic to resize ext2|3 partitions as it corrupts them. Use [G]Parted instead for your paritioning chores.

---

