---
title: "Backup and Restore GNOME Panel 2.32"
date: 2012-07-25
forum: Desktop Environments
---

### Post by tg3793 on 2012-07-25
I thought for sure that this would be a simple google task. But alas here I am thinking this question is too simple for a post but asking it anyhow.

Where would I find the settings for any GNOME Panels I have created. I have GNOME Panel 2.32.1 with both Window List 2.32.1 and 
Workspace Switcher 2.32.1 on it and I'd like to delete it for the moment but put it back later if I don't like some of the changes that I'm getting ready to make.

Thanks.

---

### Post by tg3793 on 2012-07-26
Okaly Dokaly. So no resolution that I can be sure of yet but just a work-around for now. I went to properties on my two Gnome Panels and checked the box that said "Show Hide Buttons" and made sure that the "Arrows on Hide Buttons" was left unchecked.

So, at least now these things are out of my way. But I would still like to backup their individual settings and get rid of them in a way that would also allow me to re-enable them at a later time if I'd like.

I [studied another thread]("http://ubuntuforums.org/showthread.php?p=9060322") which led me [to this answer]("http://ubuntuforums.org/showpost.php?p=9060322&postcount=2"). 

```
sudo mv /usr/bin/gnome-panel ~/.panel_backup
```

It's not exactly the answer that I'm looking for but I'll dive into it later if I don't find a better answer in the meantime.

What I am hoping for, is a way to backup individual gnome panels so I can get rid of one and 'not' the other. In my case I have three panels and I want to selectively get rid of two of them.

Thanks to anyone that can help shed a little light on this.

---

### Post by tg3793 on 2012-08-04
Ok, I think I've found them. Not only the gnome panel that I was looking for, but then several others that will likely be useful as well one day.

```
~/.gconf/apps/panel
```

And it seems that all of the customizations are found here:

```
~/.gconf/apps/panel/objects
```

Hope this helps someone else out one day as well since I didn't find a lot on this when I was googling around.

---

