---
title: "Has anyone had good luck with tcrequant?"
date: 2006-01-27
forum: Desktop Environments
---

### Post by Blueshell on 2006-01-27
I just tried the simplest possible test with transcode's tcrequent.  Under Breezy, with either the shipped version (transcode 1.0.1) or the latest (1.0.2), it segfaults, presumably somewhere in an included library, on at least two-thirds of the files I give it, a variable number of megabytes in.  (These are files produced by a Hauppauge PVR-250 at the default 4500kbits/sec video rate.)

Under Hoary, it finishes, but running it with default options (just -i, -o, default requantization of 1.5) produces an mpeg that's shot through with blockiness and no real audio (just clicks and screeches) when played with mplayer.

Clearly, something's broken.  Anyone have any success stories w/it?  Otherwise, I'll just open a bug report at Launchpad.

(All .debs, except the 1.0.1 included w/Breezy, are from [http://www.hezmatt.org/~mpalmer/ubuntu/;](http://www.hezmatt.org/~mpalmer/ubuntu/;) please be considerate of his bandwidth and don't download them unless you're testing this.)

---

