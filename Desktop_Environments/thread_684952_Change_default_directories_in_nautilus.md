---
title: "Change default directories in nautilus"
date: 2008-02-01
forum: Desktop Environments
---

### Post by Seymore on 2008-02-01
I recently moved from another distro to Ubuntu. So far I love it. 

I particularly like how everything seems to merge into each other. In my other distro (gentoo), I really never cared for it, but now that I have it, I cant live without it. 

My problem is that I still like to customize (everything). In particular, I have a separate hard drive for music, movies, pictures etc. So I made a soft link to the directory on the other drive that holds my pictures in my $home, and deleted the already present Pictures directory. 

But when I open a file in a gnome-aware program, the old Pictures directory (now in trash) still appears, while my new Pictures directory (naturally) doesn't  appear. So somewhere theres a list of directories to appear in the file-opener, but I cannot for the life of me find out where this list resides. I've tried to search for "Pictures" in gconf, but found nothing. I did find several <schema> entries in nautilus, but I cant change them. 

I am not that familiar with Gnome, using it first time with Ubuntu. I am not a total noob when it comes to linux i general tho. 

**If you think this text is too long, this is the gist of it:**
[LIST=1]
[*]How do I change the default "Pictures" directory?
[*]Alt: How do I change the "default" directories that appear in the "Open" dialog in Gnome programs?
[/LIST]

Any help would be greatly appreciated.

---

### Post by Tenken on 2008-02-01
When you say default Pictures directory are you referring to the one in the places menu/ Nautilus side bar? If you are open a Nautilus window right click the Pictures directory and delete it, then drag the linked Pictures directory that you created into it's place.

---

### Post by Seymore on 2008-02-02
Well, almost. I have already added several directories to the "places" thing. However, what I am talking about is the section above that. There I also find my home directory, my desktop, and several drives (many of which I cannot mount without root access), and also Pictures, if I try to open a file in The Gimp for instance. 

But those I cannot delete or modify in that window. I would really like to delete the drives I havent asked to be there (For instance the root of my Gentoo install). And I would like to change the Pictures directory. 

It seems like Gnome is aware that it's supposed to be pictures in the Pictures directory, as this directory only appears in certain programs. But where is the damn setting?

---

