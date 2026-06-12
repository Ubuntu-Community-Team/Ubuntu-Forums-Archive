---
title: "Nautilus date modified"
date: 2010-11-29
forum: Desktop Environments
---

### Post by utubun on 2010-11-29
I've been using Ubuntu 10.04, since 10/04, and really like it - but  still have a number of outstanding puzzles and annoyances. Here is a  main one.

The 'date modified' of a file seems in nautilus to be updated whenever  that file is rewritten, not only when the content is changed. So if I  move a file between discs, its date modified gets updated. I find this  really unhelpful. An extreme example is that in switching over to  Ubuntu, I created an archive disc for all the data files on my old PC -  they now all share the same date modified, making it impossible to  distinguish between older and newer versions of similar files.

Is there any way to change the rules for 'date modified', or to access a 'content modified' field instead?

---

### Post by tom4everitt on 2010-11-30
I guess one could argue that when you move a file between disks, you are really creating a copy on that new disk. Then it makes sense to give it a new time-stamp. But I clearly see your point too!

If you for example have a lot of archive files, which dates you want to remember, the easiest and safest solution would be to include the date in the file name. Obviously :)


But, as you say, you can also modify the date-modified stamp this way:
```

touch -d "2007-04-07" <some-file-name>
touch -t "200704072359" <some-file-name>

```

So I guess with that you could really create your own little 'date-copy' utility by a simple shell script. Tell me if you need help with that.

Credit to: [http://ubuntuforums.org/showthread.php?t=409202](http://ubuntuforums.org/showthread.php?t=409202)

---

### Post by utubun on 2010-11-30
Thanks for this idea - it would certainly work for some purposes, and I may well use it.

I guess I am just trying to replicate useful behaviour that I have previously found as default in other operating systems - in fact that I had never thought about until nautilus didn't do it. I guess what I want is for the system to update the date modified tag only when the file is saved from within an application; that seems more sensible to me than updating it every time the file is moved.

Thanks for your help, though.

---

### Post by Krytarik on 2010-11-30
I recently also had the same problem, I copied the content of an entire partition to another one in order to back it up, before I formated it (due to some unconsistencies/errors). Unfortunately I only saw afterwards, that all files and folders had lost their orginal timestamps (Yiehaah! ;)).

The only way that I know to preserve the original timestamps for such operations is to use the "cp"-command with the respective option via a terminal:

```
cp -a <source> <target>
```

It copies all specified files and directories, including subdirectories, without changing their timestamps (and other attributes, if permitted by the formats of the involved filesystems).

Obviously one will copy files/dirs that way only in important cases.

However in a just now conducted test I could not reproduce that annoying behaviour.

Krytarik

---

### Post by tom4everitt on 2010-12-01
> **Krytarik said:**
> 
However in a just now conducted test I could not reproduce that annoying behaviour.


That is interesting. I do not actually get the behavior the OP is referring to either: no matter if I copy or move, and whether it is on the same partition or between different, my 'Date Modified'-stamp is still unaffected. 

I would have thought it was because I use Nautilus Elementary instead of Nautilus. Which Nautilus do you use? 


@OP 
To install Nautilus Elementary, which I have to say I'm pretty pleased with for many reasons, follow [http://www.webupd8.org/2010/01/nautilus-elementary-simplified-nautilus.html](http://www.webupd8.org/2010/01/nautilus-elementary-simplified-nautilus.html)

It seems that it handles the stamps the way you expect it to.

---

### Post by utubun on 2010-12-01
I was using nautilus, and did not even know that nautilus-elementary existed. I've now installed this and, without exhaustive testing, the date modified seems to behave.

I also like it much more already for several other reasons - so thanks v. much for tip.

---

### Post by tom4everitt on 2010-12-01
> **utubun said:**
> I was using nautilus, and did not even know that nautilus-elementary existed. I've now installed this and, without exhaustive testing, the date modified seems to behave.

I also like it much more already for several other reasons - so thanks v. much for tip.

Great :)

---

### Post by Krytarik on 2010-12-01
I also used the "standard" Nautilus in both cases. The first case was a few months ago, it seems the developers of Nautilus have changed the command executed at a copy/move-operation. Now it seems fine.

I will also try Nautilus Elementary, thanks for the tip.

Krytarik

---

