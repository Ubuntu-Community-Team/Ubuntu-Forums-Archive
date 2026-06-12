---
title: "Unreal Tournament 2004 installation..."
date: 2007-05-29
forum: Gaming &amp; Leisure
---

### Post by Neon_Knight on 2007-05-29
Okay, here we go:

I love linux to bits, and I'm all for trying gaming on linux.

A while ago, I installed UT2004 on linux no problems, it wouldn't start, but the newest patch fixed that, and It had GREAT frame rates, everything was just great, I could even play online.

Since then I've gone through 2 ot 3 reinstallations of Ubuntu (6.06), and I'm trying to install it again, but this time..

*DONK* installer says "balls to this, yo" and jumps out of the window.

Here's what really happens:

It opens a new window (after the line "sudo bash linux-installer.sh") , and it does the whole licence agreement thing, and the install options, and then it opens a window that tells me which file it's installing at the current point in time.  When the error happens, the window just closes.

```


david@david-desktop:~/Desktop$ sudo bash linux-installer.sh 
Password:
Copying to a temporary location...
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 2004 for GNU/Linux 3186......................................................................
UZ2: Failed to fully write [**/usr/local/games/ut2004/Maps/DOM-Conduit.ut2**]!
./setup.sh: line 148: **15832** Aborted                 "$setup" "$@"


```

The bits that are **bold** are the bits that change each time I try to install. It's always a different file that it fails to write (it's usually a map) and sometimes it's a whole bunch of files, but I think each time it goes slightly further with the installation, because they don't reappear after the next attempted installation.

What do you think I should do? I think it's probably a repository problem, as it worked before, but now it isn't.

I've cleaned the disk many times.

What can I do about this?

I'm currently downloading the game files through a torrent, but it looks to take a long long time and I'd rather get the one I already have to work properly. ¬_¬

---

### Post by Cappy on 2007-05-29
I searched on the error and found
"If you get a &#8220;Failed to fully write&#8230;&#8221; error, I was able to overcome this by copying the DVD to a directory on the hard drive. I created a directory (called /root/ut2004dvd) and copied everything with the following command:" ...

More @ [http://girasoli.org/?p=228](http://girasoli.org/?p=228)

---

