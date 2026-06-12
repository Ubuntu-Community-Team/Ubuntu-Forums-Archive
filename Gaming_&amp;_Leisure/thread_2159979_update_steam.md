---
title: "update steam"
date: 2013-07-05
forum: Gaming &amp; Leisure
---

### Post by MikeCyber on 2013-07-05
Hi
installed 13.04 and want to keep settings etc. but download/install the latest steam.
How to move my password etc. from 12.10? Is that all in ~./steam?
Thanks
PS: ./steam is huge...can I move it elsewhere then in home?

---

### Post by oldrocker99 on 2013-07-05
Even if your /home folder gets overwritten, and you have to reinstall and start over, when you log in to Steam, it'll send you a 4-character code in your email and asks you to enter it to  prove you're you. You may have to redownload your games, but in my experience Steam treats its customers pretty darned well.

I am a bit unclear about whether ~/Steam and ~/.steam can be moved. I know that Windows users can move their installations around, but I currently don't know. Prehaps a bit of investigation is in order.

---

### Post by Ranko Kohime on 2013-07-07
In can certain be moved.  The folder you're going to want to be concerned about is ```
~/.local/share/Steam
```
Move that folder anywhere you wish, and then symlink it, like so: ```
ln -s /new/path/to/Steam ~/.local/share/Steam
```

For reference, I don't have a ```
~/Steam
```
folder, just the aforementioned folder and ```
~/.steam
```
which merely contains symlinks back to the above.

---

