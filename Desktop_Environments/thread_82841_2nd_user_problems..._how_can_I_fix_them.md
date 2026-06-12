---
title: "2nd user problems... how can I fix them?"
date: 2005-10-27
forum: Desktop Environments
---

### Post by mlaverd on 2005-10-27
Hello folks,

Because I wanted to put in practice the principle of Least Privilege, I created a second user on my desktop.

However, I bumped on two problems so far:
1) USB drives would not get mounted automatically. I had to manually add the user to the proper group, as told in the man page, and I added all rights in the sudoers file. I think its fixed (did that a few days ago), but I don't like the workaround.

2) This second user does not have a sound card in Systems > Preferences > Sound, whereas the card is there for the initial user. I copied the file that had the information (my grep yielded: ~/.gnome2/accels/gnome-volume-control), and checked with alsamixer, and found that things are OK from its perspective. The audio card is ICH6.

My quick conclusion is that there is something weird in the user adding scripts, so how can those be fixed?

Also, how do I get those things to work cleanly?

---

### Post by Remmelas on 2005-10-27
for the mounting issue, in an fstab entry, for the options for the usb drives entry make sure 'user' is included, then users can mount that media, no need for sudo or any muckery like that.

as far as your audio problem, add the new user to the group 'audio' if you haven't already.

---

### Post by mlaverd on 2005-10-28
Whoho! It works!

For the usb, I added the user to the group plugdev. 
For the audio, I added the user to the group audio, as you said.

The USB drive is mounted flawlessly.
I'm listening to a good OGG stream as I type this (cbc.ca) :cool: 

Now, a more fundamental question... should I file a bug for this? For a user-friendly system, things like that should not be a concern.

Thanks for the help!

---

### Post by Remmelas on 2005-10-28
I don't know if i'd file a bug for all of it, of course, i'm no expert on ubuntu dev policy.  from a linux stand point(as opposed to ubuntu), a user shouldn't be in any groups you don't intentionally put them in(except maybe their own group or the group users).  That says, it would be more 'automagic' if the user add script at least prompted for such things.

---

