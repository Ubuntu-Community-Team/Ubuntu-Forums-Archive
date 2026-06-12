---
title: "Rhythmbox importing folders problem"
date: 2005-09-10
forum: Desktop Environments
---

### Post by jworr on 2005-09-10
I've been using Ubuntu for a year now but this is my first post

I use rhythmbox for my music and it works great however some of my ogg files tags where misnamed so I changed the tags with xmms because rhythmbox didn't seem to let me.  When I open rhythmbox after changing the tags the songs that I had altered didn't load. And I tried importing them again but it simply didn't do anything not even an error message.

Any ideas?

---

### Post by Christoff UK on 2005-09-10
Did you give the songs a track number, if I don't muine cant import my songs, not sure if this applies to Rhythmbox, hope it helps...

---

### Post by jworr on 2005-09-10
Yes all my songs have track numbers

---

### Post by jworr on 2005-09-10
I have also tried completely removing rhythm box with sunaptic and reinstalling it buts that doesn't help.  Also I have tried deleting the .gnome2/rhythmbox/rhythmdb.xml file and that doesn't help either

---

### Post by Christoff UK on 2005-09-11
Do you have the required codecs installed to play the files, perhaps you should try....

sudo apt-get install gstreamer0.8-plugins  , or search gstreamer in synaptic and find that package, not sure if this will help, but worth a try?

---

### Post by jworr on 2005-09-11
That didn't change anything :(

---

### Post by thepcdoctor on 2005-09-11
What does this mean?

Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate

---

### Post by Christoff UK on 2005-09-11
I beleive you need to enable extra apt repositories, check out this from ubuntu guide...

[Adding More Apt Repos](http://ubuntuguide.org/#extrarepositories)

---

