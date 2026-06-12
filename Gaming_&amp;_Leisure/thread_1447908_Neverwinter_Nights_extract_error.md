---
title: "Neverwinter Nights extract error"
date: 2010-04-05
forum: Gaming &amp; Leisure
---

### Post by micasa2001 on 2010-04-05
Running Ubuntu Jaunty, trying to install the Bioware .tar.gz file. When attempting to extract the file with Archive manager receive the following message:

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors

I find this odd since this is supposed to be in gzip format given the .gz extension.

Note: I am a Noob with short-term memory issues, so please be gentle.

Any ideas?

---

### Post by disturbed1 on 2010-04-06
Which file? If it's something you downloaded, try to download it again - perhaps the transfer was corrupt.

If it's the 482MB English_linuxclient169_xp2.tar.gz update, here's the md5sum for it.

```
bash-4.0$ md5sum English_linuxclient169_xp2.tar.gz
b021f0da3b3e00848521926716fdf487  English_linuxclient169_xp2.tar.gz
```

You can use these installers with your original discs
[http://liflg.org/?catid=6&gameid=65](http://liflg.org/?catid=6&gameid=65)

---

### Post by micasa2001 on 2010-04-06
> **disturbed1 said:**
> Which file? If it's something you downloaded, try to download it again - perhaps the transfer was corrupt.

If it's the 482MB English_linuxclient169_xp2.tar.gz update, here's the md5sum for it.

```
bash-4.0$ md5sum English_linuxclient169_xp2.tar.gz
b021f0da3b3e00848521926716fdf487  English_linuxclient169_xp2.tar.gz
```You can use these installers with your original discs
[http://liflg.org/?catid=6&gameid=65](http://liflg.org/?catid=6&gameid=65)

It's the Bioware download nwresources129.tar.gz file. The instructions state to extract this, then go to another site to download the .bin files and place them in the NWN folder. I haven't seen any other reference to this type of error, so I'm not sure what's going on.

I'll have to study up on the bash command, not familiar with it yet. As I said, I'm pretty much a noob who is not very good at command line stuff. TG for cut and paste, though! 

I have the Platinum edition with the Keys for NWN, Unrentide and SOU. I'm not sure where my original disks went, though:) I'd have to dig through a bunch of boxes to find them.

You think I should download the file again? It took about 40 minutes the first time.

Thanks for the reply.

Mike

---

### Post by micasa2001 on 2010-04-06
Re-downloaded the file, apparently the original was corrupted. This one extracted just fine into a folder I labeled "nwn".

---

