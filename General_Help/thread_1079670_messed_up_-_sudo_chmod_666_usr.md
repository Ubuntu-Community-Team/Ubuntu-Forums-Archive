---
title: "messed up - sudo chmod 666 /usr"
date: 2009-02-24
forum: General Help
---

### Post by nsewell on 2009-02-24
how do i undo what i just accidentally did ?
i type 'sudo chmod 666 *'  while in the /usr folder.

i assume part of the resolution is to hopefully go into Recover mode and to the prompt... but not sure what to type to undo my mistake... please help.   thanks.

---

### Post by punx45 on 2009-02-24
there is no magic undo.   you would have to manually change things back to what they originally were, again, with chmod, if you could know the mode for every file.   technically you could do this, but in my opinion the easiest thing to do would be backup and reinstall.   as a side note, this is an excellent example of why to use a separate /home partition.   also good lesson.   be careful when using wildcards, especially with sudo.   on the safe side you can ls * before and see if the files are what you expected.   also, you can use interactive mode with things like rm and it will confirm before taking action.

i suppose it could be possible to go into a live CD and replace just /usr with stock files, but not sure on that.

---

### Post by brian_p on 2009-02-24
> **punx45 said:**
> 

i suppose it could be possible to go into a live CD and replace just /usr with stock files, but not sure on that.

I wonder whether the --reinstall option to apt-get would suit you.

---

### Post by bodhi.zazen on 2009-02-24
Moved to general help (as this is not a security question).

Reinstalling is probably faster then trying to undo that command.

---

### Post by geirha on 2009-02-24
If that's exactly the command you ran, then it's not too hard to fix. If there was a -R (recursive option) in that command, it's a completely different story.

Asuming the command is exactly what you typed, I recommend you boot the ubuntu CD. Once you're in the ubuntu CD's live session, mount your / partition. Just double-click all the harddrives in nautilus' left margin until you find the right one. I'll assume it got mounted to /media/disk. Open a terminal and do
```
cd /media/disk/usr

# If the following two commands output the same directories, then we're good!
ls -ld *
find -perm 666 -ls

# Change the permissions back to default, which should be 755 for all directories in /usr
sudo chmod 755 *

```

---

### Post by nsewell on 2009-02-25
thanks to all for their comments.
I was hoping as mentioned since I did not do this command recursively that I would easily be able to undo my actions.
Taking your advice, I booted up in Recover mode (hitting ESC after rebooting) and then went into the Root prompt.
I then did the following:

cd ..
cd usr
chmod 755 *

Rebooted and everything is back to normal.

I included all of these details in case someone else runs into this and they can see the steps that I took to resolve.

thanks again to all for your quick replies.

---

### Post by brian_p on 2009-02-25
> **nsewell said:**
> 

I then did the following:

cd ..
cd usr
chmod 755 *

Not every directory in /usr should have these permissions.

---

### Post by geirha on 2009-02-25
> **brian_p said:**
> Not every directory in /usr should have these permissions.

Ah, yes. The src directory has a little different permissions. I thought I had changed those permissions myself on my system, but looking at a fresh install, the src directory has 2775 permission. It is not vital for the system to function, but might as well set it back to its default
```
sudo chmod 2775 /usr/src
```

---

### Post by handy on 2009-02-25
Please don't think I'm being harsh, but the following page I link to really does have it laid out well; it even has an interactive chmod parameter changer:

*_[http://www.ss64.com/bash/chmod.html](http://www.ss64.com/bash/chmod.html)_*

---

### Post by punx45 on 2009-02-25
> **nsewell said:**
> thanks to all for their comments.
I was hoping as mentioned since I did not do this command recursively that I would easily be able to undo my actions.

> **geirha said:**
> If that's exactly the command you ran, then it's not too hard to fix. If there was a -R (recursive option) in that command, it's a completely different story.

Asuming the command is exactly what you typed, I recommend you boot the ubuntu CD. Once you're in the ubuntu CD's live session, mount your / partition. Just double-click all the harddrives in nautilus' left margin until you find the right one. I'll assume it got mounted to /media/disk. Open a terminal and do
```
cd /media/disk/usr

# If the following two commands output the same directories, then we're good!
ls -ld *
find -perm 666 -ls

# Change the permissions back to default, which should be 755 for all directories in /usr
sudo chmod 755 *

```

the problem is that the * wildcard does act recursively, even if you have not specified it.   go in to /usr and ls * to see for yourself.   and as stated earlier, while most of the contents of /usr and beyond are 755, but not everything is.

---

### Post by geirha on 2009-02-26
> **punx45 said:**
> the problem is that the * wildcard does act recursively, even if you have not specified it.   go in to /usr and ls * to see for yourself.   and as stated earlier, while most of the contents of /usr and beyond are 755, but not everything is.

No, that's just ls. If you give ls a list of directories, it will list each directory's content. If you add the -d option to ls, it will just list the directory without its content instead. Note that the wildcard is interpreted by the shell before the command is run. Try with "echo *", does it give the expected result?

---

### Post by punx45 on 2009-03-01
ok yep, youre right. my bad :oops:

i tested it with some scratch folders and sub folders   

chmod xxx * 

affected contents of current dir but nothing recursive.

i assumed that dir and dir/dir2 were both acceptable matches for * (which i understand to be 'anything')   

still should be cautious using the * wildcard.

---

