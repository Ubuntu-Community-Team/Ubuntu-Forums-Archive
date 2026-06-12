---
title: "Skype won't install - tar says 'unexpected EOF'"
date: 2010-02-26
forum: Desktop Environments
---

### Post by tonywhelan on 2010-02-26
I have two machines with Ubuntu Karmic, one an i386 built with Alternate i386 disk and the other an AMD64 which I have built with the Alternate AMD64 bit disk.

Kernel is 2.6.31-19-generic

Since the past week or so, both machines display failures installing Skype or Google desktop or Opera and other DEB packages with gDebi package installer. gDebi reports ```
dpkg-deb: error processing skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/bin/skype')
```

in gDebi, if I click the tab "Included files" I don't get a file list, instead get "Error reading file content 'Error -3 while decompressing: invalid stored block lengths'".

If I open the DEB in FileRoller or xArchiver, and extract the data.tar.gz file (which is the payload) to my desktop  then try to un-tar it manually I get an error:

```

tar zxfv data.tar.gz
./
./usr/
./usr/bin/
./usr/bin/skype

gzip: stdin: invalid compressed data--crc error

gzip: stdin: invalid compressed data--length error
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

``` 

I have rebuilt my AMD64 machine this week believing I had a corrupt system somehow when I first encountered this same error trying to install Sun Virtual Box. But since I find have the same issue on another machine, I now have to ask if there's a bug somewhere in tar version 1.22?

I had previously downloaded these packages and installed them a few weeks ago and there was no issue at the time. Can't think what could have changed since then. 

Has anyone else had trouble installing Skype or other DEBS, with a similar error?

Postscript:

I have managed to get Skype installed by downloading yet again and so assume the early copy was corrupt. Installed Google desktop from a repository and that worked. Still stuck with Opera failing, despite several repeats of the download. Likewise cannot install VirtualBox or Truecrypt.

All of these packages have installed and run perfectly in the past, so I'm a bit p***d off at my sudden change of fortune. I just can't make sense of that's happening here.
[B][COLOR="Red"][B]
SOLVED (in a fashion): [/B][/COLOR][/B]I had been saving all downloaded files to a network drive on another machine and installing from there. There has never been a problem with that in the past. However that network machine was rebuilt last week. Light comes on slightly in the murkiness .... So I re-downloaded new DEBS to my local desktop and they installed perfectly!

But if I copy the original DEBS from my network drive to my local desktop, and try them, they fail. This suggests that somehow any downloads to the network drive are corrupting. Which is a worry, but a different problem for another day. Right now I feel alcohol is in order.

---

### Post by gmargo on 2010-02-27
You can check the integrity of any gzip-compressed file with "**gzip -t filename.gz**". But it seems obvious that you have a short or corrupt .deb file

---

### Post by tonywhelan on 2010-02-27
> **gmargo said:**
> You can check the integrity of any gzip-compressed file with "**gzip -t filename.gz**". But it seems obvious that you have a short or corrupt .deb file

Its just weird that a whole bunch of them on my network drive should suddenly be corrupt. The file size of corrupt archives seems identical to the 'good' copies I later downloaded, but vbindiff suggests the contents were quite different.

---

### Post by gmargo on 2010-02-27
> **tonywhelan said:**
> Its just weird that a whole bunch of them on my network drive should suddenly be corrupt. The file size of corrupt archives seems identical to the 'good' copies I later downloaded, but vbindiff suggests the contents were quite different.

Time for an **fsck**?

---

