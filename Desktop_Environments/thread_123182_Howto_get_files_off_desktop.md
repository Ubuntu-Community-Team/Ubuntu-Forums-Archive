---
title: "Howto get files off desktop??"
date: 2006-01-29
forum: Desktop Environments
---

### Post by majikstreet on 2006-01-29
Hi,
I think that I may start using gnome again, but I have a big problem..

My desktop is cluttered with files from ~/Desktop.. I want to keep files there, but I don't want to see them on my desktop! How do I get it to either have no files on the desktop, or use another folder? (like maybe ~/Desktop/desktop or something)

thanks,
majikstreet

though I actually use dapper, but it shouldn't make a difference.

---

### Post by dcraven on 2006-01-29
You can make your $HOME folder your desktop by doing this:
```
gconftool-2 --type boolean --set /apps/nautilus/preferences/desktop_is_home_dir true
```

Cheers,
~djc

---

### Post by majikstreet on 2006-01-29
then I'd have even more stuff lol.

edit: someone on IRC is helping me, I will post afterwards..

---

### Post by majikstreet on 2006-01-29
here's what I did:

```

cd ~/Desktop
touch .hidden
ls -x > .hidden
mkdir dtfiles

```
That will make all files other than dtfiles be hidden from view.. But, since firefox downloads to ~/Desktop, I changed firefox to download to ~/ffoxdownloads

Also: any files added after you did the ls will be shown! you will need to do this to make it again:
```

cd ~/Desktop
rm .hidden
touch .hidden
ls -x > .hidden
gedit .hidden

```
and in gedit remove dtfiles then save and close,
then you are done :)

---

