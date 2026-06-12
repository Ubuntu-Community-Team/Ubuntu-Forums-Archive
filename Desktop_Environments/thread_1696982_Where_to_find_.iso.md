---
title: "Where to find .iso?"
date: 2011-02-28
forum: Desktop Environments
---

### Post by bloodshot13 on 2011-02-28
I'm still learning ubuntu and I'm trying to install windows7 in either vm player or virtualbox. I've downloaded the .iso(took 2hrs:() and now I'm not sure how to find it in ubuntu to either burn to c.d. or use virtually. Ubuntu used "Archive manager" as default for downloading. I'm not sure if this was correct to use,as I was thinking ubuntu is alot smarter than I. Where do I go to find the downloaded files?(and yes it's legal). I also downloaded the binary file of vmware, and again not sure what to do. I looked for windows files in <search< files, then alot of files came up, but I'm not sure what I'm looking at. Help me please! I'm sorry if this is newbie territory, but I'm a newb:D.

---

### Post by runeh76 on 2011-02-28
Home/Downloads

---

### Post by bloodshot13 on 2011-02-28
> **runeh76 said:**
> Home/Downloads

Nothing there.

---

### Post by Frogs Hair on 2011-02-28
Check the Archive Manager on the accessories menu.

---

### Post by cascade9 on 2011-02-28
I could be wrong on this, but here goes anyway.

If you let 'archive manager' open the file on downloading (it wont connect to the net, firefox or whatever browser you were using still does the d/ling) then it should have opened archive manager when the file finished d/ling. Not that would help, you dont want to open the .iso at all.

You should have chosen 'save this file' not 'open with ....'. If you are lucky, the .iso might still be in /tmp.

---

### Post by BbUiDgZ on 2011-02-28
in terminal do

```

sudo apt-get install locate
sudo updatedb
sudo locate *.iso

```

---

### Post by bloodshot13 on 2011-02-28
I'm not at my computer right now but I will be around 7pm est. Thanks for all the posts. I'm crossing my fingers I don't have to re-download it.

---

### Post by bloodshot13 on 2011-02-28
@frogs hair- No "Archive Manager" in accessories. @cascade-I'm not sure, I look in "search files" and put windows 7 and nothing comes up. I put in just "windows" and some come up but nothing the near the size of 3.5gigs. @BbUiDgZ I did that and nothing came up after :
sudo locate *.iso
I'm thinking I'm gonna have to download again and this time "Save file". I'm not sure but I don't think it gives you a choice where to save it. If that is the case does it automatically save it to "downloads" file?

---

### Post by Frogs Hair on 2011-02-28
Sorry bloodshot13 , the Archive Mounter needs to be added to the accessories menu from the main menu I had added it in October and forgotten.

---

### Post by bloodshot13 on 2011-02-28
> **Frogs Hair said:**
> Sorry bloodshot13 , the Archive Mounter needs to be added to the accessories menu from the main menu I had added it in October and forgotten.
That's o.k.. I've re-downloaded windows7 and I "Saved" it this time:D. Now I'm trying to install vmware player 3.1.2 and I'm not sure how to make it executable. I'm trying w/ the help of this site- [http://resalxh.wordpress.com/2010/09/09/vmware-player-3-1-1-on-ubuntu-10-10-maverick-meerkat/](http://resalxh.wordpress.com/2010/09/09/vmware-player-3-1-1-on-ubuntu-10-10-maverick-meerkat/), but term. says "chmod: cannot access `VMware-Player-3.1.2-301548.x86_64.bundle': No such file or directory. How do I make it executable?
   I'm putting chmod +x VMware-Player-3.1.2-301548.x86_64.bundle in term.

---

