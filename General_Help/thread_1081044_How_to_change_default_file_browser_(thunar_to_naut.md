---
title: "How to change default file browser (thunar to nautilus, 8.10)"
date: 2009-02-26
forum: General Help
---

### Post by Snow Keld on 2009-02-26
i've been looking for a way but havent found much, i found a help page for changing it in gnome, which is simple enough, but its for gnome :(

page i found: [http://psychocats.net/ubuntu/nonautilusplease](http://psychocats.net/ubuntu/nonautilusplease)

but you see, i like nautilus quite a bit, i have it installed but its not default and when it starts up the desktop is managed by gnome instead...

will that happen no matter what? cuz its a gnome file browser, is the desktop managed by the running file browser???


i dont understand this whole thing, and i couldn't find much already out there.



my question is, can i switch the default file browser (without lots of problems) from thunar to nautilus in xubuntu 8.10, and for anyone else finding this topic, it would be nice to explain it in a way for people to know how to change the file browser from thunar to whatever they want... if its possibly or smart to do.


well, a thanks in advance to anyone who tries, how to change the gnome one isnt difficult to do, but whoever figured it out had to have put tons of work into it with the making of the .sh scripts.

---

### Post by mb_webguy on 2009-02-26
I'm not sure that [this]("http://ubuntuforums.org/showpost.php?p=4490813&postcount=2") is the best solution, but it should work.

---

### Post by Snow Keld on 2009-02-26
i thank you for that link, it is helpful.

before i go about doing that, how to i make the script thats talked about in that post, i think the rest seems simple enough without actually trying it.

only thing is, even if it opens nautilus instead will it switch my desktop manager to gnome like it is now? or will it leave the desktop under xfce?


if that continues to be the problem and there is no real way to fix it then i'll just end up using thunar for simple stuff and nautilus when i wana use dropbox...

[dropbox](http://www.getdropbox.com/) is to keep files online, 2gigs of space for free, i like the idea, but it only wants to work with nautilus.

i like nautilus better anyway with how it recognizes devices like extra hard drives and CD drives without you having to go look for them in the filesystem.



>main point, how do i made the script mentioned [here](http://ubuntuforums.org/showpost.php?p=4490813&postcount=2), and will it keep switching the desktop to gnome when i open my file browser (nautilus). if it will then this is a lost cause anyway as i dont want that.

---

### Post by perpetualcacophany on 2009-02-26
Ok.

Download Nautilus if you haven't already. 

```
sudo apt-get install nautilus
```

Then, do the following.

```
gksu gedit /usr/share/applications/nautilus-folder-handler.desktop
```

Find the line that says: Exec=thunar %U

change it to: Exec=nautilus --no-desktop %U

I think that should work.

---

### Post by mb_webguy on 2009-02-26
> **Snow Keld said:**
> only thing is, even if it opens nautilus instead will it switch my desktop manager to gnome like it is now? or will it leave the desktop under xfce?

Whether you use the method in the link in my post, or the one Snow Keld suggested, the "--no-desktop" option of nautilus will prevent it from taking over your desktop from Xfce.

---

### Post by Snow Keld on 2009-02-27
[THIS POST](http://ubuntuforums.org/showpost.php?p=4490813&postcount=2) worked perfectly.

to anyone else searching for how to change the xubuntu file manager just follow those directions.



i imagine you could slightly alter some of it to use another file manager too, havent tried, not going to, no need, worked for me, i have nautilus working great and it doesnt mess up my desktop (YAY)




problem solved, thank you both for helping me out.

---

### Post by Snow Keld on 2009-02-27
would just like to add on, when you go to 'places' and then a folder you have bookmarked on there like music or documents it doesnt take you there, it always takes you to your account directory.

this isnt a problem, just thought that it should be known.

---

### Post by mb_webguy on 2009-02-27
> **Snow Keld said:**
> would just like to add on, when you go to 'places' and then a folder you have bookmarked on there like music or documents it doesnt take you there, it always takes you to your account directory.

this isnt a problem, just thought that it should be known.

I've seen this problem before.  Try deleting those bookmarks, then adding them again.  That should (hopefully) fix the problem.

---

### Post by Snow Keld on 2009-02-27
> **mb_webguy said:**
> I've seen this problem before.  Try deleting those bookmarks, then adding them again.  That should (hopefully) fix the problem.

ya, i thought of that after i made the post, added them with nautilus instead, but the issue is still there.

small bug regardless, its all good, if someone wants to fix the problem then thats cool, cuz that would mean it works with NO problems.

hmm... i wonder, does nautilus starts when i start the comp/log in...

doesnt matter that much, i havent put dropbox on yet, i should do that now to see how well it works.

---

### Post by dmazzone on 2009-11-24
I had a similar problem after installing pcman on my Ubuntu 9.10 netbook. The way I got nautilus to open as the default was to edit 

~/.local/share/applications/defaults.list

 and to change any occurrence of the file manager in question (i.e. thunar, pcman, etc) to the new file manager default, in my case back to nautilus.

Hope this helps!

---

### Post by mttza1 on 2010-01-02
I tried the above suggestions, and found that nothing seened to change, by default Xfdesktop draws some file manager links (File System, Home, and Trash, as well as removable devices). these cant be deleted from the desktop menu, and i cant find a directory storing them. after creating myfn (as posted above), and replacing the thunar symlink, these desktop shortcuts still open in thunar. when i looked at ~/.local/share/applications/defaults.lst the file was empty. (other than an opening ling enclosed in square brackets []). also to get the nautilus browser you need to use "nautilus --no-desktop --browser", you can also place a path after --browser (eg --browser computer:///). I found running without --browser, in xfce4, resulted in a file manager without an side pane, or the option to have one, and several other features missing.

if i could remove these desktop shortcuts i could replace them, but i cannot find their location.

thanks in advance. mttza1

---

### Post by H3R3T1K on 2012-02-15
I edited nautilus-folder-handler.desktop. How can I check if I'm using Nautilus by default now?

---

