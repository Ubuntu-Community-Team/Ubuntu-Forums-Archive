---
title: "Infinite Loop in Trash!"
date: 2008-04-27
forum: Desktop Environments
---

### Post by Nintendo01 on 2008-04-27
Problem Solved! Thanks' everyone!

While trying to get a link to my home folder on my desktop in Hardy (although I doubt this is confined to just Hardy), I copied my entire Home folder to the Desktop. I then moved it to the trash, but when I tried to empty the trash it deleted all of the stuff in the Home folder except for the Desktop folder. Since the Desktop has a link to the Home folder, and the Home folder has a link to the Desktop, there is an infinite loop in my trash can that can't be permanently deleted! 

Just to be clear, my trash holds a folder called "wayne" that contains a folder called "Desktop" that contains a folder called "wayne" that contains a folder called "Desktop"... and this goes on forever and can't be deleted.

Can anyone help me empty my trash?

It's after midnight right now, so I'll check back in the morning to see if anyone posted anything besides "What were you thinking!!!!" :)

Thanks!

---

### Post by Demorgon on 2008-04-27
Wow I've never heard of this... but yea next time it might be easer just to alt+F2 then the following to add Home folder, trash, ect....

```
gconf-editor
```

Then
```
apps \ nautilus \ desktop
```

---

### Post by HunterThomson on 2008-04-27
WOW that sucks... I have no idea how to fix it I just wanted to say that:)

---

### Post by Nintendo01 on 2008-04-27
Thanks for the input people. Still looking for anyone who can actually fix the problem, if it's possible to fix anyway.

---

### Post by Nintendo01 on 2008-04-27
> **Demorgon said:**
> Wow I've never heard of this... but yea next time it might be easer just to alt+F2 then the following to add Home folder, trash, ect....

```
gconf-editor
```

Then
```
apps \ nautilus \ desktop
```
Thanks for this bit of information! It got my Computer and Home folders on the desktop, just like I wanted. Maybe I should have Googled it before trying what I did before?

---

### Post by Psyker7 on 2008-04-27
Hardy:
```

cd ~/.local/share/Trash/files
unlink <foldername>

```

or Gutsy and before...
```

cd ~/.Trash
unlink <foldername>

```

where foldername is the folder you can't remove from the trash :)

---

### Post by Nintendo01 on 2008-04-27
> **Psyker7 said:**
> Hardy:
```

cd ~/.local/share/Trash/files
unlink <foldername>

```

or Gutsy and before...
```

cd ~/.Trash
unlink <foldername>

```

where foldername is the folder you can't remove from the trash :)
Thanks for the help, but it doesn't work. It gives me this:
```
wayne@wayne-laptop:~$ cd ~/.local/share/Trash/files
wayne@wayne-laptop:~/.local/share/Trash/files$ unlink wayne
**unlink: cannot unlink `wayne': Is a directory**
wayne@wayne-laptop:~/.local/share/Trash/files$ 

```

---

### Post by Diabolis on 2008-04-27
When you delete a file, it goes to the trash can. This is a feature of gnome, not linux. The trash can is a folder that its actually stored in your home folder as a hidden folder. Open your home folder with nautilus and press ctrl + h so you can see hidden files. The trash folder is called .Trash.
That is why you have an infinite loop.

Instead of sending your files to the trash, delete them by hand with the **rm** command.
What you have to do is:
```
cd .Trash
rm -r *
```
The first command takes you to the trash folder.
The second command deletes files.

The **-r** option makes it recursive so it also deletes folders and the ***** means delete everything.
For example if you use **A*** instead of *****, it will delete all the files that their names start with a **A**.

Be very careful with that command as it can destroy your whole system.

[COLOR="Red"]**NEVER**[/COLOR] do this:
```
sudo rm -rf /
```

Please read this:
[malicious commands]("http://ubuntuforums.org/announcement.php?f=73")

---

### Post by Nintendo01 on 2008-04-28
Unfortunately, your suggestion does not work, as there is no .Trash folder on my computer. I looked with ctrl+h to show hidden files in my home folder and there was no .Trash. I also did a search of the filesystem and the only things with trash in their names are some trashapplet files, folders, and icons. The page that opens when I open the trash can using the panel applet is "trash:///" and typing various "cd trash, Trash, .trash, .Trash, etc..." in terminal all bring up folder not found. Maybe the trash is stored someplace else in hardy?

Anyone else have a suggestion?

Edit: I just went back through the posts and realized you posted the Gutsy "cd .Trash" command. I used Psyker7's "cd ~/.local/share/Trash/files" to get to the trash, then used your "rm -r *" command and it worked! Thanks so much, problem solved!!!

---

