---
title: "synchronising multiple computers, best practices?"
date: 2007-04-30
forum: Desktop Environments
---

### Post by maphew on 2007-04-30
I posted this in General Help [[http://ubuntuforums.org/showthread.php?t=423610]](http://ubuntuforums.org/showthread.php?t=423610]), and have zero response. I am hoping this is a better place from which to draw replies as the intro articles to this forum indicate it is a place of deeper than average thought. My question is: how do people deal with keeping their documents and preferences synchronized across multiple computers?

thank you.

---

### Post by tippit78 on 2007-04-30
I think feisty comes with some sort of backup utility, which may or may not be useful for you. I use window maker, but I seem to recall seeing this program in the...preferences area? Maybe. Can't quite remember.

You could try grsync, or just rsync if you're cool with the typing of cryptic commands into a terminal. I'm okay with it but not exactly enthusiastic. I use window maker, not ratpoison. Oh, and there's ksync if you're into KDE. 

This let's you sync up documents, but really, if you've got that many different copies of your documents, having something to sync them up isn't going to help. Maybe if you've got four different drafts of the same document you could use meld or something like it to weave them into a single final draft. I write comedy this way, so it's useful.

But really the answer to your problem is in your post: USB. Or in my case, my iPod, but whatever you got: Find one place to keep your documents that is convenient to you. And has enough memory. Use it ALL THE TIME. I also recommend checking out PortableApps for when you're away from your computer. Granted they only work on Windows machines (or Linux with wine), but at least you're not totally at the mercy  of that computers selection of tools.

Because rsync is good (it seems to me) at taking one file, matching it against a backup, an seeing if it's been changed. But it can't tell what you've been doing across three differently modified copies. That's why, in that case, you have to use something like meld, or just go through each copy line by line.

THEN use rsync (or whatever graphical front end suits your fancy), and make backups-daily-of the data on your portable drive. Or on your laptop. Or on a computer in a folder you can access over a network. Lots 'o' solutions there. And make like, oh, three backups. Just in case. Then lock one of them into an airtight container. Put it in a steel drum , and coat it in concrete. Dump it in the Florida Keys (after convincing the cops your drum contains back ups not Jimmy the Fish's body).

Or just make a couple of backups. It's cool, we're all different.

Sorry for the length of this--Morning, I'm drinking coffee, nice day, and I'm marginally employed in Europe. These are optimum conditions for chattiness.


For prefs...well, I think after a while, most of us find what we like. I don't mess with my settings very much. I'd just make a copy of what's in your home folder, copy it to whatever computer you're using. The only thing where I run into trouble is using multiple copies of firefox, and keeping my info synced, for which Google Browser Sync has been good to me. You'd think there'd be something like this for...well, everything. But I don't know if it exists. I'll just go off and wish for a while.

---

### Post by Leszek Tarkowski on 2007-04-30
I personally use unison. Two packages need to be installed unison and unison-gtk. It can synchronize two computers over ssh (and more - but i use ssh). I'm using it to sync laptop with workstation.

---

### Post by maphew on 2007-05-04
Thanks for the ideas. I've used rsync on occasion, and unison too. Though neither to any degree of proficiency. I've not heard of meld, but I like what I see, [http://meld.sourceforge.net/](http://meld.sourceforge.net/) (assuming that's the same one).  At one point it did occur to me to just use the USB stick as command central but I quickly disregarded it as a silly notion. I'm not so sure about that now though!

---

