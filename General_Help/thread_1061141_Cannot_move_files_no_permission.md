---
title: "Cannot move files: no permission"
date: 2009-02-05
forum: General Help
---

### Post by jtoth on 2009-02-05
I'm trying to migrate our mediawiki installation from a Windows 2003 server to Ubuntu 8.04.  I've gotten the DB restored on the Ubuntu box, but I'm having some problem moving the mediawiki files from the Windows box to the Ubuntu box.

The error I get is that I don't have permission, even though I'm sudoing.

I'm using the ```
sudo mv 'source' 'destination' 
```command, it works with all the other files save some of the important mediawiki directories.  The directories in question (config, extensions, includes, languages, maintenance, skins) are owned by www-data and I can't change permission.  I do not have root access. What am I doing wrong, or do I need root access?

Thanks in advance.

---

### Post by overlord.gaurav on 2009-02-05
You said you're sudoing. Does it mean you tried the command with sudo?
If not, then try this:
```
 sudo mv 'source' 'destination' 
```

---

### Post by jtoth on 2009-02-05
> **overlord.gaurav said:**
> You said you're sudoing. Does it mean you tried the command with sudo?
If not, then try this:
```
 sudo mv 'source' 'destination' 
```

Yes, sorry, I forgot to include that in my code example.  I am using 

```
sudo mv 'source' 'destination'
```

---

### Post by Old *ix Geek on 2009-02-05
From the info you've provided, it's difficult to tell if the permission problem is at the source or target end.  In other words, you may not have permission on the windoze box to delete files [which is what you're doing when moving files off of it], or you may not have permission on the Linux side.  Instead of moving them, have you tried copying the files?  That way you're not using write permission on the 'doze side, and if the *nix side lets you do this then it's not a problem on its side.  Try using the recursive argument with the cp command, i.e., cp -R [source-directory] [destination-directory], and see if that works.

---

### Post by jtoth on 2009-02-05
> **Old *ix Geek said:**
> From the info you've provided, it's difficult to tell if the permission problem is at the source or target end.  In other words, you may not have permission on the windoze box to delete files [which is what you're doing when moving files off of it], or you may not have permission on the Linux side.  Instead of moving them, have you tried copying the files?  That way you're not using write permission on the 'doze side, and if the *nix side lets you do this then it's not a problem on its side.  Try using the recursive argument with the cp command, i.e., cp -R [source-directory] [destination-directory], and see if that works.

I should have specified, (stupid me) that I have the files on the the Ubuntu box, on my desktop.  Let me include the actual syntax:

```
sudo mv '/home/flagso/toth/desktop/migrate wiki/mediawiki/config' '/usr/share/mediawiki'
```

the error I get is:

```
mv:: cannot overwrite non-directory '/user/share/mediaiwki/config' with director '/home/flagso/toth/desktop/migrate wiki/mediawiki/config'
```

I'm sorry, I should have been this specific from the beginning, its one of those days D:

---

### Post by Old *ix Geek on 2009-02-05
It's okay--we ALL have those days! :)

Okay, it looks like you're attempting to overwrite an existing file named "config" that's already in your /usr/share/mediaiwki directory.  For right now, rename that file to something else, e.g., config.orig, and then try the command again. Report back with the results!

---

### Post by jtoth on 2009-02-05
DISREGARD :3  I figured out how I can force the rename by using sudo mv. So now I am able to rename and move the new files in! Thanks!

---

### Post by jtoth on 2009-02-05
Problem is solved, but I'm having problems with mediawiki recognizing the old localsettings.php, but I am pretty sure that has to do with the way I set it up in the first place.

Thanks all! :3

---

