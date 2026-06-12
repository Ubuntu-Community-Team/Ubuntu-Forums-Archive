---
title: "Replace Nautilus"
date: 2008-05-21
forum: Desktop Environments
---

### Post by Kaisersoze on 2008-05-21
Hi all, 

I have been using Linux for the past 5 months and so far I am loving it. I got a bit bored of the K GUI so I switched to Gnome. 

Gnome e is good but... I just hate Nautilus, which IMHO have the look of 90's applications. I just cant stand it.

I know that there are quite a few alternatives like Dolphin, Thunar, etc. However, what I really wanted is to replace Nautilus as the CORE file manager in Gnome. Is this possile?

Thank you

---

### Post by MaX on 2008-05-21
> **Kaisersoze said:**
> Hi all, 

I have been using Linux for the past 5 months and so far I am loving it. I got a bit bored of the K GUI so I switched to Gnome. 

Gnome e is good but... I just hate Nautilus, which IMHO have the look of 90's applications. I just cant stand it.

I know that there are quite a few alternatives like Dolphin, Thunar, etc. However, what I really wanted is to replace Nautilus as the CORE file manager in Gnome. Is this possile?

Thank you

What's there to hate about Nautilus? It's just the same as Thunar or Dolphin, it just doesn't have that many bells as Dolphin does...

