---
title: "Recovering deleted files - foremost"
date: 2009-01-05
forum: General Help
---

### Post by jaqq on 2009-01-05
Hello.

I tried foremost to recover files from a HD. It worked fine. However, I'm particularly interested on recovering only files that were once deleted. I couldn't find an option with foremost command line that would avoid retrieval/lookup of regular files. Does anyone have an idea or other suggestion? 

Thanks.

---

### Post by Titan8990 on 2009-01-05
There is no "undelete" command. If it is not in your trash, its gone.

---

### Post by jaqq on 2009-01-05
> **Titan8990 said:**
> There is no "undelete" command. If it is not in your trash, its gone.

Yes, I Know. That's why I'm using foremost ([http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)). Foremost, as other software like magicresuce and photorec, is a file recovery tool.

Just to make myself clear (in case...). I erroneously (shift) deleted several folders from my HD. In order to recover the files, I plugged this HD as a secondary device into another system an ran foremost on it.

Basically, I was able to recover all my "lost" files. (Foremost is a great tool!) However, foremost recovered not only my lost files, but the whole HD. So now I have millions of files and don't have a precise and straight-forward mechanism to distinguish/separate which ones are the "deleted" files. 

Thanks for any help.

---

### Post by jaqq on 2009-01-06
Hmm... Apparently, there's not many foremost users around. :( 

Still, let me try again. Can anyone suggest me then another (free) software? 

Or perhaps some way, some command (md5 like), or some script I could use to check the "equality" of several files at once... This way I could compare all my rescued files to the regular ones in the HD.

Thanks.

---

### Post by ubu-for on 2009-04-21
I'm sorry, I do not have an answer to your questions, but could you tell me please with which command you've undeleted your files?

[http://ubuntuforums.org/showthread.php?t=1132299](http://ubuntuforums.org/showthread.php?t=1132299)

Thank you very much!

---

### Post by jaqq on 2009-04-21
> **ubu-for said:**
> ... could you tell me please with which command you've undeleted your files?


Like this:

  foremost -v -t all -i /dev/sda3 -o /path/to/recovered/

Hope it helps!

---

### Post by ubu-for on 2009-04-21
> **jaqq said:**
> Hope it helps!
Thank you very much for your quick answer!!!

But I'm using the ext4 file system and it looks like Foremost and Scalpel can't handle it.

---

### Post by kstella on 2009-07-27
I'm using magicrescue with the gui grescue. I'm trying to recover just this one .zip, and it's spitting out all these other zips that I've never seen before. :/

---

