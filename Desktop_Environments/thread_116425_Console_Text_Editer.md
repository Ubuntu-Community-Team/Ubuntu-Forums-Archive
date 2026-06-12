---
title: "Console Text Editer?"
date: 2006-01-12
forum: Desktop Environments
---

### Post by IAmNotPhillip on 2006-01-12
I have recently partitioned and installed Breezy on my HP Pavilion ze2000 laptop. The instillation went smoothly, but there seems to be a problem with the xorg.config and the GUI can not start properly, so currently I am confined to the command line interface which leads me to my problem:

I have read in another thread that someone with a similar problem was able to fix it by following [this]("http://wiki.ubuntu.com/BinaryDriverHowto/ATI") guide. But when I try to apt-get the necessary files, it simply can not find them. I am positive that the reason why is because I have not opened up the universe or multiverse repositries (sp?) yet. I have searched multiple threads and sites to find out how to do this, but every one of them says to use the gedit command. Seeing that I have no access to a GUI yet in Ubuntu, gedit will not work. I know there used to be a command line text editer, but I can't for the life of me remember what the command is. So that basically is my question. What command should I use to edit the resources.list file via the CLI? Any help will be greatly appreciated.

EDIT: Fixed. Nano does wonders. :)
See my latest post for new problem.

---

### Post by bensode on 2006-01-12
Use pico.  Works nicely and was installed by default in my 5.10 install ...

---

### Post by rfruth on 2006-01-12
Another vote for pico / nano here !  [https://wiki.ubuntu.com/NanoHowto?highlight=%28nano%29]("https://wiki.ubuntu.com/NanoHowto?highlight=%28nano%29")

---

### Post by healychan on 2006-01-12
The well known text editor "vi" is a good choice. If you are not familiar with "vi", read some articles before you start, otherwise, you may not even be able to save and exit.

---

### Post by Gadren on 2006-01-12
Neither vi nor emacs is friendly to new users (but I've heard that once you learn it, it's great!).  I like using nano -- it's fast, simple, and intuitive.

---

### Post by IAmNotPhillip on 2006-01-12
Nano was the one I was looking for, so thank you for reminding me of it. :D

But now I have a new problem, I uncommented all the repositries and added multiverse, but whenever I try to sudo apt-get update, it says it "Couldn't stat source package list" and that I should "run apt-get update to fix the problem"  :X

Any ideas?

---

### Post by kaamos on 2006-01-12
One solution: Back up your sources.list and generate a new one from [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by darth_vector on 2006-01-12
nano is a pico clone, isnt it?

vi is the bomb, kudos to its writters =D>

---

### Post by IAmNotPhillip on 2006-01-12
I tried that source-o-matic thingie, checked and rechecked for typos, and saved.

Still the same problem.
I apt-get update,
errors are thrown in my face,
and the computer helpfully suggests I run an apt-get update to fix the problem.:(

---

### Post by Randomskk on 2006-01-12
Just to be sure, you are using sudo before the apt-get command, yeah?
ie:
sudo apt-get update

Becuase not doing that will throw errors.

---

### Post by und3rtug4 on 2006-01-12
" vi " is my vote!
;)

---

### Post by IAmNotPhillip on 2006-01-12
That would be a yes to the sudo question...but no matter!

I was able to solve the problem by reinstalling while my laptop was plugged into a reliable internet source (ethernet cord directly plugged into my DSL modem). :P

I read somewhere that it might have been a DNS error, and seeing that I didn't know how to change that via the console, I just reinstalled while plugged in and let Ubuntu fix itself automatically. :)

BTW, this post is from my newly installed Ubuntu 5.10 Breezy. :D

Now to just get my built in wireless to work and I'll seriously consider removing windoze alltogether. :)

Thanks for all your help guys (and gals)!

---

