---
title: "Cleaning Utilities"
date: 2006-06-25
forum: Desktop Environments
---

### Post by RESmonkey on 2006-06-25
So how do I clean my cache, internet files, defragment, etc. like I did on the old   
Virusdows XP?

Any thing I need to get?  Please help a newbtolinux like me...lol

:confused:

---

### Post by alaaji on 2006-06-25
[QUOTE=RESmonkey]So how do I clean my cache, internet files, defragment, etc. like I did on the old   
Virusdows XP?

Any thing I need to get?  Please help a newbtolinux like me...lol

:confused:[/QUOTE]

Well, if you are using Firefox, I can help you with your internet files/cache.  Go to Edit > Preferences > Privacy.  At the bottom of the Privacy tab should be a settings button for the Clear Private Data tool.  Customize it to your liking and voila!

Here is a forum post about [fragmenting]("http://www.ubuntuforums.org/showthread.php?t=192967&highlight=defragment").

Here is another link that you might find useful about [improving performance in Ubuntu]("http://ubuntuforums.org/showthread.php?t=189192").

---

### Post by newman on 2006-06-25
I don't know about cleaning utilities, but in Firefox you can press <Ctrl-Shift-Del> to bring up the "Clear Private Data" menu...

---

### Post by FredB on 2006-06-25
[QUOTE=newman]I don't know about cleaning utilities, but in Firefox you can press <Ctrl-Shift-Del> to bring up the "Clear Private Data" menu...[/QUOTE]

Or set it up to clean after you close it.

And defragging ? Why ? ;)

---

### Post by raptros-v76 on 2006-06-25
unlike ntfs,  (which i still need to make up a dirty joke for), a dirty filesystem (meaning it gets framgented) that windows uses, **ext3**, which ubuntu uses, does not get fragmented

---

### Post by jongkind on 2006-06-25
[QUOTE=raptros-v76]unlike ntfs,  (which i still need to make up a dirty joke for), a dirty filesystem (meaning it gets framgented) that windows uses, **ext3**, which ubuntu uses, does not get fragmented[/QUOTE]

I'm not sure about this. After 1 month of use fsck indicates that the files of my home partition were 8% non contiguous. After 3 months that was 16 %. 

This could be reduced to 3 % after copying the files of my home partition to another potition and copying them back again. 

I'm not sure about the effect of the non-contiguous files on the performance of the system. However, as I look now at it now, the statement that "ext3 does not get fragmented" is not valid.

---

### Post by raptros-v76 on 2006-06-25
ok. but it doesnt slow it down as much. and it happens much less.

---

### Post by jongkind on 2006-06-26
I see your point and this is given by a lot of people as advantage for Linux and the ext3 file system. 

However, extrapolation of 16 % in 3 months to 1 year makes 64%. This does not seem worse or better to me than what Windows XP does, whereas this latter OS has a defragmentation utility. This is bothering me for some time now. I guess I'll make a new thread of this, since I'm concerned that it disappears in the 'noise' of the current thread.

---

### Post by RESmonkey on 2006-07-02
I read the defragmenting topic, will it really break my disk?

So there is nothing I have to do to clean the ext3 Ubuntu?

---

