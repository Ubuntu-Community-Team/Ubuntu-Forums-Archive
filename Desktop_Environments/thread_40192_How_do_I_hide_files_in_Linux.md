---
title: "How do I hide files in Linux?"
date: 2005-06-08
forum: Desktop Environments
---

### Post by duffmckagan on 2005-06-08
I want to hide some of my files in Linux. How do I do that?

Here, it is Ubuntu with Gnome.

---

### Post by kvidell on 2005-06-08
[QUOTE=duffmckagan]I want to hide some of my files in Linux. How do I do that?

Here, it is Ubuntu with Gnome.[/QUOTE]
 You could just chmod the directory they're in to 700 I guess...
chmod 700 directory
- Kev

---

### Post by duffmckagan on 2005-06-08
No, it did not work. 

Also tell me how do i unhide (not just unhide from Nautilus)......removing the Hidden Tag.

---

### Post by mulino on 2005-06-08
Try renaming the files to include a . (dot) at the beginning of the filename.

example:

$ ls
mystuff

$ mv mystuff .mystuff

With the permissions/ownerships you can't hide a file/directory. There is also an option for several progarms to show/hide hidden files when browsing with a graphical program.

Hope it helps,
mulino

---

### Post by 23meg on 2005-06-08
the dot trick is handy; it works with directories as well, and you can choose to view hidden files in nautilus's preferences. it's also easy to access a hidden directory (whose name/path you remember) without doing this by just starting to type its name into the adress bar led by a dot.

---

### Post by duffmckagan on 2005-06-08
[QUOTE=23meg]the dot trick is handy; it works with directories as well, and you can choose to view hidden files in nautilus's preferences. it's also easy to access a hidden directory (whose name/path you remember) without doing this by just starting to type its name into the adress bar led by a dot.[/QUOTE]
 Thanks for the reply guys.

I already told that I know Unhide Option in Nautilus. How can i remove the Hidden Flag from the files/folders?

I hope you will get me this time.

---

### Post by wulf on 2005-06-08
By "hidden tag", do you mean the dot? I'm not at all experienced with Nautilis (command line all the way for file management) but if that is the case, you need to be careful. It will be okay for your own files but if you start renaming files like *.bashrc* to *bashrc*, your system will stop working!

Wulf

---

### Post by Alexander Kirillov on 2005-06-08
[QUOTE=duffmckagan]I want to hide some of my files in Linux. How do I do that?

Here, it is Ubuntu with Gnome.[/QUOTE]
 There is no "hidden" flag/tag in Linux. By default, Nautilus does not show files whose name begins with dot (these are usually configuration files) or ends in ~ (these are usually backup files). Option "show hidden files" refers to these files. But there is no way to make an oridanry file "hidden" short of renaming it so that the name start with dot. 

May I ask why you need this? If you want to make a file invisible to other users, the best way to do it is via file permissions.

---

### Post by duffmckagan on 2005-06-08
[QUOTE=Alexander Kirillov]There is no "hidden" flag/tag in Linux. By default, Nautilus does not show files whose name begins with dot (these are usually configuration files) or ends in ~ (these are usually backup files). Option "show hidden files" refers to these files. But there is no way to make an oridanry file "hidden" short of renaming it so that the name start with dot. 

May I ask why you need this? If you want to make a file invisible to other users, the best way to do it is via file permissions.[/QUOTE]

Hey Alexander, thanks for the information.
Actually, that was what I was frankly looking for.

Now, why do i need to hide files.....

I have multiple Linux Distros installed, and they all have a seperate /home partition.
So, when in another distro, I can always mount the partition of distro which i ain't using. So, permissions don't make sense there. If one can't see files, he won't do that. That is just a step ahead for security. That won't be totally secure though.

---

### Post by wulf on 2005-06-08
[QUOTE=duffmckagan]Hey Alexander, thanks for the information.
Actually, that was what I was frankly looking for.

Now, why do i need to hide files.....

I have multiple Linux Distros installed, and they all have a seperate /home partition.
So, when in another distro, I can always mount the partition of distro which i ain't using. So, permissions don't make sense there. If one can't see files, he won't do that. That is just a step ahead for security. That won't be totally secure though.[/QUOTE]
 How many users on the system? If you're the only one, I can't see much point in hiding the files. Why not just make sure that you mount them read-only? Don't give anyone untrusted access to an account that can mount the other drives.

Wulf

---

### Post by duffmckagan on 2005-06-08
Ok.Thanks.

Currently I am the only one, But I will add some more soon.

Oh yeah.......and it doesn't matter, as i am the root, and only root can mount stuff....!

---

### Post by bisconer on 2006-08-24
hey thats a cool feature.  thanks guys.

---

### Post by rockclimber88 on 2006-09-02
haha, i was really confused when i ripped a cd called "...and the Battle Begun" and the folder I put it in was hidden and amarok wouldn't read it...

I looked all over the menus and preferences attached to the folder and couldnt figure out why it was hidden.

once i added a space to the beginning of the folder's name it displays correctly.

---

### Post by xhizors on 2007-08-01
hiding files is nice for neat freaks. out of sight out of mind.

hiding files because more than one user? Just check the 'Show Hidden Files' and there they are. Not much security there. ;)

---

### Post by kevinlyfellow on 2007-08-01
Another way to hide things in nautilus or konquorer is to list the file or folder in a file called .hidden in the directory the file is in.

For example, I don't use my Desktop folder enough to want it shown in my home folder.

```
echo "Desktop" >> .hidden
```

---

### Post by kshezeppelin1 on 2007-08-26
Iwant on the other hand to know if there is a way to remove the SHOW HIDDEN FILES checkbox from the view dropdown menu I have a coworker who is always nosing into my data when I'm not around and I do not have time to log in and out ect  any help please

---

