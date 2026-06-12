---
title: "Unique problem: Cannot delete a directory"
date: 2006-08-26
forum: Desktop Environments
---

### Post by anil_robo on 2006-08-26
I can't stop laughing at what's happening here, but it's true.

1. I have installed ubuntu server on a very old computer, and my username on that computer is akumar.
2. I am hosting sites on my home directory on my mac (myipaddress/~akumar/) - notice I have the same username on my mac too.
3. I sit in front of my Ubuntu box, and use wget to download the site being hosted on the mac. It gets downloaded in /var/www/~akumar/
4. I'm not satisfied with the downloaded site, and I want to delete it from the Ubuntu box. So I cd to this dir /var/www/~akumar and pass the "sudo rmdir" command.
5. Now, Ubuntu thinks that I'm trying to delete my home directory on ubuntu box (~akumar) rather than the "~akumar" directory in /var/www. If I cd to /var/www/~akumar, it takes me to /home/akumar instead. And since my home directory is not empty, it can't delete it!!!

Now, how do I delete this /var/www/~akumar dir? I tried enclosing the dir name in quotes (as I do in google searches) but doesn't work. Sorry, I'm new to command-line, hence this stupid question.

---

### Post by aysiu on 2006-08-26
/var/www/~akumar isn't symlinked to /home/akumar, is it?

If not, the ~ (tilda) in the beginning of the folder name may be what's confusing it. Is it possible to rename the directory something else? ```
sudo mv /var/www/~akumar /var/www/akumar
```

---

### Post by croak77 on 2006-08-26
I think you need to use the full path name. I made a simple test on my box. Creating /var/www/~scratch, (my username). I cd'd to /var/www. Then tried rmdir ~scratch and it complained that /home/scratch was not empty. But rmdir /var/www/~scratch worked. If the folder has files in it, you should do rm -r. 

```
sudo rm -r /var/www/~akumar
```

---

### Post by anil_robo on 2006-08-26
No, there is no symlink of any kind whatsoever.

I was able to use the command Aysiu told:
```

sudo mv /var/www/~akumar /var/www/akumar
```

Now I have two directories there:
akumar and ~akumar
And I can't delete either!

So I started off with one undeletable directory, and have managed to have two of them now :rolleyes:

---

### Post by aysiu on 2006-08-26
So when you issue the command ```
sudo rm -rf /var/www/akumar
``` what happens?

---

### Post by anil_robo on 2006-08-26
> **aysiu said:**
> So when you issue the command ```
sudo rm -rf /var/www/akumar
``` what happens?

This did something interesting. When I passed that command, it removed the akumar directory. Passing the same command to /var/www/~akumar directory removed the ~akumar directory too. Now I have a clean folder.

However, the second directory I removed (/var/www/~akumar) deleted my home folder. So, Ubuntu is unable to differentiabe between /var/www/~akumar and /~akumar/ directories, which is quite strange.

Luckily, I didn't have much in my home dir, so it's okay to have lost that. But I'd still like to know how to delete a directory like /var/www/~username

Thanks Aysiu

---

### Post by aysiu on 2006-08-26
I'd say for future reference that you shouldn't put tildas (~) in file or folder names.

Normally ~/ means /home/akumar

---

### Post by peabody on 2006-08-26
when all else fails on the shell, use single quotes '  '

For some real fun, try deleting a file named '-r' :)

---

### Post by bullgr on 2006-08-26
ok, maybe my advice is outdated but when i get some problems is use midnight commander.
just use
> sudo mc
go there you want and press F5 to delete

---

### Post by Tomosaur on 2006-08-26
Couldn't he just have used an escaped tilde, like this:
```

sudo rmdir ./\~akumar/

```
or, of course, rm -rf.

---

### Post by DoktorSeven on 2006-08-26
If you have a tilde (~) in your directory name, use a backslash before it.

rmdir /var/www/\~akumar

Edit: beaten by a minute or so :)

---

### Post by anil_robo on 2006-08-26
> **aysiu said:**
> I'd say for future reference that you shouldn't put tildas (~) in file or folder names.

Normally ~/ means /home/akumar

I didnt put tilda in the folder name. I used wget to download a folder from the web. This folder from the web was being hosted from my mac, under my home directory which had the same username as on Ubuntu. So, the website that wget downloaded was something like [http://my-ip-address.com/~username-on-mac](http://my-ip-address.com/~username-on-mac). This resulted in creation of a local folder on my ubuntu box like this:

/my-ip-address.com/~username-on-mac (note this directory autocreated by wget contains the full web address of the website, which contained a tilda to begin with)And since my username on mac is exactly the same as my username on Ubuntu, ubuntu got confused.


This problem would never have occurred if the website I downloaded didn't have a tilda in its username.

Advanced users only: Please backup your home directory, use wget to download a website folder containing a tilda ~ in its name, and then try to delete that folder... and let me know what do you think :rolleyes:

I'm not using ubuntu since a long time now... but I think this is something the developers need to know - it has happened to me, so it can happen to everyone (loss of home directory due to tilda in a foldername, that is) [-X

---

### Post by aysiu on 2006-08-26
> **anil_robo said:**
> but I think this is something the developers need to know I think you should file a bug report on it.

---

### Post by mgmiller on 2006-08-27
What would happen if you ran ```
sudo nautilus
``` in a terminal and then navigated to the ~directory and deleted it using nautilus.  I would think it would only delete what you have highlighted.  The ~ is probably confusing the command line.

---

### Post by aysiu on 2006-08-27
I would have suggested ```
gksudo nautilus
``` except that the OP said it was on a server on a really old computer.

---

