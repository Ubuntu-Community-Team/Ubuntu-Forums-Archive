---
title: "Evince default window size"
date: 2005-10-26
forum: Desktop Environments
---

### Post by Jingo on 2005-10-26
It took a little while to get used to the 'feature' of evince windows always opening in default size when trying to watch new pdf files - at least it would 'remember' the window sizes of files which had been opened before .. now - the recent version does not seem to remember the window size of watched pdfs any more plus it changes the size to default on the ones it remembered before - I find that _really_ annoying .. does anybody have a clou how to correct this behaviour or is it a new feature? :???: 

I see that the data is saved in $HOME/.gnome2/evince/ev-metadata.xml, but restored again.

How do I change the default window size for new pdf's?

/Jingo

---

### Post by mykey on 2005-10-26
yeah - man - I tried it all - even downgrade to the hoary version .. nothing helps .. I am fed up with this, posted it a couple of weeks ago already and got no response .. but .. found an alternative **sudo apt-get install gnome-gv** has the features you are looking for - it may be a split-sec slower than evince but at least you don't have to resize every time you want to read a pdf

---

### Post by Jingo on 2005-10-27
Hmmm
I think gnome-gv is not as great as evince.... but this bug is really annoying!

I dont get it... it restores the page at which I was looking last time i opened the pdf! But not the size. Is the default size hardcoded?

---

### Post by ow50 on 2005-10-27
It's being worked on. There's a couple bug reports related to it
[http://bugzilla.gnome.org/show_bug.cgi?id=317031](http://bugzilla.gnome.org/show_bug.cgi?id=317031)
[http://bugzilla.gnome.org/show_bug.cgi?id=316454](http://bugzilla.gnome.org/show_bug.cgi?id=316454)
[http://bugzilla.gnome.org/show_bug.cgi?id=168450](http://bugzilla.gnome.org/show_bug.cgi?id=168450)

---

### Post by mtpadilla on 2006-06-28
I would recommend using kpdf...it has all of the features that evince has and more.

---

