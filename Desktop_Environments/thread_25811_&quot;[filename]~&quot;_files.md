---
title: "&quot;[filename]~&quot; files"
date: 2005-04-10
forum: Desktop Environments
---

### Post by Trickyphillips on 2005-04-10
I've been noticing "[filename]~" files while browsing around with the terminal, that I'm unable to see while viewing the same directories with File Browser. I'm guessing gedit creates these as a backup, when I modify a file. They're just taking up space, but I don't want to locate and delete them individually. Is there any way I can remove them all at one?

Thanks. :)

---

### Post by Nis on 2005-04-10
They most likely are from gedit (you can turn this behavior off in the gedit preferences).  You could try the below to find and remove all these files in your home directory:
```

for file in `slocate "~"`; rm -i $file; done

```
I do not guarantee the above code will work so be careful.

---

### Post by skoal on 2005-04-11
Go to a directory where you see them.  The following command will find all ~ files in the current directory and subdirectories.

find . -name "*~" -ok rm  {} \;

will prompt you before you delete them.

find . -name "*~" -exec rm {} \;

will delete them without interation.

---

### Post by Trickyphillips on 2005-04-11
[QUOTE=Nis]They most likely are from gedit (you can turn this behavior off in the gedit preferences).  You could try the below to find and remove all these files in your home directory:
```

for file in `slocate "~"`; rm -i $file; done

```
I do not guarantee the above code will work so be careful.[/QUOTE]

Ah.. Thanks! I was using "[COLOR=DarkRed]locate ~[/COLOR]" to locate, instead of "[COLOR=DarkRed]locate"~"[/COLOR]". It was just returning every file in my home directory.

I was getting an error when I used "for file in `slocate "~"`; rm -i $file; done", so I just used "locate "~" >> file.txt", added "rm" in front of every file I wanted gone, and saved it as a shell script.

Worked like a charm. Thanks, both of you! :-)

---

