---
title: "archive manager double-click to extract here ?"
date: 2009-05-05
forum: General Help
---

### Post by macakinho on 2009-05-05
Hi!

First post here! :KS

I was looking for a way to extract files from archives using Archive Manager just by double clicking on them and have them extracted where the file is instead of having to right-click and select "extract here".

Is there any way to configure Archive Manager to make it work like this?

Cheers!

---

### Post by bruno9779 on 2009-05-05
To achieve this i would write a script in bash that does what you are looking for, then set it in "properties > open with" so that the script is used as default app when double-clicking.

I am not writing the script for you, as i think that is a kinda dangerous thing to do, and you should consider well if you are willing to take the risk. (eg. exploding .tar files, and the fact that also the enter key would have the same effect)

If you are still interested post back and i'll help with the script (really just a couple of lines)

---

### Post by macakinho on 2009-05-05
I am willing to take that risk, as I come from OSX and the archiver there just does that by default.

As I am a noob, I would appreciate all the help I could get!

---

### Post by bruno9779 on 2009-05-05
I am going to write the script tonight, as at work i am forced to use a win-dose box.

hold on till tomorrow and it'll be done

---

### Post by macakinho on 2009-05-05
thanks a lot Bruno!

will check back tomorrow!

---

### Post by bruno9779 on 2009-05-05
I have written the script using references from the net, but as i said I am on Win-dose box and cannot test it now.

so:

1: create a text file called oneclickExtractor.sh (or anything else you like)

2: paste the code
```

#!/bin/bash

#extract script to automate decompressing

extract () {
   if [ -f $1 ] ; then
      case $1 in
         *.tar.bz2)   tar xjf $1      ;;
         *.tar.gz)   tar xzf $1      ;;
         *.bz2)      bunzip2 $1      ;;
         *.rar)      rar x $1      ;;
         *.gz)      gunzip $1      ;;
         *.tar)      tar xf $1      ;;
         *.tbz2)      tar xjf $1      ;;
         *.tgz)      tar xzf $1      ;;
         *.zip)      unzip $1      ;;
         *.Z)      uncompress $1   ;;
         *)         echo "'$1' cannot be extracted via extract()" ;;
      esac
   else
      echo "'$1' is not a valid file"
   fi
} 
```

and save

3: move it to /usr/bin (you don't have to but i like to consider this scripts as user programs)
you may have to 

```
sudo mv oneclickExtractor.sh /usr/bin
```

4: right click on a compressed file, go to open with and add /usr/bin/oneclickExtractor.sh, then choose it.

5: close and you are good to go. (you will have to do this for any file extension you want it to work with)

[SIZE="5"]I REPEAT: IT HAS NOT BEEN TESTED. IT ISN'T A DANGEROUS COMMAN, BUT TRY IT ON A DUMMY FILE FIRST[/SIZE]

also i would appreciate if you feedback on the outcome

PS: you may have to install packages for the proprietary file extensions (.rar .ace etc.)

---

### Post by geirha on 2009-05-05
Try setting the default "Open with" to "/usr/bin/file-roller -f" or "/usr/bin/file-roller -h" (without the quotes).

Read the man-page to see what those options mean
```
man file-roller
```

---

### Post by macakinho on 2009-05-05
Bruno:

Am trying your script but I get a weird error.

When I choose the script file at the "open with", "custom command", after I browse and look for it, when I press "open" it says Could not find '/usr/bin/oneclickextractor.sh'

Do you know what might be going on?

---

### Post by macakinho on 2009-05-05
> **geirha said:**
> Try setting the default "Open with" to "/usr/bin/file-roller -f" or "/usr/bin/file-roller -h" (without the quotes).

Read the man-page to see what those options mean
```
man file-roller
```



This command worked! Thanks!

The only thing now is, how to make it the default, as everytime I double-click the icon, it still opens Archive Manager.

---

### Post by bruno9779 on 2009-05-05
> **macakinho said:**
> Bruno:

Am trying your script but I get a weird error.

When I choose the script file at the "open with", "custom command", after I browse and look for it, when I press "open" it says Could not find '/usr/bin/oneclickextractor.sh'

Do you know what might be going on?

if you opern /usr/bin, is oneclickextractor.sh there?

---

### Post by bruno9779 on 2009-05-05
> **geirha said:**
> Try setting the default "Open with" to "/usr/bin/file-roller -f" or "/usr/bin/file-roller -h" (without the quotes).

Read the man-page to see what those options mean
```
man file-roller
```

I thought about doing it with file-roller, but i found some posts that said it doesn't accept cli input, so i went for tar and the script. I will read the man pages and possibly come to the end of this as soon as i can get to my jaunty box

---

### Post by macakinho on 2009-05-05
> **bruno9779 said:**
> if you opern /usr/bin, is oneclickextractor.sh there?

Yes! I though I had the path wrong but I clicked the browse button and selected the file. So the file is there!

Tried geirha command and it worked! Thanks any way! :)

Can you just help me out getting the selected script to open by default when I double click?

---

### Post by bruno9779 on 2009-05-05
if the command worked, you just have to tick it in right click > **properties** > open with.

---

### Post by macakinho on 2009-05-05
P E R F E C T ! ! ! :P:):P

Thank you so much!

---

### Post by samarthmath on 2012-09-22
Macakinho, can you elaborate on the geirha command? as i wanna do the same.

---

### Post by samarthmath on 2012-09-22
Okay, sorry, I figured it out above!!

THANKSS :D

---

### Post by overdrank on 2012-09-22
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