It's possible to set Thunar to take over your desktop.
See scripts here:
[http://psychocats.net/ubuntu/nonautilusplease](http://psychocats.net/ubuntu/nonautilusplease)

---

### Post by brallan on 2008-06-11
what we need is a file manager that lets you see the folder sizes and the complete number of files in all subdirectories, not just the files and directories. Its a nightmare when you have to transfer over gigabytes of information to try and discover what still needs to be copied and what doesn't and then confirm that its all been copied over.

---

### Post by vanadium on 2008-06-11
> Its a nightmare when you have to transfer over gigabytes of information to try and discover what still needs to be copied and what doesn't and then confirm that its all been copied over.

Time to learn and use command line tools such as rsync for tasks with this scope. These will figure it out automatically for you.

---

### Post by brallan on 2008-06-13
yeah, i hear you, i should learn these but its scary and easy to make mistakes from the command line. i'll check out rsync.

But am I alone in wanting a better filemanager GUI? since it's likely one of the most used programs, it'd be nice to have more features... it's quite a pain that you send nautilus to copy things and only halfway through when it encounters errors it asks if you want to overwrite or whatever. it would just be nice if nautilus could open a progress bar when copying that had advanced options in checkboxes like: 

overwrite only if the file is newer, 
overwrite only if different size and date, etc. 

that would save a huge wait on unnecesarily overwriting files with the same exact file. and a recovery mode or some type of memory so that if it crashes it remembers what it was doing and asks you again if you want to do it, or at least starts from where it left off when you repeat the process.

---

### Post by vanadium on 2008-06-13
rsync is dedicated to copy/synchronise eventually complex directory trees, and is designed to minimise the information that needs to be copied. You might want to try grsync, which is a graphical interface to rsync. It is available in synaptic.

---

### Post by jimmy the saint on 2008-06-15
First, I would like to point out that there is nothing wrong with wanting a graphical file manager that does what he needs.  It is a basic task, and some people (like me) prefer the graphical method that we grew up with, and are comfortable using.  

Second, there is a method that seems to have worked here
[http://ubuntuforums.org/showthread.php?t=665156&highlight=gnome+dolphin&page=2]("http://ubuntuforums.org/showthread.php?t=665156&highlight=gnome+dolphin&page=2")
Good Luck!!

---

### Post by brallan on 2008-06-16
wow, grsync is an amazingly useful program! I can't believe I've never come across it before. Suddenly, backups of a 100GB huge file archive are taking seconds!!! thanks soooo much for putting me onto this great program. hopefully someday we will have a file manager that, when overwriting, lets us know how many files are different and what the differences are (and perhaps even looks inside documents to show us the difference!) and then offers us the chance to use something like grsync to overwrite.

---

### Post by Fingers &amp; Thumbs on 2008-06-16
I too have just installed Grsync whilst reading this thread, I may not have used it yet but I did launch it to have a look, and one thing jumped out at me straight away. The tooltips associated with the options not only give a description of the option, but also the command line equivalent. Such a simple and brilliant idea, If more apps adopted this approach perhaps new users would not be so put off the use of terminal and even those of us who strive to learn the command line might find the learning curve gathers momentum much more quickly.
  I will certainly be adopting this standard on the programs I am working on.
  (My appologies as this post is a digression from the original purpose of this thread.)

---

### Post by brallan on 2008-06-17
> **Fingers & Thumbs said:**
> I too have just installed Grsync whilst reading this thread, I may not have used it yet but I did launch it to have a look, and one thing jumped out at me straight away. The tooltips associated with the options not only give a description of the option, but also the command line equivalent. Such a simple and brilliant idea, If more apps adopted this approach perhaps new users would not be so put off the use of terminal and even those of us who strive to learn the command line might find the learning curve gathers momentum much more quickly.
  I will certainly be adopting this standard on the programs I am working on.
  (My appologies as this post is a digression from the original purpose of this thread.)

Yeah, that jumped out at me, too, and i thought, wow! that's brilliant! if i want cron to run that rsync command for me, all I have to do is configure grsync the way i want it, then cut and paste the command it spits out to rsync, which does the work! the truth is, i don't really like using the command line if I can avoid it, but I would LOOOOVE knowing what the GUI is doing at the command-line level. I mean, I often wonder if a program like synaptic, when I click on apply is just doing some apt-get command, or whether nautilus is just running some cp command when i ask it to copy files. I-d love to see that!

---

### Post by vanadium on 2008-06-18
If what you want is "mirroring", i.e. make destination directory tree identical to source directory tree, then the command line is really simple. You need the option -a and the option --delete if you want to delete files in the destination that do not anymore exist in the source. For example:

rsync -a --del /home/user/source/ /home/user/backup/

Setting this up for the first time, you might prefer to omit the --del to see if the copy goes into the right destination. The --del option could be very dangerous if you mistakenly swap source and destination.

That said (we are somewhat off-topic) I do like nautilus for daily copying work nevertheless.

In fact, when copying a directory over, nautilus asks first if you want to "merge" or "merge all" (i.e. copy into the destination directories) and then asks whether to replace or not already existing files. Using the "skip all" option, it will only transfer files and directories that do not yet exist in the destination. I tested on a quite large volume of data, and because both  prompt comes early in the copying process, I do not see the issue.

---

### Post by brallan on 2008-06-20
> **vanadium said:**
> In fact, when copying a directory over, nautilus asks first if you want to "merge" or "merge all" (i.e. copy into the destination directories) and then asks whether to replace or not already existing files. Using the "skip all" option, it will only transfer files and directories that do not yet exist in the destination. I tested on a quite large volume of data, and because both  prompt comes early in the copying process, I do not see the issue.

holy cow do I feel dumb!

Though I'm happy to learn that nautilus DOES do what I want, i wonder if other people are also confused by nautilus's form of asking the question? I was thinking that the "skip all" option was aking me to abort the whole procedure, it never occured to me that it would still copy the files that were different!! 

what probably threw me off, is that there are two consecutive dialogues which open with five options each:

<cancel> <skip all> <merge all>   <skip> <merge> 

(and upon choosing <merge all>)

<cancel> <skip all> <replace all> <skip> <replace>

in which the first <skip all> basically means "cancel the op", the second <skip all> basically means "allow the op" - to merge without overwriting. 

 I wonder if this couldn't be rethought. It seems to be based on a model which allows you to decide about each and every directory and file before overwrite, a model which strikes me as something I might have wanted to do in the early 1990's, but rarely anymore, there are just too many files to think about each one.

perhaps the best thing would be a couple of checkboxes below the options which would ask:
( ) ask me about each directory
( ) ask me about each file & subdirectory 

which would reduce it to a single dialogue asking:

<cancel> <skip> <merge> <overwrite>

---

### Post by dabugas on 2008-06-20
Unison is also pretty useful and it allows you to go back and forth between the two replicas. So you can archive to a flash drive, for example, then modify those files on another computer and then bring back the flash drive and reconciles changes with the source.

```
unison /home/user/source/ /home/user/archive/
```

There's also a GUI: unison-gtk

---

